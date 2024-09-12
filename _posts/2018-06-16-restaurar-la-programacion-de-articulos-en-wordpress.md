---
title: "Restaurar la programación de artículos en Wordpress"
date: "2018-06-16"
categories: 
  - "gnulinux"
  - "manual"
  - "wordpress-2"
tags: 
  - "articulos"
  - "blog"
  - "cronjob"
  - "posts"
  - "programacion-2"
  - "scheduler"
  - "wordpress"
---

Hace poco me fui de viaje y vi que todas las entradas programadas para mi blog fallaron. El motivo por el cual la programación de los artículos en Wordpress falla normalmente es por el uso de plugins. En especifico por el uso de plugins que cachean las páginas. Al cachear las páginas no se ejecuta el cron de Wordpress y si no se ejecuta el cron entonces Wordpress no publica los artículos programados.

Como no quiero perder toda la velocidad de carga que obtengo cacheando las páginas de mi blog he encontrado un método para arreglar el problema sin tener que desinstalar ningún plugin. Puedes instalar OTRO plugin para solucionar el problema o añadir un cronjob. **En este artículo voy a explicar como arreglar la programación perdida de los artículos añadiendo un cronjob.**

Hay hostings que puedes añadir el cronjob usando el panel de control (lo vas a tener que buscar tu en la pagina de ayuda de tu hosting) o si tienes control entero sobre tu servidor vas a poder [añadir el conjob tu mismo](https://rocreguant.com/como-ejecutar-una-tarea-periodicamente-en-ubuntu-linux/872). Básicamente se trata de ejecutar periódicamente el siguiente link

```
http://tudominio.com/wp-cron.php?doing_wp_cron
```

En condiciones normales este link se carga cada vez que un usuario entra en el blog pero si usamos cache la página no se carga y perdemos las publicaciones. Para poder publicar las entradas programadas y mantener nuestra cache tendremos que ejecutar este link de modo automático gracias al cronjob.

Un cronjob requiere de un comando (no de un link). Así que lo que he escrito un comando para que el link sea cargado sin guardar el HTML en ningún sitio:

```
wget -O /dev/null http://tudominio.com/wp-cron.php?doing_wp_cron
```

Personalmente lo he puesto cada hora, pero lo puedes poner cada 5minutos. No usa casi recursos así que difícilmente vas a sobrecargar el blog.

Recuerda que la primera vez que accedas al link después de los errores de programación, todas las entradas falladas se van a publicar a la vez. Consecuentemente es interesante que revises la programación de los posts antes de acceder al link.
