---
description: Handshake can serve as a much safer alternative to Certificate Authorities
---

# More secure internet

In traditional DNS, the root of trust for HTTPS is supported by Certificate Authorities. There are thousands of Certificate Authorities that you need to trust in order to browse the web securely, and even more intermediaries that they delegate trust to. If even a single one of those third parties act maliciously or get hacked, then all of your internet browsing is compromised.

Handshake shifts the root of trust from centralized Certificate Authorities to a cryptographically-backed distributed root of trust based on the blockchain. Instead of a single bad Certificate Authority compromising your security, the entire Handshake blockchain would need to be compromised in order to compromise your security.

## The Problem: HTTP <a href="#the-problem-http" id="the-problem-http"></a>

When you make an HTTP request to google.com, your browser first does a DNS lookup to find the IP address of Google's servers. Your browser then makes a request to that IP address. The request goes from your computer to Google's servers, but your request is routed through a variety of large interconnected networks before it reaches its destination. In some cases, it may even pass through another country before returning to your country. For instance, most of the internet traffic in South America [routes through Miami](https://en.wikipedia.org/wiki/NAP\_of\_the\_Americas). At any point along this journey, intermediaries may inspect or even attempt to modify the data you send to Google to another server that's not Google! This is known as a MITM (Man In The Middle) attack. In fact, Edward Snowden’s documents [revealed](https://www.cnet.com/news/nsa-disguised-itself-as-google-to-spy-say-reports/) that the NSA did exactly that when they performed MITM attacks on Google to collect data on people.

![MITM attack. Source cloudflare.com](<../../.gitbook/assets/MITM (1).png>)

## The Solution: HTTPS <a href="#the-solution-https" id="the-solution-https"></a>

We need Authentication, Integrity, and Encryption in order to prevent MITM attacks.The solution is to use HTTPS, which relies on TLS and CAs.&#x20;

Your browser encrypts traffic to websites using TLS (Transport Security Layer), which relies on public key cryptography. Public key cryptography is a method of asymmetric encryption using a pair of keys: a public key and a private key pair (as opposed to symmetric encryption with only one key). The public key is shared publicly and is used to verify signatures. The private key is used to decrypt messages encrypted by the public key. The private key is never shared.

When the browser makes an HTTPS request to Google, it initiates a [TLS Handshake](https://www.cloudflare.com/learning/ssl/what-happens-in-a-tls-handshake/) with Google and receives Google's public key. The browser then uses Google’s public key to verify that the rest of the messages in the TLS handshake are initiated by Google, because only Google has the private key for its public key. This way, even if intermediate networks spy on the request, they won't be able to decrypt the contents of it. If an intermediary routes the request to another server pretending to be Google, the browser will know because that server won't be able to respond to the request.

## Certificate Authorities <a href="#certificate-authorities" id="certificate-authorities"></a>

How do you know that Google's public key is actually Google's public key? When you make that first request to Google, an intermediate network may have intercepted your request and returned a fake public key for Google. CAs attempt to solve this problem. CAs are trusted third parties that verify the authenticity of public keys for websites. Your operating system ships with a list of vetted CAs by default. When a website wants to support HTTPS requests, they register their public key with one of the trusted CAs. You verify that the public key you receive from Google is truly Google's public key by checking it with your CAs.

![Google’s key is trusted by GlobalSign, which my computer trusts as a root CA. Check yourself by visiting Google.com and clicking the lock icon in the URL bar. ](https://images.ctfassets.net/v3ez3dek3dk6/2a4iKL9SiujjvWnav3ATa3/75943c435b1ca77416baf75b6a651eb8/image.png?fit=pad\&w=720)

## Problems with CAs <a href="#problems-with-cas" id="problems-with-cas"></a>

You may have noticed a fundamental assumption: You must trust the CAs. All of them. There are hundreds of CAs installed on your computer by default — Microsoft Windows comes with [390 certificates](https://gallery.technet.microsoft.com/Trusted-Root-Program-381e7a89), and Mac OS X comes with [170 certificates](https://support.apple.com/en-us/HT209144). These CAs can delegate trust to intermediates, and those intermediates can delegate trust to even more child intermediates. You don’t know who all these CA intermediates are and if even a single one of them gets hacked, all your HTTPS traffic is vulnerable to MITM attacks. In the [DigiNotar attack](https://en.wikipedia.org/wiki/DigiNotar), the Iranian government hacked a Dutch CA and used it to MITM 300,000 Iranian citizens.

![Just a few of the certificates that my machine trusts. Not surprised to see GoDaddy but I did not expect to see a Hong Kong CA installed...](https://images.ctfassets.net/v3ez3dek3dk6/4aSc1sI708gGsIMefV39zO/06878ba9bad31d6c47b2334ce3ee91f1/OS\_X\_Certificates.png?fit=pad\&w=720)

## Fixing the CA problem  <a href="#fixing-the-ca-problem" id="fixing-the-ca-problem"></a>

While blockchain-based protocols can be slow and limited, they excel at addressing the issue of trusted third parties. Data stored on blockchains are immutable and all parties can verify that the data stored on a blockchain is correct. Take Bitcoin as an example. Wallets on Bitcoin have public keys that are used to sign transactions. Wallets also have data associated with them, including how many bitcoin are in the wallet. You can even associate arbitrary data with your wallet, such as the [birth date of a baby](https://www.blockchain.com/btc/tx/9439b6de84d4d5d7dd9b990c713d820b451a412cdef325f64cfa95fe43864556) stored on the Bitcoin blockchain.

![Eric Meltzer memorializes his daughter's birth date on the Bitcoin blockchain.](https://images.ctfassets.net/v3ez3dek3dk6/4mIFLSXTgJSSJPtPshY9g0/886b09d80899fe9c4848b6ce4452b10f/Screen\_Shot\_2019-09-12\_at\_7.04.19\_PM.png?fit=pad\&w=720)

You can imagine a system where instead of storing arbitrary data on the blockchain, you store names on the blockchain and their public keys. Instead of relying on an arbitrary list of CAs as your root of trust, you rely on a cryptographically-backed distributed root of trust. Name owners could associate their own keys to their name, and everyone would be able to verify that the public key for a name is the correct one. This would solve the issue of trusting CAs, and Handshake is precisely such a system!

## Handshake <a href="#handshake" id="handshake"></a>

Handshake is a blockchain protocol that aims to solve the issue of trusting hundreds of CAs. It's a protocol that's similar to Bitcoin, except instead of using coins as money, you use Handshake coins to register names on the Handshake blockchain. These names are top-level domains (TLDs) like .com, .org, .net. Handshake decentralizes the root zone file, which is the ICANN-controlled file that determines who owns what TLD. Anyone can register their own TLD on the Handshake blockchain.

![DNS hierarchy. Source cloudflare.com](https://images.ctfassets.net/v3ez3dek3dk6/1di653gtbQwZieFp4cTivQ/f8f5791690235e68b846b2501b7da52b/dnsRootServerDiagram.png?fit=pad\&w=720)

One benefit of TLDs on Handshake is that they have public keys associated with them that can be verified to be authentic. Only the name owners can associate DNS data and other arbitrary data with their name that everyone can verify on the blockchain instead of trusting CAs.

There's another significant benefit of Handshake names — they are resistant to censorship, seizure, and tampering because Handshake names are stored on the blockchain. Like Bitcoin wallets, only the name owners can update their names or transfer their names as long as they keep their private keys safe.

A consequence of this is that names are their own root of trust. They can simply pin the TLS keys they use instead of relying on external trust in CAs. This allows Handshake names to avoid attacks against CAs that exist in the current system.
