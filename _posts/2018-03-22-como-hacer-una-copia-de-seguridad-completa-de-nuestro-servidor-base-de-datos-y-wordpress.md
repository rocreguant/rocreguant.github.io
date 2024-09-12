---
title: "Como hacer una copia de seguridad completa de nuestro servidor, base de datos y Wordpress"
date: "2018-03-22"
categories: 
  - "gnulinux"
  - "manual"
  - "seguridad-informatica"
  - "wordpress-2"
tags: 
  - "backup"
  - "blog"
  - "copia-de-seguridad"
  - "cronjob"
  - "ftp"
  - "manual-2"
  - "tar"
  - "tutorial"
  - "wordpress"
---

Los backups son necesarios para cualquier sistema para prevenir la pérdida de datos. Siguiendo un poquito con la tónica de los últimos posts, [instalar wordpress en un servidor propio](https://rocreguant.com/instalar-wordpress-en-un-servidor-propio/1173) y [usar certificados SSL para nuestro Wordpress](http://como-forzar-wordpress-para-que-use-un-certificado-ssl-gratis-mediante-un-plugin/1177), esta vez lo que haremos será un **backup completo de nuestro Wordpress**. En este post lo que hago es crear un cronjob, osease un script que se ejecute a diario y haga una copia completa de nuestra base de datos juntamente con distintas carpetas que queramos conservar de nuestro blog.

### Generamos un dump de todas las bases de datos

La base de datos es uno de los componentes más importantes de cualquier sistema. Es donde históricamente se ha guardado la información. Para hacer una copia de la base de datos necesitaremos _mysqldump_. Esto nos permitirá sacar una copia consistente de la base de datos.  Para obtener la copia de todas las bases de datos ejecutaremos el comando

```
mysqldump -u[usuario] -p[contraseña] --single-transaction --quick --all-databases > output.sql
```

El fichero output.sql contendrá toda la información en la base de datos.

### Agruparemos todos los directorios y documentos en un solo archivo

Una vez ya tengamos generado el dump de nuestra base de datos lo que tendremos que hacer es crear un archivo único para mejorar la transportabilidad del backup. En mi caso también lo comprimo usando gzip para ahorrar espacio, ya que raramente se consultan/usan los backups y así ahorro espacio. En mi caso he usado _tar_ (para una introducción podéis leer _[mi anterior post a tar](https://rocreguant.com/manual-del-comando-tar-en-gnulinux/216))_ para mantener los permisos de cada archivo.

```
tar cfz /home/donde/quieras/archivo.tar.gz /var/www/ /directorio/hacia/backup/output.sql
```

En el comando anterior vemos que hemos creado un archivo comprimido que contiene el directorio _var/www_, y el dump que hemos hecho de la base de datos _/directorio/hacia/backup/output.sql_

### Subiremos el archivo comprimido a un servidor externo

Para asegurarnos que cualquier problema que pueda tener nuestra máquina no afecte a nuestros backups subiremos el archivo comprimido a un servidor externo. Imagínate que haces sólo los backups pero los dejas en tu ordenador y el disco duro se estropea. Si pasa eso no podrías recuperar la información. Por esto es importante guardar copias de seguridad en distintos sitios.

Para este apartado he creado como un mini-script con las instrucciones para que el cliente FTP lo ejecute y haga la copia. En mi caso lo voy a guardar con el nombre _ftp.txt_

```
open [url o IP]
user usuario contraseña
passive #algunas veces requerido
put /home/donde/tenías_el/archivo.tar.gz nombre_del_archvo_en_el_ftp.tar.gz
bye
```

Finalmente ejecutaremos este trozo de código con

```
 ftp -n < ftp.txt
```

### Asignaremos un cronjob que haga backups y los salvaguarde

A partir de la segunda vez que tienes que realizar una tarea uno tiene que empezar a pensar de que modo puede optimizar el proceso. Lo que he decidido hacer es [crear un cronjob](https://rocreguant.com/como-ejecutar-una-tarea-periodicamente-en-ubuntu-linux/872) para que haga una copia de seguridad a diario y la suba al servidor externo mediante FTP.

```
echo "Starting script: $(date)"
day=$(date +"%d")

echo "Doing the mysql dump of all tables"
mysqldump -u[usuario] -p[contraseña] --single-transaction --quick --all-databases > output.sql

echo "Compressing the websites and the mysql dump into one file"
tar cfz /home/donde/quieras/archivo.tar.gz /var/www/ /directorio/hacia/backup/output.sql

echo "open url o IP 
user usuario contraseña 
passive #algunas veces requerido 
put /home/donde/tenías_el/archivo.tar.gz nombre_del_archvo_en_el_ftp.tar.gz 
bye" > ftp.txt

echo "Executing FTP and uploading the file"
ftp -n < ftp.txt

rm ftp.txt
```

Este vendría a ser el script que va a ejecutar el cronjob. Pero para ejecutar el script de forma automática tendremos que guardarlo propiamente como cronjob. Para esto usaremos el siguiente comando para editar los cronjobs de nuestro sistema.

```
crontab -e
```

y dentro del fichero, al final, escribiremos el siguiente comando

```
00 4 * * * sh /camino/hacia/cronjobs/cron_backup.txt > /dev/null 2>&1
```

Este comando ejecuta el script en _/camino/hacia/cronjobs/cron\_backup.txt_ cada día (los asteriscos) a las _4:00_ (am) sin guardar el output (_\> /dev/null 2>&1_). Ahora guardaremos el fichero y ya lo tendremos inicializado.

Para [aprender un poquito más sobre los cronjobs](https://rocreguant.com/como-ejecutar-una-tarea-periodicamente-en-ubuntu-linux/872) podéis leer mi entrada anterior dónde lo explico más detalladamente.

### Finalmente para recuperar los archivos

Cuando lo más temido pasa, cuando se nos estropea el ordenador y tenemos que ir a buscar los backups, lo tendremos todo preparado.

Primero nos logearemos con el cliente FTP y nos descargaremos el archivo con los backups.

```
ftp [url o IP]
```

pondremos el nombre de usuario y contraseña cuando nos lo pida. Una vez logueados descargaremos el fichero con el backup en nuestro ordenador local

```
get Nombre_del_backup.tar.gz
```

Saldremos de la sesión para descomprimir y extraer los archivos

```
tar xf Nombre_del_backup.tar.gz
```

Todo lo que sea blogs Wordpress tendremos que copiar los ficheros en _/var/ww/_ otra vez y volver a configurar el apache. En cuanto la base de datos tendremos que importar el dump

```
mysql -u[usuario] -p output.sql
```

Y de este modo ya habremos recuperado todo lo que temíamos haber perdido.
