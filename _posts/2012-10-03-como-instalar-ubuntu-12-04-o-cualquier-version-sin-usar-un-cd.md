---
title: "Como instalar Ubuntu 12.04 o cualquier versión sin usar un CD"
date: "2012-10-03"
categories: 
  - "gnulinux"
  - "manual"
tags: 
  - "instalacion"
  - "manual-2"
  - "no-cd"
  - "tutorial"
  - "ubuntu"
  - "ubuntu-12-04"
---

Instalar la última versión de Ubuntu sin utilizar un CD es realmente muy simple. Para empezar nos [descargaremos la última versión de Ubuntu](http://www.ubuntu.com/download/desktop) (en mi caso es la versión 12.04, pero sirve para todos).

Ahora mientras se baja, busca tu memoria USB. Una vez encontrada nos bajaremos el adaptador de Ubuntu al USB, el programa que usaremos es [Universal-USB-Installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/).

Una vez descargado todo abriremos el Universal-USB-Installer, en éste rellenaremos los campos la versión, la unidad y el directorio dónde se encuentra el iso de Ubuntu.

Una vez hecho esto le damos a crear, este paso nos avisará que se va a borrar todos los datos de la memoria y se nos cambiará el nombre del USB.

Para finalizar tendremos que cambiar la secuencia de arranque del ordenador. Para esto cuando iniciamos el ordenador siempre nos dice algo parecido a: “Press TECLA to enter for Setup”. Una vez en el setup deberemos hacer y ponemos el USB antes del disco duro, o el USB como “fist boot device”. Guardamos los cambios y salimos.

Ahora cuando se nos inicie, si tenemos conectado el USB, nos saldrá ya la pantalla de instalación de Ubuntu como si fuera un CD.

Espero que os haya servido! :) Yo al final descubrí que se puede instalar también en Windows, lo pone debajo dónde pulsas para descargar la iso.
