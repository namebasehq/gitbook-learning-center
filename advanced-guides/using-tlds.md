---
description: A guide for using Handshake TLDs
---

# Utiliser les TLDs

## How do you use Handshake names as a name owner? <a href="#how-do-you-use-handshake-names-as-a-name-owner" id="how-do-you-use-handshake-names-as-a-name-owner"></a>

Your name is a TLD, so you can point it to a nameserver and issue your own domains. Domain registrars like GoDaddy and Namecheap operate their own nameservers for domains, but to use Handshake you’d need to run your own nameserver (or use Namebase!). If you own .joke, you can point it to your nameserver and create good.joke and great.joke. You can even sell bad.joke.&#x20;

Amazingly, you can point your TLD to an IP address directly and use your TLD as a domain! In the recording below we pointed .namebase to the same server as namebase.io and visited it by typing in namebase/.

{% embed url="https://videos.ctfassets.net/v3ez3dek3dk6/53uEzDIzJZvnwq1CUS5fpO/69e581806763993e65fa801ca414c922/handshakeDemoShort.MP4" %}

Your name can also have arbitrary data associated with it using TXT records, which opens the door to numerous use cases. For instance, you can associate a Bitcoin wallet address with your name, in addition to using your name as a domain. You could visit your friend's website at satoshi/ and then send bitcoin to satoshi/ with your crypto wallet.

## How do you use Handshake names as an end-user? <a href="#how-do-you-use-handshake-names-as-an-end-user" id="how-do-you-use-handshake-names-as-an-end-user"></a>

Handshake is backward compatible with existing DNS protocols. All you need to do to use it is point your computer's DNS resolver or your router's DNS resolver to a Handshake resolver. It's similar to using existing resolvers like Cloudflare's 1.1.1.1 and Google's 8.8.8.8. That’s how we got an iPhone to resolve namebase/ in the recording above.&#x20;

[Follow these instructions](../starting-from-zero/how-to-access-handshake-sites.md) to learn how to access Handshake sites with NextDNS, one of Firefox's Trusted Resolvers. You can run your own resolver as well — Handshake is the only naming blockchain launching with a [lightweight recursive DNS resolver](https://github.com/handshake-org/hnsd). A recursive DNS resolver is a piece of software that can recursively resolve domain names to IP addresses. If you’ve never heard of recursive resolvers, think of DNS as a tree stemming from the root down to the individual domain ([pic](../about-handshake/about-handshake/more-secure-internet.md#handshake)). Recursive resolvers traverse the entire tree (recursively!) to find the information that a domain points to. The light client can trustlessly resolve Handshake names using only 10mb of memory and virtually zero CPU. It’s the most secure way to use Handshake because it doesn’t require trusting any third party resolvers that can inspect your DNS traffic.

The light client is critical to Handshake's adoption because it drastically increases the surface area of where people can safely use Handshake. You can easily embed the light client into browsers, apps, and embedded devices. Without it, consumers would need to run full-nodes to trustlessly resolve names, and empirically no consumer wants to do that (even if you’re a crypto enthusiast, how many people do you know who run Bitcoin full-nodes?).
