---
description: >-
  With Handshake, you're able to run your own SPV node using HNSD to trustlessly
  resolve Handshake names without having to run a full-node.
---

# Setting up the light client

Handshake is the only naming blockchain with a lightweight recursive DNS resolver, which you can easily embed into browsers, apps, and devices.

A recursive DNS resolver is a piece of software that can recursively resolve domain names to IP addresses. The light client can trustlessly resolve Handshake names using only 10mb of memory and near zero CPU. It’s the most secure way to use Handshake because it doesn’t require trusting any third party resolvers that can inspect your DNS traffic.

Step 1 will involve getting the light client running on your computer.

{% hint style="info" %}
If you're interested in learning more about the differences between running a Simplified Payment Verification (SPV) node to access a blockchain, and a full node, click through to [the StackOverflow post here](https://bitcoin.stackexchange.com/questions/4649/what-is-an-spv-client). The inclusion of an SPV node is one of the main reasons Handshake was built off of a fork of Bitcoin.
{% endhint %}

## Using Docker

To run the light client on Docker with Mac OS X, run the following command:

```
docker run -d --name hnsd --restart always -p 53:53/udp namebasehq/hnsd "/opt/hnsd/dist/hnsd" -p 4 -r 0.0.0.0:53
```

Once the light client is up and running in the background, you'll need to point your computer's DNS IP to your local machine. Click to the next page to find out how to set the DNS settings for your operating system.

{% content-ref url="setting-your-operating-system-dns.md" %}
[setting-your-operating-system-dns.md](setting-your-operating-system-dns.md)
{% endcontent-ref %}

## Install from Source Code

If you'd like to compile the resolver yourself, you can do so by grabbing the source code from the handshake-org/hnsd repo linked below.

{% embed url="https://github.com/handshake-org/hnsd" %}

## Coming Soon: Install from pre-built binaries

### OSX

### Windows

### Linux

{% hint style="info" %}
* Redhat/Fedora: There is no rpm package for yum. If you would like to contribute, please contact us.
* Debian/Ubuntu: There is no dpkg for apt. If you would like to contribute, please contact us.
* Alpine: There is no package in apk for Alpine. If you would like to contribue, please contact us.
{% endhint %}
