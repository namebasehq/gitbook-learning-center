---
description: HDNS is a public DNS resolver that supports Handshake domains
---

# HDNS.io

HDNS provides a public DNS resolver with Handshake support available at the following IP addresses:

```
103.196.38.38
103.196.38.39
103.196.38.40
```

Once you've configured HDNS ([instructions](https://hdns.io)) you can visit Handshake domains directly in your browser (i.e. try visiting [welcome.nb/](http://welcome.nb/) once you've configured HDNS). You can also use HDNS programmatically in applications to query Handshake domains just like you would use a traditional DNS resolver like Cloudflare's 1.1.1.1 or Google's 8.8.8.8.&#x20;

```bash
dig @103.196.38.38 niccarter
dig @103.196.38.38 welcome.nb
```

## DNS-over-HTTPS (DoH)

HDNS offers DNS-over-HTTPS resolvers with support for wireformat queries available at:

```
https://query.hdns.io/dns-query
```

You can use curl's DoH flag to query Handshake endpoints in shell scripts easily:

```javascript
curl --doh-url https://query.hdns.io/dns-query http://welcome.nb/
```

Here's an example on how to query the DoH resolver in Node.js. Note that you must install the [dohjs](https://www.npmjs.com/package/dohjs) package first.

```bash
npm i dohjs
```

```javascript
const doh = require('dohjs');

const resolver = new doh.DohResolver('https://query.hdns.io/dns-query');

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
	await getTxt('f44ca263-6f26-410d-a08a-ac3bb0f7c480._auth.johnxu');
	await getTxt('f44ca263-6f26-410d-a08a-ac3bb0f7c480._auth.qq.johnxu');
	await getTxt('f44ca263-6f26-410d-a08a-ac3bb0f7c480._auth.vv.johnxu');
})()
```

