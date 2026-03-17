---
title: "Arreglando el wifi después de actualizar a Lubuntu 14.04 LTS"
date: "2015-04-22"
categories: 
  - "gnulinux"
---

Como ya comenté el otro día la actualización de Lubuntu 14.04 me rompió algunas configuraciones. A parte del teclado me rompió la recepción del señal de wifi. Me hizo desaparecer el gestor de la red (_Network Manager_).

Para hacerlo funcionar manualmente debemos usar el siguiente comando en la consola:

```
nm-applet
```

Pero para solucionarlo de forma permanente tendremos que ir al menú de Lubuntu luego preferencias y la opción de “_Aplicationes por defecto para LXSession_” (_Default applications for LXSession__)._ Una vez allí debereis escoger la pestaña _Autostart_ y luego debajo de “_aplicaciones manuales en autostart_” (_Manual autostarted applications_) escribir "_nm-applet_" y darle al botón de “_\+_ _añadir_” a su derecha. Para variar podéis reiniciar para ver que tiene efecto.
