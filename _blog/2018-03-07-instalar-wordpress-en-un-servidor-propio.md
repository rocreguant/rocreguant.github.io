---
title: "Instalar Wordpress en un servidor propio"
date: "2018-03-07"
categories: 
  - "manual"
  - "wordpress-2"
tags: 
  - "instalacion"
  - "manual-2"
  - "servidor"
  - "tutorial"
  - "wordpress"
---

Como ya vimos el otro día, podemos [alojar varios sitios web en un mismo servidor](https://rocreguant.com/como-tener-varios-sitios-web-alojados-en-un-mismo-servidor/1170). En mi caso para lo que los quería era para instalar distintas instancias de Wordpress (osease distintos blogs). Pero para usar Wordpress requerimos distintas aplicaciones para las diferentes partes del sistema.

### PHP

Primero instalaremos PHP para que los scripts de Wordpress puedan ser ejecutados.

```
sudo apt-get install php apache2 libapache2-mod-php php-mcrypt php-mysql
```

### Base de datos

Ahora instalaremos la base de datos

```
sudo apt-get install mysql-server
 sudo mysql_secure_installation
 sudo mysql_install_db
```

y crearemos los usuarios para cada uno de nuestro blog. Primero nos logearemos como root para poder crear usuarios

```
mysql -u root -p
```

crearemos el usuario

```
GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost' IDENTIFIED BY 'pass';
```

Saldremos de la conexión con la base de datos con el root, y nos logearemos con el nuevo usuario

```
 mysql -u user -p
```

y crearemos una nueva base de datos para el blog

```
CREATE DATABASE db_wordpress;
```

### Scripts de Wordpress

Nos [bajaremos la última versión de Wordpress](https://es.wordpress.org/txt-download/). La descomprimiremos y la pondremos en _/var/www/directorio-de-tu-blog/._ Para terminar de [configurar el apache podéis seguir esta guía](https://rocreguant.com/como-tener-varios-sitios-web-alojados-en-un-mismo-servidor/1170).

### Finalizar

Para finalizar y que los cambios tengan efecto reiniciaremos apache

```
sudo systemctl restart apache2
 apt-cache search php- | less
```

y accederemos a la url de nuestro blog. Allí se nos pedirá que ingresemos los datos de la base de datos y otra información básica sobre el blog.
