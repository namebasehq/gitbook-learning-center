---
description: Use a Handshake name as the domain for your traditional website
---

# Traditional website

With Handshake, you can use both your root name (i.e. [nb/](https://nb.hns.to)) and a subdomain (i.e. [welcome.nb/](http://welcome.nb.hns.to)) as the domain for your traditional websites.

Conceptually all you have to do is set resource records like A records and CNAME records just like you would with a traditional domain. However, root resource records are [limited](https://hsd-dev.org/guides/resource-records.html), so you need to set an NS record on your root name pointing to a nameserver in order to set A and CNAME records.

If you register your name on Namebase, we configure this automatically for you and provide a free nameserver you can use as well.

![](<../../.gitbook/assets/Handshake DNS tutorial.png>)

You can also follow this guide to use your own nameserver: [Setting up a Handshake TLD with a hosted DNS service](https://dev.to/rithvikvibhu/setting-up-a-handshake-tld-with-a-hosted-dns-service-2g6c)

Once you've set up your Handshake website, follow this guide to learn how to resolve them on any of your devices.

{% content-ref url="../resolving-handshake/" %}
[resolving-handshake](../resolving-handshake/)
{% endcontent-ref %}

## Hosting providers

Many hosting providers such as Vercel, Heroku, and GitHub Pages work with Handshake names. Community members have documented how to use many of them in our general [Learning Center](../../starting-from-zero/how-to-create-a-handshake-website.md).

If a hosting provider doesn't support Handshake, it's most likely because they have a verification step for custom domains that checks if the custom domain is a valid ICANN domain. In that case, we recommend writing to the hosting provider to relax their verification so that Handshake domains work as well. This is what was done in the case of Vercel.

## HTTPS

One of Handshake's primary goals is to replace CAs with a more secure blockchain-based root of trust. [This article](https://www.namebase.io/blog/meet-handshake-decentralizing-dns-to-improve-the-security-of-the-internet/) provides an overview of the concept, and community members have documented how to set up HTTPS websites using Handshake in our [Learning Center](../../starting-from-zero/how-to-create-a-handshake-website.md).

Note that end-user configuration is necessary to visit Handshake HTTPs sites until browsers support it natively. A client app can be created to make this configuration easier in the meantime but such an app doesn't currently exist (if you're interested in making this let the [community](https://community.namebase.io/) know!).
