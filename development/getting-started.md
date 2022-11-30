---
description: >-
  This guide is for developers looking to build apps using Handshake. You will
  learn how to build four different types of applications from start to finish.
---

# Getting started

{% hint style="info" %}
Are you looking for Handshake protocol docs? Check out [hsd-dev.org](https://hsd-dev.org/)
{% endhint %}

{% hint style="info" %}
Not a developer or new to Handshake? Check out the [Namebase Learning Center](https://learn.namebase.io) for tips on how to get started with Handshake, and use your Handshake domains without code.
{% endhint %}

## Overview of Handshake

> Handshake is a decentralized, permissionless naming protocol where every peer is validating and in charge of managing the root DNS naming zone with the goal of creating an alternative to existing Certificate Authorities and naming systems.\
> Source: Handshake Whitepaper

In essence, Handshake takes a core piece of internet infrastructure, DNS's root zone file, and puts it on a blockchain. At a high level, Handshake is _just_ decentralized DNS, but solving the [CA problem](https://www.namebase.io/blog/meet-handshake-decentralizing-dns-to-improve-the-security-of-the-internet/) and making it possible to self-custody, use, and transfer names permissionlessly in a publicly-verifiable way opens up exciting applications for developers that weren't feasible before Handshake. We document four of those applications in this guide:

| Application                      | Description                                                                                                                                                | Scenario                                                                                                                                                                                                                                                                     |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Traditional website              | Use a Handshake name to resolve traditional websites hosted on servers or hosting providers like GitHub Pages, Heroku, and Vercel                          | <ul><li>Personal blog</li><li>Existing websites</li><li>Decentralized domain backup</li></ul>                                                                                                                                                                                |
| Decentralized website            | Pair Handshake with decentralized storage solutions like [Skynet](https://siasky.net/) and [IPFS](https://ipfs.io/) to create fully decentralized websites | <ul><li>Personal blog</li><li>Dapp frontends</li><li>Static websites</li></ul>                                                                                                                                                                                               |
| Decentralized login              | Allow users to securely login to your website using their Handshake names without needing to store emails or passwords                                     | <ul><li>Decentralized identity</li><li>Pseudonymous accounts and reputation</li><li>Secure E2E encryption without <a href="https://support.signal.org/hc/en-us/articles/360007060632-What-is-a-safety-number-and-why-do-I-see-that-it-changed-">safety numbers</a></li></ul> |
| Decentralized social application | Develop decentralized social applications that minimize centralization while avoiding the the usability issues of federated applications                   | <ul><li>Decentralized Reddit</li><li>Decentralized Twitter</li><li>Decentralized Tumblr</li></ul>                                                                                                                                                                            |

Each application section is standalone and doesn't require that you are familiar with the previous application sections. Dive into whatever interests you most!
