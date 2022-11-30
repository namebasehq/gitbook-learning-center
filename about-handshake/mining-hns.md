---
description: Guía para minar monedas Handshake
---

# Minar HNS

Las tarifas de minería de handshake son actualmente de \~ 0.1 HNS

{% embed url="https://www.youtube.com/watch?v=vE0mfLMuocE&feature=emb_title" %}

{% hint style="info" %}
Este video tutorial fue creado por el Namer [skyinclude/](https://hns.to/skyinclude/)
{% endhint %}

## Handshake Blocks

### Tiempo por Bloque

1 El tiempo por bloque de Handshake es = 10 minutos, que es la cantidad de tiempo promedio que se tarda en extraer el siguiente bloque de Handshake. Dicho esto, en realidad es más probable que los bloques se extraigan en menos de 10 minutos porque un bloque que lleva mucho tiempo necesitaría equilibrarse con muchos bloques "rápidos". Por ejemplo, si asumimos que los bloques "rápidos" tardan 9 minutos en extraerse (en realidad, es totalmente aleatorio), un solo bloque "lento" que tarda 1 hora en extraerse debería equilibrarse con cincuenta bloques "rápidos" para obtener un promedio de 10 minutos.

### Límites por Block

Cada bloque de Handshake tiene los siguientes límites:

* [600 "actualizaciones"](https://github.com/handshake-org/hsd/blob/af86d4899791601d10212115c80a2f2136fdb004/lib/protocol/consensus.js#L200) que son `OPEN`, `UPDATE`, `TRANSFER` y `REVOKE` covenants.
  * un sub-límite de [300 aperturas](https://github.com/handshake-org/hsd/blob/af86d4899791601d10212115c80a2f2136fdb004/lib/protocol/consensus.js#L192), que son justo `OPEN`. Ten en cuenta que estas 300 aperturas son un subconjunto de las 600 actualizaciones
* [600 "renovaciones"](https://github.com/handshake-org/hsd/blob/af86d4899791601d10212115c80a2f2136fdb004/lib/protocol/consensus.js#L208), que son `FINALIZE`, `REGISTER`, y `RENEW` covenants.

## ASICs HS1 y HS1+ por Goldshell

{% hint style="info" %}
Esta gúia fue creada enteramente por el Namer [tigs/](https://hns.to/tigs/)!
{% endhint %}

¡Hola chicos y chicas!&#x20;

¡Pensé que finalmente debería escribir algo sobre cómo configurar de manera correcta el Goldshell HS1 + para minar en una máquina con Windows!

&#x20;¡¡¡ADVERTENCIA!!! Ten en cuenta que estas instrucciones son SOLO para los dispositivos HS1 y HS1 + fabricados por Goldshell. Bajo ninguna circunstancia debes seguir esta guía en ningún otro minero ASIC o minero HNS.

En primer lugar, probablemente sea mejor grabar algunos archivos de aquí y allá para hacer esta instalación y configuración mucho más sencilla. Lo primero que querrás obtener es la última versión de firmware para tu minero ASIC. Esto es muy importante ya que es el firmware el que generalmente dicta la estabilidad y longevidad de tu nuevo dispositivo de hardware. Sin mencionar que cuanto más reciente sea el firmware, es más probable que las cosas simplemente hagan "clic" y funcionen cuando llegue ese momento.

[https://github.com/goldshellminer/HS1/tree/master/firmware](https://github.com/goldshellminer/HS1/tree/master/firmware) ← es el sitio web para descargar el firmware más reciente para tu dispositivo. En el momento de escribir estas líneas, la versión 0.0.4 era la más reciente.

### Requisitos previso para usuari@s deWindows:

Decarga el controaldor de serie STM32 [STSW\_STM32102\_V1.5.0.rar](https://github.com/goldshellminer/HS1/tree/master/miner/serial\_driver). Selecciona la versión del controlador de tu SO para instalar.

#### Descargar software de minero compatible (dos opciones):

Opción 1: Goldshell Miner versión 1.0.4 o superior: (solo Windows)

[https://github.com/goldshellminer/HS1/tree/master/miner](https://github.com/goldshellminer/HS1/tree/master/miner)

Opción 2: Handyminer CLI y GUI (Windows, Linux, MacOs)

[https://github.com/HandyMiner/HandyMiner-Goldshell-CLI ](https://github.com/HandyMiner/HandyMiner-Goldshell-CLI)(Interfaz de línea de comandos)

[https://github.com/HandyMiner/HandyMiner-Goldshell-GUI](https://github.com/HandyMiner/HandyMiner-Goldshell-GUI) (Interfaz gráfica del usuario)

**Conecta el hardware en esta secuencia**

A. Enchufe el cable de alimentación.

B. Conecta el minero HS1 o HS1-PLUS con el cable USB a la computadora

[https://www.goldshell.com/2020/09/23/hs1%e3%80%81hs1-plus-firmware-update-2020-9-21/](https://www.goldshell.com/2020/09/23/hs1%E3%80%81hs1-plus-firmware-update-2020-9-21/) ← Es muy recomendable actualizar tu firmware y se puede conseguir siguiendo esta guía. Lo siento por la gente pero la esencia es esta. ¡Básicamente, sigue el paso 2 PRIMERO! Asegúrate de que el minero esté en un estado inactivo (todavía enchufado a la corriente y a la computadora, por supuesto, y que aparece como un cuadro azul cuando se hace clic en el software Goldshell). Segundo desde el extremo derecho; Debería decir "Actualizar firmware" si pasas el mouse sobre él durante uno o dos segundos. Con un clic, navega hasta el archivo de firmware HS1-Plus que descargastes anteriormente y deja que se instale en el ASIC Miner.&#x20;

¡Ahora! Aquí es donde se reduce a la preferencia personal sobre qué programa de minería utilizar; pero yo personalmente prefiero usar la versión GUI (Graphical User Interface) de HandyMiner. Nunca me ha confundido y le saco bastante jugo, ¡alcanzando hasta 115GH / S en lugar de 105GH /. Sin embargo, esto no les sucede a todos, he intentado minar en una gran cantidad de computadoras y no puedo identificar qué es exactamente lo que los hace funcionar más rápido o a la velocidad anunciada.

Recomiendo encarecidamente usar HandyMiner, en lo que a fuerza y estabilidad se refiere. Conecta la alimentación a tu ASIC, luego el cable USB a la computadora. Al ejecutar HandyMiner, ya conoces los principales grupos que se utilizan para la minería HNS, lo que facilita un poco las cosas. De todos modos; Yo uso Dxpool.com, porque es lo que Goldshell recomienda en su sitio web. Por supuesto, elige el grupo de minería que prefieras; pero trata de estar al tanto de qué sitios son más populares que otros y las recompensas totales que te cobrarán (fee). (En algunos casos 2-3%, otros 4%)

También he establecido una cantidad de retiro automático para el grupo / sitio para el que mino; lo que hace que sea muy sencillo dejar la máquina encendida las 24 horas del día, los 7 días de la semana y seguir recibiendo un pago decente. Yo uso [https://bobwallet.io/](https://bobwallet.io/): una billetera dedicada exclusivamente al uso de Handshake y que te permite guardar tu clave privada. De esa manera, mantengo las palabras seguras y puedo dormir profundamente sabiendo que mi SNP no desaparecerá si mi nombre de usuario y contraseña se han visto comprometidos.

Hay mucho más en este asunto de la minería de lo que parece, así que POR FAVOR, acude a mí para cualquier pregunta y me hace feliz el poder ayudar.

¡Puede contactar conmigo en tigs # 2777 en Discord!

Happy Mining!

## 6miner <a href="#lets-get-started." id="lets-get-started."></a>

{% hint style="warning" %}
Esta sección está desactualizada, si tienes un tutorial de minería, compártelo en la [comunidad  Namer](https://hns.to/community.nb/) y actualizaremos esta página con la tuya.
{% endhint %}

### Empecemos.

Hay tres pasos principales que te preparan para comenzar a minar HNS.&#x20;

1. [Regístrate en Namebase para obtener la dirección de tu billetera HNS](mining-hns.md#step-1:)
2. [Ejecuta el software de minado 6miner](mining-hns.md#step-2:-run-6miner)
3. [Retira HNS a la dirección de tu billetera HNS](mining-hns.md#step-3:-withdraw-to-your-hns-wallet-address)

### Paso 1: Regístrate en Namebase

La primera parte de este proceso es crear una dirección de billetera de Handshake. Para hacerlo, simplemente [crea](https://www.namebase.io/register)  tu cuenta de Namebase y completa tu registro.

Después de completar tu registro, verás una pestaña \[Dashboard] en la parte superior de navegación. Cuando llegues a la página del Dashboard, verás una tarjeta de color azul oscuro que mostrará tu saldo de HNS disponible. En la parte inferior de la tarjeta, verás una cadena de números y letras. Esta es la dirección de tu billetera HNS. Puedes copiarla fácilmente usando la función de portapapeles junto a la dirección de tu billetera. observa la captura de pantalla que tienes a continuación como referencia.&#x20;

![Obtener la dirección de su billetera](https://images.ctfassets.net/v3ez3dek3dk6/nL4gnWryoociAFJdl0YKG/830e91a1843bb31ad0c486f55eaa8a2d/Dashboard\_image.png?fit=pad\&w=720)

### Paso 2: Ejecuta 6miner &#x20;

Este paso requiere registrarse, instalar y ejecutar un software de minería Handshake. Este tutorial usa 6miner y el mining pool 6block.

Para comenzar este proceso, regístrate en 6block [aquí](https://6block.com/register) antes de minar  Handshake para configurar la dirección de la billetera, el monitoreo de los workers, los ingresos y la verificación de los registros de pago.

El algoritmo de Handshake es blake2b + sha3.

#### Qué es 6block?

6block es uno de los primeros mining pools que está listo para el lanzamiento de Handshake. 6block está construido para el rendimiento y diseñado para ser estable, rápido y seguro.

#### Qué es 6miner?&#x20;

6miner es un minero altamente optimizado para Handshake y funciona un 20% más rápido que HandyMiner en la mayoría de las GPU probadas. Es un competidor directo de HandyMiner, que también es un minero muy bueno.

Se proporcionan enlaces a ambos mineros y animamos a las personas a probar y decidir qué opción les conviene más.

### Instala controladores de GPU

Para minar Handshake, necesitarás tener los controladores de la GPU instalados en tu ordenador. 6 miner funciona con tarjetas AMD y Nvidia, aquí se explica cómo instalar los controladores:

#### Nvidia GPU&#x20;

Aquí hay un muy buen tutorial sobre cómo instalar los controladores de Nvidia en Ubuntu:[https://www.linuxbabe.com/ubuntu/install‐nvidia‐driver‐ubuntu‐18‐04 ](https://www.linuxbabe.com/ubuntu/install%E2%80%90nvidia%E2%80%90driver%E2%80%90ubuntu%E2%80%9018%E2%80%9004)

#### AMD GPU&#x20;

Aquí está el tutorial oficial de AMD para instalar amdgpu ‐ pro en Ubuntu y CentOS: [https://amdgpu‐install.readthedocs.io/en/latest/ ](https://xn--amdgpuinstall-gm6g.readthedocs.io/en/latest/)

Para Ubuntu, asegúrate de descargar desde este enlace: se recomienda la versión 19.50, ya que admitirá hasta 5700XT (aproximadamente 240 mh de hashrate): h[ttps://drivers.amd.com/drivers/linux/19.50/amdgpu‐pro‐19.50‐967956‐ubuntu‐18.04.tar.xz ](https://drivers.amd.com/drivers/linux/19.50/amdgpu%E2%80%90pro%E2%80%9019.50%E2%80%90967956%E2%80%90ubuntu%E2%80%9018.04.tar.xz)



### Configuración de 6miner

1. Ves a http://github.com/6block/6miner/releases&#x20;
2. Descargue el archivo de lanzamiento, actualmente:https://github.com/6block/6miner/releases/download/v0.0.1/6miner‐v0.0.1‐amd64‐ linux.tar.gz&#x20;
3. Abre la terminal y descomprime el archivo: tar -xpf 6miner-v0.0.1-amd64-linux.tar.gz&#x20;
4. Entra en la carpeta que acabas de crear: cd 6miner-v0.0.1-amd64-linux&#x20;
5. Como podrás ver a continuación, abre el script de minería con tu editor preferido, aquí usamos "nano":nano mine\_hns.sh&#x20;
6. Edita la configuración y cambia lo siguiente: 6.1 POOL (si minas en un mining pool diferente a 6block)
7. USERNAME: Este es el nombre de usuario que registraste en el grupo, puedes hacer algo como myusername.1 6.3 PWD: Puede ser cualquier cosa, como una "x" será suficiente 6.4 VENDOR: amd/nvidia dependiendo de tu GPU
8. Una vez que hayas terminado, guarda y sal del archivo presionando"ctrl +x y entonces presiona Y cuadno te lo pregunte"&#x20;
9. Empieza a minar con ./mine\_hns.sh y presiona Enter

![6miner download](https://images.ctfassets.net/v3ez3dek3dk6/qPFTr3sfS97ynwvqQuNmC/141771957b7be99be5d8e62750646683/6miner1.png?fit=pad\&w=720)

Actualmente solo hay una compilación de Linux ‐ 64bit, elije esa. El minero funcionará en cualquier distribución de Linux, asegúrate de tener instalados los controladores de GPU correctos.

![6miner download](https://images.ctfassets.net/v3ez3dek3dk6/63Hd01YJ3Mkfm3q6rRTfvh/ffee9244d61eaa998d4d4d6c0473a21d/6miner2.png?fit=pad\&w=720)

![6miner folder](https://images.ctfassets.net/v3ez3dek3dk6/4xCHci1ZQXyWcPoMHPAmp1/54f2ae2bfe010f7f7a137e07d3edadff/6miner3.png?fit=pad\&w=720)

![Editing 6miner config](https://images.ctfassets.net/v3ez3dek3dk6/2Rs0HnYZNlGMum2rZSJmkd/dd708841383904dc1e9b46abe680a9c1/6miner4.png?fit=pad\&w=720)

![Mining successful!](<../.gitbook/assets/image (3).png>)

Ten en cuenta que la lectura de 64,7 MH / s es tu hashrate. Esta es de una Radeon RX 580 de 8GB. Muy buenos resultados. Ves a [https://6block.com](https://6block.com) y dirígete a "Mi página de inicio", esto te mostrará tu panel actual y todas las estadísticas de minería que necesitarás.

### Configuración de Handyminer

Todos los pasos de instalación se detallan aquí [https://github.com/HandshakeAlliance/HandyMiner‐CLI](https://github.com/HandshakeAlliance/HandyMiner%E2%80%90CLI)&#x20;

### Paso 3: Retira a tu dirección de billetera HNS

Ves a [https://6block.com](https://6block.com), haz clic en tu dirección de correo electrónico en la esquina superior derecha y luego en "Settings".

![Withdrawing HNS from 6block. ](https://images.ctfassets.net/v3ez3dek3dk6/2SZcD2m8syU8xa6VT02J6y/6d912d81baa0c0bd0580a46239d4e68d/Image\_from\_iOS\_\_11\_.jpg?fit=pad\&w=720)

Desde tu configuración, haz clic en Mining Accounts y pegua la dirección de tu billetera Namebase HNS para retirar tus HNS a Namebase.

Con todo, debería ser sencillo comenzar a minar HNS. Visita el canal [#mining ](https://discord.gg/A4f7CNr)de la  [Comunidad Namer](https://discord.gg/V3aTrkp), donde incluso los creadores de estos mineros pululan, para preguntar y discutir sobre la minería de Handshake.
