---
description: >-
  Use this resource if you're looking to create your own implementation of
  Handshake login (or explore how we implemented Handshake login in services
  like Namer News).
---

# Handshake Login Implementation Guide

#### OIDC Implementations Using Handshake

Rather than asking a user to provide a password for a specified username as is typical in a standard OIDC implementation, when authenticating using Handshake the authorization server asks the user to sign a challenge using the private key corresponding to the public key that is pinned to their specified Handshake name.&#x20;

In the Handshake case, there is no centralized authority that performs this signature verification. In a traditional implementation, if Github provided the authorization server, they would be the only authority able to validate Github usernames and passwords.&#x20;

However, anybody can:

1. run a Handshake full node
2. query a Handshake name for its pinned public key
3. validate that a challenge was signed by the correct public key

If a blog wants to add support for logging in with Handshake, then that blog can run their own OIDC authorization server that implements the protocol specified in this document. There's no need to trust any centralized parties for authentication. The blog only needs to trust Handshake.

With this being said, for convenience, that blog could use a third-party Handshake authorization server, provided they trust the organization running it. Namebase runs an authorization server for Namer News, and developers that are interested in using it in their applications can use it once it is open to the public.&#x20;

Alternatively, developers can host their own authorization server.

Now let's go through how the specific Namer News login implementation works in detail. We hope this can act as a guide for others to implement their own authorization flows.

