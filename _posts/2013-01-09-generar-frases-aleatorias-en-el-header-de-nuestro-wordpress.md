---
title: "Generar frases aleatorias en el header de nuestro Wordpress"
date: "2013-01-09"
categories: 
  - "manual"
  - "programacion"
  - "wordpress-2"
tags: 
  - "css"
  - "frases-aleatorias"
  - "manual-2"
  - "php"
  - "programacion-2"
  - "wordpress"
---

Hace tiempo vi algunas webs que tenían frases aleatorias en el header del blog. Y la idea me gustó, así que me la anoté. Ahora por fin he tenido algo de ganas y tiempo para llevarla a cabo y escribir su post correspondiente :P Empecemos!

Primero por la programación, añadiremos la función al archivo functions.php de nuestro theme de Wordpress y luego ejecutaremos la función en el header de nuestro blog. Vamos a ver lo más detallado.

El código que va a functions.php:

> function frases() {
> 
> $frase\[0\] = "Hola a todos";
> 
> $frase\[1\] = "Adios a todos";
> 
> $frase\[2\] = "me gustan los árboles";
> 
> $cantidad = count($frase)-1;
> 
> echo $frase\[rand(0,$cantidad)\];
> 
> }

Como veis es de lo más sencillo. Simplemente tenéis que cambiar las frases ya existentes y si queréis poner más teneis que añadir **_$frase\[3\] = “nueva frase”;_** cambiando el 3 por los números adecuados.

Vamos a cambiar el header ahora. Dentro del hgroup y debajo del <h2> he puesto esto:

> <div align = "right"> <?php frases()?> </div>

El frasesm es la clase que he creado para el CSS (explicado más adelante) y el frases() es la función que se ejecuta para obtener las nuevas frases.

La nueva clase CSS, tengo que decir que ha sido lo que me ha costado más ya que no estoy habituado a ello. El código:

> .provarara { position: absolute; top: 80%; left: 0; width: 100%; color: white; font: bold 24px/45px Helvetica, Sans-Serif; letter-spacing: -1px; background: rgb(0, 0, 0); background: rgba(0, 0, 0, 0.7); padding: 0px; padding: 0 2px; background: none; }

Decir que todo es cambiable y no lo voy a explicar todo, básicamente he ido probando cosas para adaptarlo. Aun estoy probando así que puede ser que cuando leas esto el código sea otro.

Creo que con esta modificación y algunos plugins que le añadiré doy mi blog por tuneado durante una temporadilla.

_Fuentes: [http://forobeta.com/wordpress/28315-poner-frases-rotatorias-header.html](http://forobeta.com/wordpress/28315-poner-frases-rotatorias-header.html) y [http://www.cssblog.es/ejemplos/bloques-texto-imagen/ejemplo\_bloque\_texto\_imagen.html](http://www.cssblog.es/ejemplos/bloques-texto-imagen/ejemplo_bloque_texto_imagen.html)_

PD: Finalmente no he modificado demasiado. Aunque espero que os sirva ;)
