---
title: "Como tener varios sitios web alojados en un mismo servidor"
date: "2018-04-22"
categories: 
  - "wordpress-2"
tags: 
  - "hosting"
  - "wordpress"
---

Recientemente cambié este blog de una maquina virtual a una maquina física pasando de compartir maquina a tener una para mi solito. Con el cambio quise tener alojados todos mis blogs en el mismo servidor para simplificar tareas y resultó ser más fácil de lo que pensaba.

Primero instalamos apache

```
sudo apt-get install apache2
```

Luego creamos los directorios para nuestros blogs

```
sudo mkdir -p /var/www/miblog1.com/blog/
sudo mkdir -p /var/www/miblog2.com/blog/
```

y cambiamos los permisos

```
sudo chown -R www-data /var/www/
```

Creamos una landing page para cada uno

```
sudo vim /var/www/miblog1 .com/html/index.html
sudo vim /var/www/miblog2.com/html/index.html
```

creamos unos archivos de configuración

```
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/miblog1.com.conf
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/miblog2.com.conf
```

y los editamos (solo pongo uno aquí pero tiene que ser para todos los sitios)

```
sudo vim /etc/apache2/sites-available/miblog1.com.conf
```

Modificamos y añadimos las siguientes lineas

```
ServerAdmin me@miblog1.com
ServerName miblog1.com
ServerAlias www.miblog1.com
DocumentRoot /var/www/miblog1.com/blog
<Directory /var/www> 
     Options FollowSymLinks
     AllowOverride All
</Directory>
```

Activamos los sitios usando los comandos

```
sudo a2ensite miblog1.com.conf
sudo a2ensite miblog2.com.conf
```

reiniciamos apache para que los cambios tengan efecto

```
sudo service apache2 restart
```

Comprueba que funciona a través de la IP y añade los A recods a tu dominio para que se pueda acceder usando la url.
