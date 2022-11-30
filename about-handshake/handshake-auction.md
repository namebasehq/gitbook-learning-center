---
description: Acerca de las subastas Vickrey de nombres Handshake
---

# Subasta Handshake

## Proceso de Subasta

Des del 14 de febrero de 2020, los nombres de Handshake se publican al azar en lotes semanales a lo largo de 52 semanas. Cada semana, se desbloquean nuevos nombres  para pujar, lo que garantiza que los que llegan tarde todavía tengan la oportunidad de pujar por nombres "buenos".

Una vez que se ha publicado un nombre, puedes realizar una oferta con monedas Handshake (HNS), lo que activará el período de puja de 720 bloques (\~ 5 días) de la subasta del nombre. Las ofertas pueden tener cualquier valor y, opcionalmente, puede añadir un cegamiento para ocultar el valor real de tu puja a los demás.A tu puja+ciego se llama bloqueo, que es el único valor que ven otros postores.

Una vez finalizado el período de licitación, comenzará el período de revelación del bloque 1440, durante el cual los postores deben revelar el valor de sus pujas para que se pueda determinar un ganador (de lo contrario, solo se conocen los bloqueos y no el valor de las ofertas). Si añadiste una cantidad cegada, ésta se te devolverá inmediatamente cuando revele tu oferta. Si olvidas revelar tu bloqueo, se perderá para siempre y tu oferta no se contará. Sin embargo, Namebase realiza la revelación automáticamente por ti, por lo que si eres un usuario de Namebase, no tendrás que preocuparse por este paso.

Una vez que finaliza el período de revelación, el/la postor/a que realizó la oferta más alta solo pagará la cantidad de la oferta segunda más alta, se le reembolsará la diferencia entre su oferta y la segunda oferta más alta, y recibirá el nombre que ganó. Los/as postores/as que pierdan recibirán su oferta completa de vuelta. Si solo hay una oferta, el/la único/a postor/a recibirá ese nombre gratis porque la segunda oferta más alta es efectivamente "0". Ten en cuenta que el pago del/la ganador/a se quema de la cadena de bloques, por lo que el/la ganador/a no paga ofertas a nadie, creando efectos deflacionarios en el precio de HNS.

Comprueba tu comprensión de las subastas de nombres Handshake con estos casos prácticos.

## Cegamientos y bloqueos

Cantidad bloqueada = Cantidad de la puja + Cegamiento añadido

Tu bloqueo es la suma de tu puja más el cegamiento. A esto se le llama "lockup" ya que no podrás usar tus HNS bloqueados hasta que la audición acabe.

Es importante tener en cuenta que solo las pujas determinan a los ganadores de las subastas; los cegamientos son completamente opcionales. Agregar cegamientos puede ser útil porque ocultan el valor de tu oferta y hace que parezcan más altas para los demás (solo tú puedes ver el monto de tu oferta, mientras que el "lockup" es lo que se muestra a otros pujadores). También el cegamiento lo recibes de vuelta al comienzo del período de revelación, mientras que tu puja solo una vez que finaliza el período de revelación.

Tu bloqueo ("lockup") no se puede actualizar después de enviarlo. Puedes enviar bloqueos adicionales, pero los anteriores seguirán bloqueados (por ejemplo, si envías dos bloqueos de 1,000 HNS y 10,000 HNS, 11,000 HNS estarán bloqueados durante la duración de la subasta).

## ¿Qué ocurre si hay un empate?

Si empataste con otra persona pero ella ganó, hay dos posibilidades:

1. Es posible que en realidad te hayan superado la puja por una pequeña cantidad. Ves a la página de la subasta en un ordenador (no en un dispositivo móvil) y pasa el mouse sobre las cantidades de la oferta para mostrar más decimales. Namebase muestra 2 decimales de forma predeterminada, por lo que si  pujas 1 HNS y otra persona puja 1.0001 HNS, ganarás, pero tus pujas se verán idénticas a menos que pases el mouse sobre el bloqueo.
2. Si tú y la persona que ganó realmente hicisteis ofertas idénticas, quien revele la transacción gana primero. Sin embargo, si tanto túcomo el ganador sois usuarios de Namebase, el ganador será elegido al azar porque Namebase revela todas las ofertas casi al mismo tiempo.

