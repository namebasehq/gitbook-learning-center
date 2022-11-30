---
description: Un tutorial para resolver dominios de Handshake
---

# Acceder a los nombres Handshake

Los nombres de Handshake viven en la blockchain de Handshake, que la mayoría de los navegadores aún no admiten. Mientras esperamos que los navegadores se pongan al día, a continuación se muestran varias formas en las que puedes acceder a los nombres de Handshake en tu navegador.

{% embed url="https://youtu.be/vAMpfZnqG78" %}

## Nivel 1- La puerta

### HNS↗TO&#x20;

Utiliza el motor de búsqueda [HNS.to](https://hns.to/) para acceder a los nombres de Handshake sin instalar nada ni cambiar la configuración de DNS; intenta usarlo para buscar "welcome.nb" o cualquiera de [estos](https://github.com/namebasehq/awesome-handshake) sitios de Handshake. También puedes realizar búsquedas directamente agregando "hns.to/" delante de los dominios de Handshake como "[hns.to/welcome.nb](https://hns.to/welcome.nb)".

![](../.gitbook/assets/HNS.to.gif)

{% hint style="info" %}
HNS.to es un proyecto desarrollado veloped únicamente por el [Namer](https://discord.gg/V3aTrkp) @nijynot/
{% endhint %}

## Nivel 2 - Navegador

### Navegador de móvil Puma

{% embed url="https://www.pumabrowser.com/" %}

Instala la aplicación del navegador Puma en tu móvil para acceder a los nombres de Handshake en tu barra de búsqueda.

{% hint style="info" %}
Puma es un proyecto desarrollado por el Namer [@html5cat/](https://hns.to/html5cat).
{% endhint %}

### LinkFrame

![](../.gitbook/assets/linkframe.jpg)

Instala la [extensión LinkFrame](https://chrome.google.com/webstore/detail/linkframe/klcheodcjdbkbiljlcfiphagmkhbifmm?hl=en-US\&authuser=0) para acceder a los nombres de Handshake directamente en la barra de búsqueda de tu navegador Chrome; intenta usarlo para buscar "welcome.nb /" o cualquiera de [estos](https://github.com/namebasehq/awesome-handshake) sitios de Handshake.

{% hint style="info" %}
LinkFrame es un proyecto desarrollado únicamente por el [Namer](https://discord.gg/V3aTrkp) @linkframe/.
{% endhint %}

### Resolvr add-on

![](<../.gitbook/assets/resolvr (1).png>)

Instala el  [add-on Resolvr](https://addons.mozilla.org/en-US/firefox/addon/resolvr/?src=search) para acceder directamente a los nombres Handshake desde la barra de búsqueda de tu navegador Firefox — intenta usarlo para buscar "welcome.nb/" o cualquiera de [estos](https://github.com/namebasehq/awesome-handshake) sitios Handshake.&#x20;

{% hint style="info" %}
Resolvr es un proyecto desarrollado únicamente por el [Namer](https://discord.gg/V3aTrkp) @codecrafting.
{% endhint %}



## Nivel 3 - DNS

### NextDNS

![](../.gitbook/assets/nextdns.png)

"NextDNS te protege de todo tipo de amenazas de seguridad, bloquea anuncios y rastreadores en sitios web y aplicaciones, además de brindar una Internet segura y supervisada para niños, en todos los dispositivos y en todas las redes".

1. Visita [nextdns.io](https://nextdns.io) y clica "Try it now"
2. Desplázate hacia abajo hasta la Guía de configuración y elige cualquiera de las opciones dadas (por ejemplo, DNS privado, Aplicación, Ipv4) para tu dispositivo, y sigue la guía destacada proporcionada por NextDNS.
3. Una vez que tu dispositivo esté conectado a NextDNS (confirma con el botón verde en la parte superior de la página de configuración), visita la pestaña "Configuración" en el sitio web de NextDNS y activa "Resolver dominios de Handshake"
4. Visita nuestra página de bienvenida de Handshake en [http://welcome.nb/](http://welcome.nb/)!

![](<../.gitbook/assets/Screen Shot 2020-11-20 at 01.09.32.png>)

{% embed url="https://www.youtube.com/watch?v=hiEmV4-RT3U&feature=youtu.be" %}

### easyhandshake

{% embed url="https://matthewzipkin.medium.com/resolving-hns-names-using-dns-over-https-94643fe62ecd" %}

{% hint style="info" %}
easyhandshake es un proyecto desarrollado únicamente por el [Namer](https://discord.gg/V3aTrkp) @pinheadmz.proofofconcept/.
{% endhint %}

### Resolvr

![](<../.gitbook/assets/resolvr (1).png>)

Ves a la configuración de red de tu dispositivo y agregue la dirección 18.207.80.99 IP de [Resolvr](https://resolvr.info/)  para resolver los nombres de Handshake a través de cualquier navegador en tu dispositivo.&#x20;

![](<../.gitbook/assets/Resolvr DNS.png>)

Alternativamente, puedes configurar el proveedor de DNS de tu navegador en "[https://dns.resolvr.info/dns-query](https://dns.resolvr.info/dns-query)" de Resolvr para resolver nombres de protocolo de enlace solo a través de ese navegador.

![](<../.gitbook/assets/Resolvr Browser DNS.png>)

{% hint style="info" %}
Resolvr es un proyecto desarrollado solamente por el [Namer](https://discord.gg/V3aTrkp) @codecrafting.
{% endhint %}



## Nivel 4 - SPV light client

![](<../.gitbook/assets/Handshake LinkedIn.png>)

Para los más expertos en tecnología, puede ejecutar [tu propio nodo SPV con HNSD](https://github.com/handshake-org/hnsd) para resolver sin confianza nombres de Handshake sin ejecutar un nodo completo.

Handshake es la única cadena de bloques de nombres con una [resolución de DNS recursiva ligera](https://github.com/handshake-org/hnsd), que puede integrar fácilmente en navegadores, aplicaciones y dispositivos. Un solucionador de DNS recursivo es una pieza de software que puede resolver recursivamente nombres de dominio en direcciones IP. El cliente ligero puede resolver sin confianza nombres de protocolo de enlace utilizando solo 10 MB de memoria y prácticamente cero CPU. Es la forma más segura de usar Handshake porque no requiere confiar en ningún solucionador de terceros que pueda inspeccionar tu tráfico de DNS.&#x20;

## Nivel 5 - HSD

### HSD

{% embed url="https://github.com/handshake-org/hsd" %}

Ejecuta HSD localmente para acceder a Handshake de la forma más descentralizada, privada y segura.

### HSD en Raspberry Pi

{% embed url="https://gist.github.com/pinheadmz/a3e5ded7a4f0413e948a6a257c375891" %}

Instala HSD en Raspberry Pi para que cualquier dispositivo conectado a la red inalámbrica de tu hogar pueda resolver los nombres de Handshake.
