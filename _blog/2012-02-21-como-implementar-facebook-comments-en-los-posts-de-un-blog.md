---
title: "Como implementar Facebook comments en los posts de un blog"
date: "2012-02-21"
categories: 
  - "manual"
  - "wordpress-2"
tags: 
  - "comentarios"
  - "facebook"
  - "how-to"
  - "manual-2"
  - "tutorial"
  - "wordpress"
---

Para poder poner comentarios en tu blog WordPress puedes usar el [plugin](http://wordpress.org/extend/plugins/facebook-comments-for-wordpress/ "Facebook Comments Wordpress Plugin") o hacerlo a mano. Aquí lo vamos a hacer a mano para evitar que nuestro WordPress se sobrecargue demasiado de plugins.

Para empezar nos vamos a hacer [Facebook developers](https://developers.facebook.com/apps/ "Facebook Developers"). Le tenemos que dar permisos a la aplicación (si no lo habíamos hecho ya). Seguidamente creamos una nueva app, a la que le decimos que será para un sitio web. Rellenamos los nombres que le queremos poner a la “aplicación” y aceptamos. Si es la primera vez posiblemente nos pida que necesita un número de móvil, a mi experiencia solo envía los sms para la confirmación a los usuarios de movistar, pero no lo puedo asegurar. Por lo menos creo que eso es lo que me ha pasado a mi, estoy usando Yoigo y no me ha enviado ningún sms, pero cuando he probado con un número de Movistar lo ha hecho al momento.

Editando los datos de la aplicación he intentado varias veces poner la url del blog pero no lo he conseguido, así que lo he dejado en blanco y Facebook no se ha quejado.

Ahora toca ir a nuestro sitio para editar un poco el template y insertando el código necesario para que salga Facebook comments.

Empezaremos con el header.php, allí insertaremos la siguiente línea de código cambiando _YOUR\_APPLICATION\_ID_ por el número de aplicación que nos ha facilitado Facebook para esta app en concreto. Este código sirve para juntar los comentarios de tu blog con la aplicación de Facebook.

```
<meta property="fb:app_id" content="{YOUR_APPLICATION_ID}">
```

Ahora modificaremos el archivo comments.php (puedes ponerlo dónde quieras) insertaremos el siguiente código:

```
<div id="fb-root"></div><script src="http://connect.facebook.net
/es_CO/all.js#xfbml=1"></script>
<fb:comments href="<?php the_permalink() ?>" width="687">
</fb:comments ></div>
```

Posiblemente tengas que modificar el campo width para adaptarlo mejor al ancho del que disponemos.

Yo he decidido poner el código justo debajo del post y antes de los comentarios “habituales” del blog.

**Aclaración:** Hay que tener en cuenta que estos comentarios se los “queda” Facebook, no pasan a formar parte de nuestra base de datos. El día que decida dejar de respaldar esta funcionalidad o cobrar por ella lo vamos a sufrir. Lo gratis se cobra de distintos modos, en este caso con información de los comentarios de nuestro blog.
