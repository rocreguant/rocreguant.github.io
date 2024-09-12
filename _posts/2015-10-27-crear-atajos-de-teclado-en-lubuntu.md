---
title: "Crear atajos de teclado en Lubuntu"
date: "2015-10-27"
categories: 
  - "gnulinux"
  - "trucos"
tags: 
  - "atajo-de-teclado"
  - "hotkeys"
  - "ubuntu"
---

Como ya sabréis he reinstalado Lubuntu (es como Ubuntu pero usando la interfaz gráfica LXDE). Lo primero que hago es crear un atajo en el teclado para abrir la consola pulsando la _tecla Windows + T_.

Primero tendremos que encontrar el fichero, que en mi caso está en:

```
/home/<Nombre_de_usuario>/.config/openbox/lubuntu-rc.xml
```

Luego en la sección de <keyboard> tenemos que añadir el comando que queramos tener. En mi caso para conseguir abrir la consola con la tecla windows + T he añadido las siguientes lineas:

```
<keybind key="W-T">
      <action name="Execute">
        <command>lxterminal</command>
      </action>
    </keybind>
```

Notese que en mi caso es la letra _W_ para indicar _tecla  Windows_. Otros comandos:

_A- significa "Alt+"_ _C- significa "Ctrl+"_ _S- significa "Shift+"_ _W- significa la tecla "Windows"_

Para coger ideas de como se hacen las cosas lo que puedes hacer es mirar otros ejemplos dentro el fichero.
