---
title: "Arreglar las teclas de funciones para cambiar el brillo del portátil con Lubuntu"
date: "2015-10-30"
categories: 
  - "gnulinux"
tags: 
  - "brillo"
  - "grub"
  - "lubuntu"
  - "teclas-de-funciones"
---

Como ya habrás notado en los últmos posts, tras la reinstalación de Lubuntu algunas he reconfigurado algunas cosas de mi ordenador. Una de estas ha sido arreglar las teclas de funciones para cambiar el brillo de la pantalla del portátil des del teclado.

La primera solución que encontré y que no funciona des del teclado es creando un bash script con la siguiente linea:

```
echo X > /sys/class/backlight/intel_backlight/brightness
```

Dónde _X_ es el valor del brillo. Cada vez que quería cambiar el brillo tenia que ejecutar el fichero desde la consola cambiando la _X_ por un numero del 1 al 4000.

La solución que me ha arreglado las teclas de funciones de forma permanente permitiéndome modificar la intensidad de brillo de la pantalla ha sido la siguiente. Primero de todo ejecutamos el siguiente comando en la terminal:

```
sudo gedit /etc/default/grub
```

Luego cambiamos

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

por

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
```

guardamos los cambios y ejecutamos la siguiente linea en la terminal

```
sudo update-grub
```

Sinceramente no entiendo muy bien el porqué de las lineas anteriores, pero la conclusión es que funciona :D
