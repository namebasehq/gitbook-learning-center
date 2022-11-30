---
description: Tutorial on how to login with your Handshake name as an end-user
---

# Using Handshake Login

## Set up the TXT record manually

Open the identity manager:[ https://id.namebase.io](https://id.namebase.io)

Create a new identity by entering a name you own. Click on "Copy my record".&#x20;

This will copy the key fingerprint in your clipboard.

Set a new TXT record on subdomain domain {prefix}**\_auth** with a short TTL:

```
v=0;fingerprint=<hash>
```

The prefix is generated with a hash function SHA-256 of the concatenated targeted name and the randomly generated deviceId:

```
const prefix = hash(name + deviceId, 'SHA-256');
```

TLD or subdomain records will look like this:

| Domain   | Type | Host                      | Value                   | TTL |
| -------- | ---- | ------------------------- | ----------------------- | --- |
| TLD      | TXT  | {prefix}.\_auth           | v=0;fingerprint=\<hash> | 60  |
| Sudomain | TXT  | {prefix}.\_auth.subdomain | v=0;fingerprint=\<hash> | 60  |

## Set up a custom identity manager

You have the possibility to configure your own application to carry your identity. In order to configure your name to point to your custom identity manager, you will need to add a TXT record on the subdomain \_idmanager of your name.

#### \_idmanager.\<handshake>

```
v=0;url=<https://your application>
```

