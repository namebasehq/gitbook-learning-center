---
description: HNSDoH is a public DNS resolver that supports Handshake domains
---

# HNSDoH

HNSDoH provides a public DNS resolver with Handshake support available from multiple IP addresses for stability. You can get an up to date list of IP addresses from the [HNSDoH website](https://welcome.hnsdoh.com/).


Once you've configured HNSDoH you can visit Handshake domains directly in your browser (i.e. try visiting [nathan.woodburn/](http://nathan.woodburn/) once you've configured HNSDoH). You can also use HNSDoH programmatically in applications to query Handshake domains just like you would use a traditional DNS resolver like Cloudflare's 1.1.1.1 or Google's 8.8.8.8.

```bash
dig @hnsdoh.com nathan.woodburn
dig @hnsdoh.com hnsdoh TXT
```

## DNS-over-HTTPS (DoH)

HNSDoH offers DNS-over-HTTPS resolvers with support for wireformat queries available at:

```
https://hnsdoh.com/dns-query
```

You can use knot dns utils to query HNSDoH easily:

```bash
kdig @hnsdoh.com +https nathan.woodburn
kdig @hnsdoh.com +https hnsdoh TXT
```

You can use curl's DoH flag to query Handshake endpoints in shell scripts easily:

```javascript
curl --doh-url https://hnsdoh.com/dns-query http://hnsdoh/
```

## DNS-over-TLS (DoT)

HNSDoH also offers DNS-over-TLS resolvers available at: hnsdoh.com:853

```bash
kdig @hnsdoh.com +tls nathan.woodburn
kdig @hnsdoh.com +tls hnsdoh TXT
```


## Using HNSDoH in Node.js
Here's an example on how to query the DoH resolver in Node.js. Note that you must install the [dohjs](https://www.npmjs.com/package/dohjs) package first.

```bash
npm i dohjs
```

```javascript
const doh = require('dohjs');

const resolver = new doh.DohResolver('https://hnsdoh.com/dns-query');

const getTxt = async (name) => {
	const response = await resolver.query(name, 'TXT');
	console.log(name)
	if(response.answers.length > 0){
		response.answers.forEach(ans => console.log(ans.data.toString()));
	}else{
		console.log('---')
	}
};

(async() => {
	await getTxt('hnsdoh');
	await getTxt('1.wdbrn');
	await getTxt('nathan.woodburn');
})()
```

