---
description: >-
  If you’re looking to create an app that lets others put content on their own
  Handshake domains (see: dword.johnxu/), you can use the Namebase Record
  Assistant for a smoother user experience
---

# Namebase Record Assistant

## Overview

If your app's users have registered their Handshake name through Namebase, the domain record assistant allows them to easily set DNS records on their domain with a single click.&#x20;

To do this, you'll send users to the Namebase domain management settings page of the specific domain whose DNS records need updating.&#x20;

You'll pass the records to be set via URL parameters. The record assistant decodes these parameters, and asks the user to confirm the records to be set. Namebase updates the user's records, and they're directed back to your application.

{% hint style="info" %}
The Namebase Record Assistant only works with names custodied in Namebase. If your user is self-custodying their name you should provide separate instructions for how they can set DNS records manually.&#x20;
{% endhint %}

## Step 1: Send users to Namebase with URL Parameters

Ask your user which Handshake domain they'd like to use to access the content you're helping them create. Once you have the intended domain your users are looking to update, you can send them to the following URL:

`https://namebase.io/next/domain-manager/{DOMAIN}/records?records={RECORDS}&redirect={REDIRECT_URL}`

| Parameters     | Description                                                                                                                            |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `RECORDS`      | <p>Base64-encoded JSON of the resource record array you'd like to set.</p><p>See below for more details.</p>                           |
| `DOMAIN`       | Handshake domain the user is attempting to modify records for. Handshake domain must be custodied inI Namebase, and owned by the user. |
| `REDIRECT_URL` | URL you'd like the user to be sent to upon completion of the record setting process.                                                   |

Records can be set via:

```
const records_json = [{ 
                        type: "<type>", 
                        host: "<@ or subdomain>", 
                        value: "<value>", 
                        ttl: 3600 
                      },
                      { 
                        type: "<type>", 
                        host: "<subdomain>", 
                        value: "<value>", 
                        ttl: 60 
                      }];
                      
const RECORDS = btoa(JSON.stringify(records_json));
```

Generate the url with the encoded parameters:

```
const url = new URL(`${BASE_DOMAIN()}/next/domain-manager/${tld}/records`);
const redirectUrl = getRedirectUrl();
const encodedRedirectUrl = encodeURIComponent(encodeURIComponent(redirectUrl.toString()));

url.searchParams.append('records', btoa(JSON.stringify(records)));
url.searchParams.append('redirect', encodedRedirectUrl);

window.location.href = url.toString();
```

| Parameters | Description                                                                                                                                                                                                                                         |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `type`     | Type of record you are setting. This will differ for each type of content you're working with (Skylinks require setting TXTs for example). You then must have either an ALIAS (if you're using a TLD) or CNAME (if you're working with a subdomain) |
| `host`     | Either "@" for the root, or the intended subdomain itself of the TLD you're working with.                                                                                                                                                           |
| `value`    | The URL you would like the domain to point to.                                                                                                                                                                                                      |
| `ttl`      | Integer value indicating how long you want the DNS record to be cached by resolvers for (in seconds, minimum 60 seconds).                                                                                                                           |

### Example: Skylink on bare TLD

So, if you're looking to point your Handshake TLD `wouidn/` to a file uploaded to Skynet, you will format `RECORDS`:

```
const records_json = [{ type: "TXT", host: '_contenthash', value: "sia://3AHPjX8HlJ9HTAT48zmCppDsk8HttQB5sxbk64w3_kogBA", ttl: 60 },
                      { type: "ALIAS", host: '@', value: "sia.namebase.io.", ttl: 3600 }]
                      
const RECORDS = btoa(JSON.stringify(records_json));
```

And send your user to the domain:

`https://namebase.io/next/domain-manager/wouidn/records?records=W3sidHlwZSI6IlRYVCIsImhvc3QiOiJfY29udGVudGhhc2giLCJ2YWx1ZSI6InNpYTovLzNBSFBqWDhIbEo5SFRBVDQ4em1DcHBEc2s4SHR0UUI1c3hiazY0dzNfa29nQkEiLCJ0dGwiOjYwfSx7InR5cGUiOiJBTElBUyIsImhvc3QiOiJAIiwidmFsdWUiOiJzaWEubmFtZWJhc2UuaW8uIiwidHRsIjozNjAwfV0=&redirect=https://example.com`

### Example: Skylink on subdomain

The records set for users looking to put content on a subdomain, `myblog.wouidn/` would be:

```
const records_json = [{ type: "TXT", host: '_contenthash.myblog', value: "sia://3AHPjX8HlJ9HTAT48zmCppDsk8HttQB5sxbk64w3_kogBA", ttl: 60 },
                      { type: "CNAME", host: 'myblog', value: "sia.namebase.io.", ttl: 3600 }]
                      
const RECORDS = btoa(JSON.stringify(records_json));
```

And the user would be directed to the domain:

`https://namebase.io/next/domain-manager/wouidn/records?records=W3sidHlwZSI6IlRYVCIsImhvc3QiOiJfY29udGVudGhhc2gubXlibG9nIiwidmFsdWUiOiJzaWE6Ly8zQUhQalg4SGxKOUhUQVQ0OHptQ3BwRHNrOEh0dFFCNXN4Yms2NHczX2tvZ0JBIiwidHRsIjo2MH0seyJ0eXBlIjoiQ05BTUUiLCJob3N0IjoibXlibG9nIiwidmFsdWUiOiJzaWEubmFtZWJhc2UuaW8uIiwidHRsIjozNjAwfV0=&redirect=https://example.com`

This same process is how we implemented the content upload flow for dLinks, and the authentication flow for Namer News. To read more about how to use the record assistant for authentication specifically, check out our the [Using Handshake Login](../handshake-login/using-handshake-login.md) post.

## Step 2: User confirms record setting, and is sent back to your app

At this point, the user is asked to confirm the records you're asking to have set. Should they click confirm, a JSON request is sent to Namebase's servers, and their domain is updated. They are then redirected to the specified `REDIRECT_URL`.

![What your users will see](<../.gitbook/assets/image (2).png>)

{% hint style="info" %}
If the user attempts to set records for a name they do not own, they will be presented with an error screen letting them know that they do not own the domain they're attempting to set records for.
{% endhint %}

## Conclusion

If your users are looking to update content, simply repeat the process. We hope this article was helpful, and helps you create engaging applications for your users.

To see an example application that utilizes this flow and the record assistant, check out [dWord](http://dword.johnxu.hns.to/), an app built by John Xu for the Namebase hackathon.

If you have any questions about this process, please don't hesitate to get in touch by reaching out to: [jake@namebase.io](mailto:jake@namebase.io?subject=Request%20for%20help%20with%20domain%20record%20assistant)
