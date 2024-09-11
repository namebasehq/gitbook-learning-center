---
description: A walkthrough for resolving Handshake domains
---

# Access Handshake names

Handshake names live on the Handshake blockchain, which most browsers do not yet natively support. While we're waiting for browsers to catch-up, below are numerous ways you can already access Handshake names in your browser.

![](<../.gitbook/assets/HNS Resolvers.png>)

## Level 0

Level 0 methods require trusting a central party to resolve Handshake for you, are not private because they can see which domains you're visiting, are insecure because they can MITM attack you, and requires appending something to every Handshake domain.

### HNS↗TO

[HNS.to](https://hns.to/) is a proxy gateway created by [nijynot/](http://nijynot/) that you can use to access Handshake domains without installing anything or changing your DNS settings.

Try visiting welcome.nb/ by appending hns.to at the end of the domain: [welcome.nb.hns.to](http://welcome.nb.hns.to).

{% embed url="https://hns.to" %}

#### Alternatives to HNS.to

If HNS.to is down, you can use an alternative like [costanzo/](http://costanzo/)'s [rsvr.xyz](https://rsvr.xyz).


## Level 1

Level 1 methods require trusting a central party to resolve Handshake for you, are not private because they can see which domains you're visiting, are less insecure than Level 0 methods because they aren't proxy gateways, and no longer require appending something to every Handshake domain.

### HNSDoH

[HNSDoH](https://welcome.hnsdoh.com) is a public DNS resolver created by [Nathan.Woodburn/](https://nathan.woodburn.au/) that uses DNS over HTTPS to resolve Handshake.  
It has very little downtime compared to other public resolvers.

{% embed url="https://welcome.hnsdoh.com" %}

### HDNS

[HDNS.io](https://hdns.io) is a public DNS resolver created by [namebase/](http://namebase/) that enables any device to access Handshake domains on any browser.

Point your DNS to 103.196.38.38 and 103.196.38.39 to resolve Handshake.

{% embed url="https://www.hdns.io/" %}

### Bob Extension

[Bob Extension](https://chrome.google.com/webstore/detail/bob-extension/ogcmjchbmdichlfelhmceldndgmgpcem) is a Chrome extension created by [kyokan/](http://kyokan/) that currently uses HDNS.io for resolving Handshake names directly in your Chrome browser's search bar — try using it to search "[http://welcome.nb/](http://welcome.nb/)".&#x20;

{% embed url="https://chrome.google.com/webstore/detail/bob-extension/ogcmjchbmdichlfelhmceldndgmgpcem" %}

### easyhandshake

[easyhandshake](https://easyhandshake.com) is a server created by [pinheadmz/](https://pinheadmz/) that you can use to resolve Handshake using DoH.

{% embed url="https://matthewzipkin.medium.com/resolving-hns-names-using-dns-over-https-94643fe62ecd" %}

## Level 2

Level 2 methods no longer require trusting a central party because you're accessing the Handshake blockchain directly, are private because you're recursively resolving domains locally, and are more secure than Level 1 methods because they support DANE.

### Fingertip

[Fingertip](https://impervious.com/fingertip.html) is an all-in-one open source resolver created by [Impervious](https://impervious.com) that sets up your browser for DANE and resolves Handshake trustlessly. Comes with HNSD light client installed.

{% embed url="https://impervious.com/fingertip.html" %}

## Level 3

Level 3 methods are for developers who want to access Handshake directly without relying on 3rd party software.

### HNSD (SPV node)

You can run [your own SPV node with HNSD](https://github.com/handshake-org/hnsd) to trustlessly resolve Handshake names without running a full-node.

Handshake is the only naming blockchain with a lightweight recursive DNS resolver, which you can easily embed into browsers, apps, and devices. A recursive DNS resolver is a piece of software that can recursively resolve domain names to IP addresses. The light client can trustlessly resolve Handshake names using only 10mb of memory and virtually zero CPU. It’s the most secure way to use Handshake because it doesn’t require trusting any third party resolvers that can inspect your DNS traffic.&#x20;

{% embed url="https://github.com/handshake-org/hnsd" %}

### HSD (full node)

Run [HSD](https://github.com/handshake-org/hsd) locally to access Handshake in the most decentralized, private, and secure way.

{% embed url="https://github.com/handshake-org/hsd" %}

#### HSD on Raspberry Pi

{% embed url="https://gist.github.com/pinheadmz/a3e5ded7a4f0413e948a6a257c375891" %}

Install HSD on Raspberry Pi so any device connected to your home wi-fi can resolve Handshake names.

#### HSD on Linux

{% embed url="https://skynode.medium.com/running-a-handshake-full-node-on-the-windows-subsystem-for-linux-97989c4523ae" %}
