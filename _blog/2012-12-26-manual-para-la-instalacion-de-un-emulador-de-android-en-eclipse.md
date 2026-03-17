---
title: "Manual para la instalación de un emulador de Android en Eclipse"
date: "2012-12-26"
categories: 
  - "gnulinux"
  - "manual"
  - "programacion"
tags: 
  - "android"
  - "aplicaciones"
  - "desarrollo"
  - "eclipse"
  - "emulador"
  - "manual-2"
---

Este manual nos va a servir para crear un **emulador de Android** en nuestro entorno de desarrollo Eclipse para no tener que estar comprobando todo el rato en el dispositivo. Ese se podría decir que es la continuación de la [preparación de nuestro entorno de desarrollo eclipse para Android](http://rocreguant.com/configurar-eclipse-para-programar-para-android/373/ "Configurar eclipse para programar para Android").

1. Iniciamos Eclipse, y vamos a **Window > AVD Manager** Si no te muestra esta opción puedes ir a window > costumize prespective. Luego ya dentro podrás encontrar en la pestaña "Command groups availability" la opción para marcar un check box de Android SDK and AVD Manager, marcas el check box guardas y ya te saldrá la opción anterior en el menú.
    

1. Le damos al botón de New y se nos va a abrir otra ventana de diálogo.
    
2. En la nueva ventana de diálogo al nombre le ponemos el que queramos, como por ejemplo emulador y en target escogemos la versión del SO de Android que queramos usar.
    
3. Le damos a Create AVD
    
4. Cerramos el manager de Android Virtual Device
    
5. Y ya tenemos el emulador listo! :D
    

_**Bonus:** Cada vez que iniciéis el emulador os va a tardar mucho rato (minutos) en cargar, por lo que lo podéis dejar abierto y para testear pulsáis solo al “play” (al botón de run)._

_**Bonus Linuxero:** Como el emulador abierto consume más recursos de lo que nos gustaría, pero cerrarlo y abrirlo cada vez es un tostón podemos pausarlo. Nos aseguraremos que lo tenemos abierto y buscaremos el PID. Para saber el PID, haremos ps -e en la consola. Dentro del listado buscaremos dónde ponga “emulador” (o el nombre que le hayas puesto) y nos aprenderemos el número de al lado. Una vez hecho esto desde la consola pondremos “kill -STOP numero-pid-encontrado” y cuando queramos volver a testear la aplicación pondremos “kill -CONT numero-pid-encontrado”._
