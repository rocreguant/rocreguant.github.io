---
title: "Cómo funciona vi, el editor de textos de GNU/Linux"
date: "2011-11-10"
categories: 
  - "gnulinux"
  - "manual"
tags: 
  - "consola"
  - "editor-de-textos"
  - "gnulinux-2"
  - "shell"
  - "terminal"
  - "vi"
---

Antes de nada me gustaría aclarar que es vi. Vi es un editor de texto que no se preocupa por la visualización del documento, por lo tanto simplemente nos permite escribir un archivo en texto llano. La característica de vi en GNU/Linux es que normalmente se usa desde la consola y sólo los usuarios más avanzados saben usarlo correctamente.

Voy a contar un “chiste” relacionado. Sabes como generar una secuencia de caracteres aleatoria? … Ábrele vi a una persona cualquiera y dile que lo cierre. Esto si que es un chiste pero no dista mucho de la realidad, mucha gente no sabe como usarlo aunque las funcionalidades básicas no tengan mucha complicación. En este post explicaré **como funcionan las opciones básicas de vi** para poder **editar textos desde la consola**.

Para **abrir vi desde la consola**, deberemos poner _vi NombreFichero._ NombreFichero puede ser un fichero nuevo que deseemos crear o un fichero ya existente que esté en la carpeta donde tenemos la consola (me refiero a que al hacer un ls podamos encontrar el nombre del fichero).

Ahora ya tendremos el fichero abierto, y ya podremos escribir, pero no podremos borrar! Si usamos la tecla _Supr_ si, pero no con la de borrar “normal”.

Para **parar de escribir** deberemos pulsar la tecla _Esc_ y podremos usar las flechas para movernos por el documento, mientras escribíamos no se podía ya que aparecían letras.

Ahora **fuera el modo de escritura podemos borrar letras** colocando el cursor sobre ellas y pulsando la letra _x_, si queremos **borrar una** **linea** **entera** nos ponemos sobre ella y pulsamos dos veces la letra _d_.

Si queremos **volver a editar** pulsando la letra _a_ una vez podremos empezar a escribir.

Dónde aparezca el símbolo ~ (en azul, por lo menos a mi) significa que ya se ha terminado el documento.

Ahora viene la parte difícil, **para salir** hay distintos modos. Puedes salir a secas, o guardar y salir. Primero en ambos casos tienes de **asegurarte que no estas en modo escritura** (dándole al _Esc_ es suficiente ya que si no estás en modo escritura no pasará nada).

**Para salir a saco escribe _:q!_** _(con los 3 caracteres). Si deseas_ **guardar y salir debes escribir _:wq_** (también los 3 caracteres).

En ambos casos cuando escribas los dos puntos verás que el cursor se pone al final del documento, esto es normal.

Espero que os haya servido y cada vez que tengáis que editar un fichero con el comando sudo es sea más fácil y no se convierta en un sufrimiento ;)

Si andas buscando algún otro comando específico coméntame y te intentaré ayudar.
