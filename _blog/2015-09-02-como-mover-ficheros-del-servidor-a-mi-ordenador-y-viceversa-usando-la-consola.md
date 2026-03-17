---
title: "Como mover ficheros del servidor a mi ordenador y viceversa usando la consola"
date: "2015-09-02"
categories: 
  - "gnulinux"
  - "hacks-personales"
  - "manual"
tags: 
  - "ficheros"
  - "loca"
  - "servidor"
  - "sshf"
  - "transferencia"
---

Como ya comenté en [mi anterior post](http://rocreguant.com/como-usar-rtorrent-des-de-cero/925/) conseguí un server y uno de los problemas que tuve fue mover ficheros de un lado para otro (del servidor a mi ordenador loca y al revés). Buscaba algo que pudiera usarse a través de la consola sin tener que usar otros programas (i.e. FTP, esciptorios remotos, etc.). Finalmente encontré una solución curiosa pero muy buena. Se trata de usar sshfs.

Si no lo tienes instalado (probablemente no)

```
sudo apt-get install sshfs
```

Ahora crea un directorio en tu maquina local dónde quieras enlazar el el directorio del servidor. Para enlazar los dos directorios usa el siguiente comando:

```
sshfs user@server.com:/remote/dir /home/user/test
```

Con el enlace montado puedes usar tu GUI local o lo que quieras para mover los archivos que desees. Una vez hayas terminado usa el siguiente comando para terminar el enlace.

```
fusermount -u /home/youruser/remotecomp
```

(si no te acuerdas del directorio que usaste, pulsando tab puedes ver los que tienes abiertos)

_**Bonus:** [Idea original](http://unix.stackexchange.com/questions/106480/how-to-copy-files-from-one-machine-to-another-using-ssh) junto con otras ideas para conseguir tal meta._