Muchos emaptes son causados por que los humanos prefieren números redondos. Si siempre ofertas 1.xx en lugar de 1, empatarás con menos frecuencia.

## Estudios de casos

Verifica tu comprensión del proceso de subasta de nombres respondiendo:

1. ¿Qué postor/a ganó?
2. ¿Cuántos HNS quemó el/la ganador/a?
3. ¿Cuántos HNS recibirá de vuelta el/la ganador/a?

#### Estido de Caso 1

| Pujador/a | Bloqueo   | Cantidad puja | Cegamiento |
| --------- | --------- | ------------- | ---------- |
| A         | 1,000 HNS | 1,000 HNS     | 0 HNS      |
| B         | 1,000 HNS | 100 HNS       | 900 HNS    |
| C         | 1,000 HNS | 10 HNS        | 990 HNS    |

#### Estido de Caso 2

| Pujador/a | Bloqueo   | Cantidad puja | Cegamiento |
| --------- | --------- | ------------- | ---------- |
| A         | 1,100 HNS | 100 HNS       | 1,000 HNS  |
| B         | 650 HNS   | 150 HNS       | 500 HNS    |
| C         | 2,050 HNS | 50 HNS        | 2,000 HNS  |

#### Estido de Caso 3

| Pujador/a | Bloqueo     | Cantidad puja | Cegamiento |
| --------- | ----------- | ------------- | ---------- |
| A         | 1,000 HNS   | 1,000 HNS     | 0 HNS      |
| B         | 10,000 HNS  | 1,000 HNS     | 9,000 HNS  |
| C         | 100,000 HNS | 1,000 HNS     | 99,000 HNS |

### Respuestas

#### Estudio de caso 1

1. El/la postor/a A ganó porque tenía la canitdad de la oferta más alta en 1,000 HNS
2. El/la postor/a A quemó 100 HNS porque la segunda oferta más alta fue 100 HNS
3. El/la postor/a A recibe un reembolso de 900 HNS porque solo quemó 100 HNS de su oferta de 1000 SNP

#### Estudio de caso 2

1. El/la postor/a B ganó porque tenía la cantidad de oferta más alta en 150 HNS
2. El/la postor/a B quemó 100 HNS porque la segunda oferta más alta fue 100 HNS
3. El/la postor/a B recibe un reembolso de 50 HNS porque solo quemó 100 HNS de su oferta de 150 HNS; también recibirá la cantidad cegada, igual que todos los demás.

#### Estudio de caso 3

1. El ganador aquí es un poco difícil de determinar porque los/as 3 postores/as empataron con pujas idénticas de 1,000 HNS. El/la ganador/a de una subasta con pujas idénticas de la oferta ganadora lo determina el/la postor/a que revele primero la cantidad de la oferta. Sin embargo, si los/as 3 postores/as son usuarios/as de Namebase, entonces el/la ganador/a es aleatorio.
2. El/la ganador/a quemó 1.000 HNS porque la segunda oferta más alta también fue de 1.000 SNP.
3. El/la ganador/a no recibe ningún reembolso de la puja porque ha quemado toda su oferta de 1.000 HNS; seguirá recibiendo todo su ciego añadido al igual que todos/as los/as demás

## Notas sobre el "sniping"

Si bien Namebase envía tus ofertas casi instantáneamente a la cadena de bloques, es posible que los mineros aún necesiten algunos bloques para agregarlas a la cadena de bloques. Dicho esto, existe un abanico de riesgo-recompensa para hacer tus ofertas en el último minuto (coloquialmente llamado "sniping"): cuanto más tarde hagas tus ofertas, menos información revelarás al mercado, pero mayor será la probabilidad de que tu oferta no llegue a la cadena de bloques.&#x20;

Al hacer una oferta por un nombre que realmentete importa (por ejemplo, su nombre, apellido), te recomendamos encarecidamente que coloques su cantidad real de la oferta enmascarado con un ciego  mucho antes del final de una subasta. De esta manera, puedes asegurarte de que tu oferta se incoroper a la cadena de bloques a tiempo y de que, si obtiene una oferta superior, puedes estar seguro de saber que alguien más simplemente estaba dispuesto a pagar más por el nombre. Por ejemplo, si realizas una oferta de 5 HNS por tu nombre, estás indicando que no estarías dispuesto a pagar más de 5 HNS por él y que estaría bien entregárselo a otra persona que oferte más.
