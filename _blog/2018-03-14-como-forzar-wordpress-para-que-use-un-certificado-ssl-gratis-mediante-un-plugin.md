---
title: "Cómo forzar Wordpress para que use un certificado SSL gratis mediante un plugin"
date: "2018-03-14"
categories: 
  - "manual"
  - "seguridad-informatica"
  - "wordpress-2"
tags: 
  - "manual-2"
  - "seguridad-informatica"
  - "ssl"
  - "tutorial"
  - "wordpress"
---

En los posts anteriores hemos [instalado Wordpress](https://rocreguant.com/instalar-wordpress-en-un-servidor-propio/1173) y hemos [alojado varios sitios en un mismo servidor](https://rocreguant.com/como-tener-varios-sitios-web-alojados-en-un-mismo-servidor/1170). En este post lo que haremos será mejorar la seguridad de nuestro blog y las SERPs en Google. Hace ya un tiempo Google recomendó a los webmasters dejar de usar http y pasar a https para hacer la web más segura. Para forzar un poco el brazo [Google ofreció mejoras en los rankings a aquellas webs que usaran un certificado SSL](https://webmasters.googleblog.com/2014/08/https-as-ranking-signal.html). Como no es fácil para todos los bloggers comprar un certificado SSL lo que propongo es obtener gratuitamente un certificado de SSL gracias a cloudflare y así poder ofrecer nuestro blog de forma más segura para los usuarios.  Para conseguirlo solo tenemos que seguir los siguientes pasos.

### Instalar el plugin para el certificado SSL en wordpress

Para instalar el plugin Wordpress podemos ir al apartado de plugins y buscar "[_WordPress HTTPS_](https://wordpress.org/plugins/wordpress-https/)" e instalarlo usando el panel de control. También podemos instalarlo manualmente mediante FTP, subiéndolo directamente a la carpeta de _/wp-content/plugins/_ e instalándolo como cualquier otro complemento. Una vez instalado lo activaremos.

### Conseguir el certificado SSL gratis

La mayoría de certificados son de pago pero [cloud cloudflare fare nos permite usar un certificado SSL gratis](https://www.cloudflare.com/ssl/) para proyectos más modestos. Lo único que tenemos que hacer es registrarnos y añadir la página web cuando nos la pidan. Finalmente cambiaremos los name servers en nuestro registrador de dominios.

### Actualizar los ficheros de configuración de Wordpress

Finalmente iremos a ajustes generales en la sección de ajustes de nuestro blog wordpress y cambiaremos http por https dejando el resto de la url intacta. Por algún motivo que desconozco he tenido que cambiar el fichero _wp-config.php_. Justo antes de _/\* That's all, stop editing! Happy blogging. \*/_ he tenido que añadir

```
define('FORCE_SSL_ADMIN', false);
```

para poder acceder al wp-admin.

Espero que esto os haya servido para mejorar la seguridad del blog y los rankings de las SERPs.
