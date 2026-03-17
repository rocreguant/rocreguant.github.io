---
title: "Instalar MongoDB en Ubuntu"
date: "2015-01-13"
categories: 
  - "big-data"
  - "gnulinux"
  - "manual"
tags: 
  - "base-de-datos"
  - "gnulinux-2"
  - "instalacion"
  - "mongobd"
  - "no-relacional"
  - "nosql"
  - "ubuntu"
---

Uno de los propósitos de año nuevo, [como ya visteis](http://rocreguant.com/propositos-para-el-2015/719/), ya me he puesto manos a la obra en aprender MongoDB. Para esto necesito tenerlo instalado en el ordenador (con SO Ubuntu) para poder trastear. Así que al turrón!

Primero de todo MongoDB nos recomienda importar la “public key” usada por el gestor de paquetes.

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
```

Luego crearemos una lista en un fichero para MongoDB

```
echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | sudo tee /etc/apt/sources.list.d/mongodb.list
```

Seguidamente actualizaremos la base local de paquetes con:

```
sudo apt-get update
```

Finalmente instalaremos la última versión estable de MongoDB

```
sudo apt-get install -y mongodb-org
```

Y así se instala MongoDB en nuestro ordenador local con Ubuntu! :)

Para iniciar MongoDB tendremos que ejecutar en la consola “mongod”. Pero para acceder a la consola y poder ejecutar queries en la base de datos tendremos que usar el comando “mongo”.

_**Bonus:** Para los curiosos, la versión de 32bits permite un límite teórico de 4,3GB de datos (2^32). Teniendo en cuenta padding, espacios vacíos y otras ineficiencias la empresa estima que el espacio disponible para datos es de entre 2GB y 4GB._
