---
description: >-
  This guide provides a quick tutorial on how you can get an existing blog
  online using Web 3.0 technology in 3 minutes or less.
---

# Building a decentralized blog on Handshake

Web 3.0 has opened an entirely new technological field for developers. A question we often get from developers looking to begin building for the decentralized web is, “Where do I start?”. There are many ways to answer this question. We’ll be exploring one: decentralizing your existing static site.

This guide will highlight two core pieces of the decentralized stack: naming, and storage. In this guide, we’ll be working with the Handshake, and Skynet blockchain protocols to handle these two parts respectively.

## Build your blog

The first part of creating a decentralized application involves creating the content you hope for others to access in the first place. Most of the time, this process maps quite closely with traditional development approaches.

If you're just starting off, we recommend choosing a static site generator, and building a single page application that you can then upload to Skynet. We suggest [this Netlify guide](https://www.netlify.com/blog/2020/05/04/building-a-markdown-blog-with-next-9.4-and-netlify/) if you're looking for steps on creating a simple static blog.

If you're just looking to go through the motions of this guide and confirm content is accessible, [download the 'public' folder from this Github repo](https://github.com/jakeschaeffer/exampleBlog).

## Upload to Skynet

Skynet is able to host static websites natively. As long as the directory you’re uploading has an `index.html` file, you should be able to upload your site directly to Skynet, and access it via any Skynet portal.

To upload our content, we can use Sia’s user-friendly [siasky.net webportal](https://siasky.net) (alternatively, we can use the command-line interface). Once on [siasky.net](https://siasky.net):

1. Scroll down the page to the upload box, and select “Do you want to upload the entire directory?”
2. Click “Browse”
3. Select the folder that contains the contents of your already built app from your computer (this may be a 'dist', ‘public’, or 'out' folder - any will work as long as the folder contains an `index.html` file)

The link that's output is now a link to your application, stored on Skynet, which can be accessed through Sia's gateway.

If you used the UI, grab the Skylink to your content. The Skylink is the 46 character string at the end of the link that was returned. The `siasky.net/` in front of the string is one of many portals you can use to access the content living at the Skylink Note this down because you’ll need it later to connect your content to Handshake.

It's important to note that the Skylink is what lets other computers find your content. However, you can use any portal to access that content. For example, the Skynet docs are stored on Skynet, but can be accessed using any of the below links.

1. [https://skyportal.xyz/PAL0w4SdA5rFCDGEutgpeQ50Om-YkBabtXVOJAkmedslKw](https://skyportal.xyz/PAL0w4SdA5rFCDGEutgpeQ50Om-YkBabtXVOJAkmedslKw)
2. [https://siasky.net/PAL0w4SdA5rFCDGEutgpeQ50Om-YkBabtXVOJAkmedslKw](https://siasky.net/PAL0w4SdA5rFCDGEutgpeQ50Om-YkBabtXVOJAkmedslKw)
3. [https://skydrain.net/PAL0w4SdA5rFCDGEutgpeQ50Om-YkBabtXVOJAkmedslKw](https://skydrain.net/PAL0w4SdA5rFCDGEutgpeQ50Om-YkBabtXVOJAkmedslKw)

Your app is now living on the decentralized Internet! However, given the complexities of the links, they're not yet quite human-readable.

Continue on to understand how your application can be fully decentralized beyond just this storage layer.

## Configure the domain

When using Skynet, each time you redeploy your application, you’ll be returned a new Skylink. A constantly updating link may present challenges as you attempt to share your content online. Additionally, while the application itself is stored on a decentralized storage network, when users go to access your app, the IP address it lives at is still resolved using the traditional Domain Name System.

This can present issues for those looking for a site that's truly censorship-resistant. The first way users interact with any application is via its domain. Handshake allows you to obtain your own Top Level Domain that no one can block access to.

Before continuing, you’ll need a Handshake domain. [Namebase](https://namebase.io) makes it easy to purchase your own Handshake domain.

### Update domain records

To access the content you have on Skynet via a simple, human-readable URL, other computers must be able to perform two distinct actions:

1. Find out where the content is (performed via a DNS Lookup)
2. Access the content once it’s told where the content lives (in our case, the content lives on Skynet which traditional computers can’t access without prior configuration)

To accomplish this, we will:

1. Set a TXT record with the Skylink for your app&#x20;
2. Set an ALIAS or CNAME record (depending on whether you're accessing the app via a bare TLD, or a secondary domain respectively) pointing to a Skynet gateway

When working with Handshake domains, domain records operate similarly to traditional DNS domains. However, rather than using the A record to point a domain to an IP address, we’ll use the nameserver .TXT record to point the domain to our Skylink.

#### Setting the TXT record

1. Navigate to the Namebase domain manager for the domain you’re putting your project on at: `https://namebase.io/domain-manager/YOUR_DOMAIN`&#x20;
2. Scroll down to the “Namebase nameserver DNS records” section, and click, “Add new record”
3. Select “TXT” from the dropdown, and input

| Parameter  | Value                                                                                                                                                   |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Name       | <p><code>_contenthash</code> </p><p>(or <code>_contenthash.YOUR_SUBDOMAIN</code> if putting content on a secondary domain under your Handshake TLD)</p> |
| Value/Data | `sia://` + your Skylink (the 64 character string that comes after the ‘/’ in the returned link from Part 1)                                             |
| TTL        | 5 mins                                                                                                                                                  |

You're done with Part 1! The good news is: any computer that makes a request to your Handshake domain will be directed to the provided Skylink! Continue on to Part 2 to learn how to deal with the next step.

### Set up the Sia gateway

Because most computers aren’t currently setup to natively access files on Skynet, they don't know how to find your app using just a Skylink. To fix this, we’ll need to set either an `ALIAS` or `CNAME` record pointing to the gateway that computers can use to access your application.&#x20;

Namebase currently hosts a public gateway for anyone to use at `sia.namebase.io.`. However, keep in mind this is experimental and won’t be thoroughly maintained. If you want to create a more reliable, secure site, hosting your own gateway is highly recommended.

If you want to create a site that is truly decentralized, hosting your own gateway is the next step to complete decentralization.

#### **Using Namebase’s public Skynet gateway**

If you're **setting content on the bare TLD**, create an ALIAS type record under the "Namebase nameserver DNS records" section and set:

1. Name: @
2. Value/Data: `sia.namebase.io.` (note the trailing period)
3. TTL: 60 mins

If you're **setting content on a subdomain**, start by double-checking that the TXT record name you set above is of the format, `_contenthash.YOUR_SUBDOMAIN`. Then create a CNAME type record with the following values:

1. Name: `YOUR_SUBDOMAIN`
2. Value/Data: `sia.namebase.io.` (again, note the trailing period)
3. TTL: 60 mins

## Conclusion

Now as long as your device can resolve Handshake names, you can go to a web browser and view your blog at http://YOUR\_DOMAIN or http://SUBDOMAIN.YOUR\_DOMAIN!

### Further Reading

#### [How to build a decentralized site on Handshake](https://ras.cr/handshake-tutorial.html) - ras.cr/

## &#x20;
