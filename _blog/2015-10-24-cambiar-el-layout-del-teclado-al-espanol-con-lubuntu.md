---
title: "Cambiar el layout del teclado al español con Lubuntu"
date: "2015-10-24"
categories: 
  - "gnulinux"
tags: 
  - "autostat"
  - "keyboard-layout"
  - "layout-del-teclado"
  - "lxde"
  - "lxsession"
---

Después de una nueva instalación el teclado no me correspondía con la configuración del sistema. La primera solución que encontré para cambiar fue la siguiente aunque no nos cambia el layout de forma permanente. **Simplemente se tiene que ejecutar el comando en la consola.**

```
setxkbmap -layout "es"
```

Para conseguirlo de forma "**permanente**" he usado el Autostat que ofrece LXDE. Lo encontramos en:

_Menu inicio > Preferences > Default applications for LXSession_

En la nueva ventana vamos a la pestaña de _Autostart_ y en "_manual autostarted applications_" añadimos el comando anterior. De esta forma cada vez que Lubuntu arranque se ejecutará el comando fijando el teclado al layout español.