{% hint style="info" %}
Here is an open source OIDC Authentication Server: [https://github.com/namebasehq/handshake-oidc](https://github.com/namebasehq/handshake-oidc)
{% endhint %}

## Overview

When implementing OIDC with Handshake, the OIDC provider makes a Handshake DNS query to fetch a TXT record which contains a fingerprint of the user's public key. The user's ability to sign a challenge with their private key is what proves their identity to Handshake, the OIDC provider, and the application requesting identity.

{% hint style="info" %}
To minimize trust, we recommend each application host their own OIDC provider to handle queries to the Handshake network as opposed to relying on a third-party provider.
{% endhint %}

### "Login with Handshake" Identity Manager

The "Login with Handshake" [Identity Manager](https://github.com/namebasehq/handshake-id-manager) - in this example implementation - manages the identities of the user's keys linked to their respective Handshake domains. This is so that the associated keys are securely accessible when implementing the Login with Handshake flow.

In this example implementation, we are showing one example of how keys can be handled. The specifics of how you manage the keys, via the Identity Manager or otherwise, is up to the discretion of each developer. This could be via a hardware wallet, using WebAuthn, or any custom key management solution.&#x20;

In this case, the extension stores a public and private key pair for each domain a user has associated with their domain records. Everything is stored locally, and the keys stored are unique from their ownership public and private keys. This means that even if the data stored in a user's extension was compromised, user's domains themselves would still be entirely safe.

## Walkthrough

### 1. OIDC client discovers the authority public keys

Before users ever interact with your platform, the OIDC client will discover the authority public keys from the OIDC provider.&#x20;

To configure the OIDC client:

```typescript
const clientConfig: any = {
	authority: oidc.authority,
	client_id: oidc.clientId,
	client_secret: oidc.clientSecret,
	redirect_uris: oidc.callbackUrls,
	token_endpoint_auth_method: 'client_secret_post',
	response_types: ['code'],
};
const issuer = await Issuer.discover(clientConfig.authority);
const client = new issuer.Client(clientConfig);
```

### 2. Replay attack defense

When a user tries to access secured content, the OIDC client generates replay attack defense and redirects the user to the OIDC provider.

Let's cache the code\_verifier to verify the response at the end of the login flow and let's generate the authorization URL:

```typescript
export async function getLoginUrl(req: Request): Promise<string> {
	const code_verifier = generators.codeVerifier();
	const state = generators.nonce();
	const { redirect } = req.query;

	req.session.auth = {
		code_verifier,
		state,
		redirect: redirect?.toString() || '',
	};

	const code_challenge = generators.codeChallenge(code_verifier);
	const url = client.authorizationUrl({
		scope: 'openid email profile offline_access',
		code_challenge,
		code_challenge_method: 'S256',
		state: state,
		response_mode: 'form_post',
		prompt: 'consent',
		audience: oidc.audience,
	});

	return url;
}
```

### 3. The OIDC provider fetch the TXT record on the subdmain \_idmanager and redirect to the identity manager passing the relevant encoded data as a hash query

Locate the associated identity manager:

```typescript
const txts = await dns.resolveTxt('_idmanager.' + id, { all: true });
// v={x};url={idManagerUrl}
```

Let's redirect to the id manager:

```typescript
const idManagerUrl = new URL({idManagerUrl});
idManagerUrl.hash = `#/login?state=${btoa(data.state)}&id=${btoa(data.id)}&callbackUrl=${btoa(data.callbackUrl)}`
```

**state** is used to prevent replay attack

**id** identifies who is trying to log in

**callbackUrl** specifies the oidc endpoint where the data need to be posted back&#x20;

### 4. User creates their new identity

{% hint style="info" %}
If users are simply selecting a domain that they have already used to set up a profile, skip to Step 5.
{% endhint %}

The user is then prompted to create a new identity by providing the name of an owned handshake domain or subdomain.&#x20;

The identity manager generates a new pair of asymmetric keys. The fingerprint of the public key is stored on a dedicated TXT records and should returns the following format:

```
$ dig -t txt {prefix}._auth.{name} @103.196.38.38
v={x};fingerprint={hash};
```

The prefix is generated by concatenating a randomly generated device identifier and the name, then hashing with SHA-256 and keeping only the first 16 characters:

```typescript
// digest SHA-256
const pefix = hash(deviceId + name).substr(0, 16);
```

### 5. Identity selection, and the OIDC provider page

The user selects an identity from the list displayed via the identity manager which injects into the OIDC provider page:

* the random string {no replay} is signed with the identity private key.
* the original random string. {no replay}
* the public key of the selected identity.
* the handshake domain used as identity.
* the device prefix generated for the name: **hash(deviceId+name)**

```typescript
  let publickey = atob(req.body.publicKey);
  let id = atob(req.body.domain);
  let signed = atob(req.body.signed);
  let prefix = atob(req.body.prefix)
```

### 6. TXT record fetch, and hash finding

At this stage, the OIDC provider fetches the TXT Records of the \_auth. subdomain from the supplied handshake domain name and tries to find the hash.

```typescript
import dns from 'hdns';

const dnsResovlers = [ x.x.x.x, ... ]
dns.setServers(dnsResovlers);

const txts = await dns.resolveTxt(prefix + '._auth.' + id, { all: true });
```

It then extracts the value from the TXT records.

```typescript
  async getFingerprintAsync(id) {
    let regex = /([^;]+)=([^;]*)/g;
    try {
      let txts = await dns.resolveTxt('_auth.' + id, { all: true });
      let parsedRecords = txts
        .map((txt) => {
          let params = {},
            match;
          while ((match = regex.exec(txt))) {
            params[match[1]] = match[2];
          }
          return params;
        })
        .sort((a, b) => {
          if (!b.v) {
            return -1;
          }
          return a.v > b.v ? -1 : 1;
        });

      if (parsedRecords) {
        return parsedRecords[0].fingerprint;
      }

      return undefined;
    } catch (e) {
      console.warn('invalid hns check', e);
      return undefined;
    }
  },
```

{% hint style="info" %}
dnsResolvers provides a list of IPs of servers resolving handshake names
{% endhint %}

### 7. Fingerprint comparison, and replay attack verification

At this stage, the OIDC provider compares the fingerprint on the DNS records with the fingerprint of the supplied public key. The signed string is compared, and verified with the public key. The {no-replay} value is verified.

In our implementation, the fingerprint on the TXT record is fetched using HDNS:

```typescript
  let fingerprint = await hnsUtils.getFingerprintAsync(id);
```

Then we verify that the fingerprint matches:

```typescript
  let isFingerprintValid = await hnsUtils.verifyFingerPrint(fingerprint, publickey);
```

And we verify that the challenge has been signed by the correct key:

```typescript
async verifySignature(publicKey, signature, data) {
    const binaryDerString = atob(signature);
    const binaryDer = this._str2ab(binaryDerString);
    return await subtle.verify(
      {
        name: 'RSA-PSS',
        saltLength: 64,
      },
      publicKey,
      binaryDer,
      this._encodeMessage(data)
    );
  },
```

```typescript
let crypto = await hnsUtils.importCryptoKey(publickey);
let isSignatureValid = await hnsUtils.verifySignature(crypto, signed, params.state);
```

### 8. Provider generates claims, user is authenticated

Finally, the OIDC provider generates the required claims and signs a JWT token. This is returned to the client where the user is now authenticated.&#x20;

```typescript
if (isFingerprintValid && isSignatureValid) {
  // success
  const result = {
    select_account: {}, 
    login: {
      account: account.accountId,
    },
  };
} else {
  result = {
    error: 'access_denied',
    error_description: 'Invalid credentials',
  };
  console.warn('Fingerprint or decryption invalid.');
}
```

```typescript
await oidc.interactionFinished(req, res, result, { mergeWithLastSubmission: true });
```

##
