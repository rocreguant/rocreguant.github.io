---
title: "Aprendiendo un poco sobre Criptodivisas (Bitcoins y similares)"
date: "2014-02-03"
---

Cuando salió toda esta burbuja de los Bitcoins medité si debía escribir sobre el tema o no. Finalmente decidí que ya había mucha gente escribiendo por lo que me decanté por el no, pero ahora algunas cosas han cambiado y me gustaría indagar un poco más sobre la parte técnica, filosófica y económica del Bitcoin así como muchas de las otras [cripto-divisas](http://es.wikipedia.org/wiki/Criptodivisa).

Al parecer hay muchas divisas similares al Bitcoin, pero con algunas características diferentes, como el tiempo de minado o la capitalización máxima y por supuesto el valor por unidad. Se puede encontrar una lista [Crypto-Currency Market Capitalizations](http://coinmarketcap.com/).

Junto al lado de cada divisa hay la capitalización total (en usd) del mercado, el precio por “unidad”, el total de monedas existentes en el momento, el volumen en negociación en 24h y la variación de la divisa en %. Finalmente hay una gráfica de la evolución de la capitalización de 7 días.

La idea principal de todas las cripto-divisas es poder efectuar pagos en Internet de forma directa, entre un usuario y otro, sin tener que pasar a través de los bancos. Esto es el concepto Peer to Peer (P2P) se realiza entre personas sin usar intermediarios.

Estas monedas a su vez no pueden ser falsificadas (a diferencia del dinero real). Todas las transacciones son registradas por todos los nodos (todos los monederos) y pueden ser traqueadas desde el inicio. Nadie puede añadir dinero a la red si no es minando.

La idea es que la **red se automodera** a si misma y los nodos son libre haciéndola “indestructible” todos dependen de todos y nadie depende de nadie.  
El minado consiste en añadir los registros de transacciones al “libro de contabilidad” (que es una cadena de bloques). Esta cadena de bloques es la confirmación para el resto de nodos que la transacción ha tenido lugar. Este es el sistema anti-fraude para evitar la falsificación de operaciones \[1\].

El minado es intencionalmente acaparador de recursos para conseguir que los bloques de nuevas divisas encontradas permanezca estable. Los bloques del minado tampoco pueden ser falsificados ya que incluyen una prueba de cómputo. Las pruebas de cómputo están vinculadas a los datos de cada bloque. La dificultad de estos cálculos se ajustan con el fin de limitar la velocidad de generación de nuevos bloques por la red cada 10 minutos \[2\].

El minado no es realizado por personas plenamente altruistas. Este es realizado con el fin de descubrir un bloque nuevo de Bitcoins y así ganar dinero. Consiguiendo así **una red descentralizada, segura y robusta**.

[Aquí el documento](http://bitcoin.org/bitcoin.pdf) de su creador, Satoshi Nakamoto (pseudónimo)

\[1\] [https://en.bitcoin.it/wiki/Mining](https://en.bitcoin.it/wiki/Mining)  
\[2\] [https://en.bitcoin.it/wiki/Proof\_of\_work](https://en.bitcoin.it/wiki/Proof_of_work)
