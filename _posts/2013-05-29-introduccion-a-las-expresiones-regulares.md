---
title: "Introducción a las expresiones regulares"
date: "2013-05-29"
categories: 
  - "analitica"
  - "manual"
  - "programacion"
  - "trucos"
tags: 
  - "expresiones-regulares"
  - "manual-2"
  - "patrones"
  - "programacion-2"
  - "truco"
---

Según la [wikipedia](http://es.wikipedia.org/wiki/Expresi%C3%B3n_regular) una **expresión regular**, a menudo llamada también **patrón**, es una expresión que describe un conjunto de cadenas sin enumerar sus elementos.

Ayuda a encontrar elementos en un texto que coincidan con la descripción de la expresión de un modo más simple y rápido que de cualquier otra forma.

Las expresiones regulares tengo que reconocer que son algo complicadas pero cuando se entiende tiene un enorme potencial. Pero algún día hay que empezar no? Así que mejor que nos pongamos manos a la masa.

Carácteres básicos:

- \\ para mi probablemente sea uno de los caracteres más importantes. Sirve para hacer que el carácter que precede pierda su significado y pase a ser un carácter normal. Por ejemplo \\\* pasaría a buscar un \* o \\\\ (doble barra invertida) pasaría a ser una sola.
    
- . indica que le falta un carácter es decir _'.asa'_ puede devolver _'casa'_, _'basa'_... pero nunca _'asa'_.
- ? indica que el elemento predecesor puede estar o no, por ejemplo _'casa?'_ Puede devolver _'casa'_ o _'cas'_.
- \* este elemento permite que el elemento anterior pueda estar desde 0 veces a infinitas, por ejemplo, _'casa\*'_ puede ser _'cas'_, _'casa'_ o _'casaaaaaaaaa'_...
- \+ implica que el carácter al que está asociado pueda por lo menos una o más veces. Sigamos con el ejemplo _'casa+'_ puede ser _'casa'_, _'casaaaa'_ pero en ningún caso _'cas'._
- ^ indica que está en el principio de la cadena.
    
- $ este por el contrario indica que se encuentra en el fin.
    
- () sirve para agrupar un conjunto de elementos, por lo que '_(casa)_' pararía a ser un solo elemento ocasionando que _'(casa)+'_ pudiera devolver '_casacasacasa_' o simplemente _'casa'_.
- | (barra vertical) sirve para marcar una 'o' (para los programadores seria el equivalente a una or). Por ejemplo '(casa|hogar)' puede devolver _'casa'_ o _'hogar'_, en ningún caso _'casahogar'_.
- \[\] los corchetes brindan la posibilidad de escoger entre uno de los elementos que están en su interior. Se pueden marcar rangos usando el guión medio. '_\[a-z\]_' nos puede devolver cualquier letra minúscula de la '_a_' a la '_z_'.
- {} puede contener uno o dos números separados por una coma. Vendría a ser el elemento propio equivalente y de uso idéntico a ?, +, \* pero personalizado. Por ejemplo '_{2, 7}_' quiere decir que el elemento se puede repetir mínimo dos veces pero con un máximo de 7. Con '_{7,}_' indicas que de 7 hasta infinito.
    

Mi primera expresión regular pensada íntegramente por mi y que funciona, sirve para encontrar las url de un texto.

_(https?\\:\\/\\/)\*\[0-9a-zA-z\\-\\\_\\.\]+\\.(com|es|net|org|info)\\/\*\[a-zA-z\\-\\\_\\.\\/\]\*_

 Pero vamos a verla por partes:

 _**(https?\\:\\/\\/)\***_ => Este trozo indica que tiene que usar el protocolo _'http'_ o _'https'_ (de aquí el interrogante después de la 's' juntamente con \\: para indicar que van los dos puntos y \\/ dos veces esto para señalar que quiero una barra normal.

_**\[0-9a-zA-z\\-\\\_\\.\]+**_ => esto sería el cuerpo de la url antes de la extensión. Puede constar de uno o más elementos en minúsculas, mayúsculas, números guiones o puntos (subdominios).

_**\\.(com|es|net|org|info)**_ => indica que ahora consta de un punto seguido de una de las extensiones com, es, net, org o info.

_**\\/\*\[a-zA-z\\-\\\_\\.\\/\]\***_ => y finalmente brinda la posibilidad de que sea un subdirectorio
