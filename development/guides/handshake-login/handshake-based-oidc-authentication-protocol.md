---
description: >-
  Use this resource to get a high level overview of the proposed system design
  for login with Handshake.
---

# Handshake-based OIDC Authentication Protocol

## Background and Motivation

Handshake secures DNS by using a blockchain as the root-of-trust. With a trusted DNS, you can use domain names to attach many different types of information to a name. In this document, we'll describe how you can pin public keys to your Handshake names and subsequently use those keys to login to websites.

For maximum interoperability, we've designed this standard to be compatible with the OIDC authentication protocol.

{% hint style="info" %}
Check out this [overview](https://auth0.com/docs/protocols/openid-connect-protocol) and this [illustrated guide](https://developer.okta.com/blog/2019/10/21/illustrated-guide-to-oauth-and-oidc) for a primer on OIDC. Note that you don't need to deeply understand OIDC to use Handshake login — if you've ever added Google Sign-On to your website then you've already used OIDC.
{% endhint %}

## OIDC and Handshake

Let's walk through a quick example of typical OIDC usage. Suppose you're logging in to a third party website and you want to use your Google account. Google is the "Authorization Server", and Google is responsible for ensuring you type in the correct password.

Now let's walk through how OIDC can work with Handshake.

There are two key differences between typical OIDC usage and OIDC usage with Handshake:

1. Rather than asking the user to provide a password for a specified username, the Authorization Server asks them to sign a challenge using the public key pinned to the specified Handshake name.
2. There is no centralized authority that performs this signature verification. Google is the only authority that can validate Google usernames and passwords. With Handshake, any Authorization Server can perform the verification.

![Sequence diagram outlining the OIDC Authentication flow with Handshake](<../../../.gitbook/assets/Sequence diagram.png>)

{% hint style="info" %}
We provide an open-source OIDC Authentication Server here: [https://github.com/namebasehq/handshake-oidc](https://github.com/namebasehq/handshake-oidc)
{% endhint %}

## Details

### Pin public keys to your Handshake names

In this implementation, a Handshake name is used as a login identifier. The end-user generates a pair of keys where the fingerprint of the public key is stored on a TXT record to prove ownership of the identity.

### The \_auth Records

A TXT records is added under the subdomain "{deviceId}.\_auth" of the targeted Handshake name.

```
v={x};fingerprint={hash}
```

#### The deviceId subdomain

Used to support multiple-device. This is a random value generated on the device carrying the identities.

#### The authv field

Used as identifier in the TXT records, {x} can be used for versioning.

#### The fingerprint field

Contains the hash of the public key pinned to the specified Handshake name.

### Security considerations

The v0 of this protocol is using a pair of keys generated with the algorithm RSA-PSS with a length of 4096 bits. Its associated digest function is SHA-512.

The fingerprint is generated using the digest function SHA-256 against the public key.

In the future, \_auth records can be extended to specify the hash function used for the specified identity.

```
v=n;fingerprint={hash};digest={digest};alg={alg}
```

The COSE algorithm identifier is defined as a future improvement to dynamically identify the encryption used for the name. A list of valid values can be found here: [https://www.iana.org/assignments/cose/cose.xhtml#algorithms](https://www.iana.org/assignments/cose/cose.xhtml#algorithms)

For example to specify a key pair using ECDSA w/ SHA-256 and a SHA-2 256-bit Hash:

```
v=n;fingerprint={hash};alg=-7;digest=-16
```

## Usage of Handshake with an Authorization Server

Instead of asking the user to provide a password for a specified username, the Authorization Server asks the user to sign a challenge using the private key pinned to the specified Handshake name.

The user also provides the public key to allow the Authorization Server to verify this challenge.

The OIDC provider can then compare the fingerprint on the DNS records with the fingerprint of the supplied public key.

This comparison is then determined to be valid by proving that the challenge has been signed by the owner of the key. At this point, the Authorization Server can return a successful Authentication Response.

### Security considerations

To prevent replay attacks, the Authorization Server must present the user with a unique challenge for every login attempt. This challenge is the random "state" field provided to the Authorization Server by the application at the start of the OIDC flow. Because the challenge is unique to each login attempt, the client's login payload cannot be replayed. The challenge is signed with RSA-PSS with a salt length of 64 bits.

Once the user receives this challenge, they must sign it with their private key to prove their identity. Then, the Authorization Server can query a trusted Handshake DNS resolver (such as a local full node) to securely verify that the key used to sign the challenge matches the key pinned to the specified Handshake name.
