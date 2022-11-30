---
description: A refresher on DNS
---

# Actualisation du DNS

DNS is one of the oldest components of Internet architecture. It was invented nearly 40 years ago in 1983 and hasn’t changed much since to address threats to freedom and safety on the Internet.

![DNS hierarchy. Source cloudflare.com](https://images.ctfassets.net/v3ez3dek3dk6/1di653gtbQwZieFp4cTivQ/f8f5791690235e68b846b2501b7da52b/dnsRootServerDiagram.png?fit=pad\&w=720)

## Domain name anatomy

The following uses "mail.google.com" as an example

### Top-level domain

Top-level domains (TLDs) like “.com” are run by [registries](dns-refresher.md#registry) like Verisign who make billions of dollars annually by renting and renewing [second-level domains ](dns-refresher.md#second-level-domain)(SLDs) like google.com. Which entity controls what SLD is recorded on the[ nameservers](dns-refresher.md#name-server) run by the registries.

### Second-level domain

Verisign (aided by registrars like Namecheap, GoDaddy etc, who act as brokers) allows anyone who pays a standard fee to rent a SLD below .com, like the “google” part of our mail.google.com example. “Rent” is used here because there is no way to have true ownership over an SLD; instead you get what is effectively a renewable tenancy over it, governed by the terms of a standardized contract with the TLD manager. You are not free to do whatever you like with “your” domain; like a rented apartment, there are restrictions, and you can be evicted or have the terms of your lease modified at times.

### Subdomain

Finally, the "mail" part of our mail.google.com example domain is what’s known as a subdomain. Subdomains are managed by the entity currently controlling the SLD (in this case, Google) and are often used for organizational purposes like separating out different functions of a website. Subdomains are occasionally also granted to third parties; for example tumblr gives out subdomains to users (e.g. myusername.tumblr.com) on a first-come first-serve basis, but the problems inherent to SLDs are even worse for subdomains—your use of the subdomain is 100% at the mercy of the SLD manager, and most ToS’s allow them to be revoked for any reason at all and with no warning—recall when Tumblr users had their blogs disappear due to the site's over-active censorship filter.

## Root zone

At the top of the DNS hierarchy is a file called the [root zone](dns-refresher.md#root-zone) where TLD ownership info is recorded. The root zone is managed by the ICANN, which determines who gets what TLD— "who" in this case means governments, non-profits, and for-profit corporations like Verisign which owns ".com". In other words, the **entire traditional DNS system** is controlled at the top by a single entity, ICANN.

## Root server

What's a root server?

## Nameserver

What are nameservers?

## Resolver

What's a resolver?

## Registrar

What's a registrar?

## Registry

What's a registry?
