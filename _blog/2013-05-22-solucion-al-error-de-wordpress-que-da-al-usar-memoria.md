---
title: "Solución al error de Wordpress que da al usar memoria"
date: "2013-05-22"
categories: 
  - "wordpress-2"
tags: 
  - "000webhost"
  - "error"
  - "manual-2"
  - "memoria"
  - "solucion"
  - "wordpress"
---

El otro día felizmente intenté entrar en el panel de control de **Wordpress** para moderar comentarios y añadir un nuevo post y me encontré con este error:

> **Fatal error**: Allowed memory size of 67108864 bytes exhausted (tried to allocate 71 bytes) in /public\_html/wp-includes/capabilities.php on line 1211>

No sé si es culpa mi hosting **000webhost**, o que pero he estado buscando la solución y ha resultado ser que tenía que colocar la siguiente linea en **wp-settings.php** (dentro del directorio principal).

_define('WP\_MEMORY\_LIMIT', '96M');_

Normalmente las definiciones se colocan al inicio del código, ya verás otros defines.

PD: Para "colocar" la línea tal y como indico arriba lo que se tiene que hacer es editar el fichero con un editor de texto como bloc de notas, wordpad, notepad+, gedit, vim... y guardarlo.

_**Bonus:** No sé porqué pero la mayoría recomendaba poner el limite de memoria en 64 (el cual a mi no me funcionaba así que lo he colocado a 96._
