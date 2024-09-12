---
title: "Como vincular los artículos de tu blog a Google+?"
date: "2012-05-09"
categories: 
  - "seo"
tags: 
  - "authorship"
  - "google-plus"
  - "google"
  - "rich-snippet"
  - "serps"
---

Hace ya un tiempo Google incluyó esta modificación en la visualización de las SERPs. Al vincular los artículos de tu sitio con tu cuenta en Google+ lo que haces es brindarle la posibilidad a Google para que muestre tu imagen de perfil de g+ al lado de tu snippet en las SERPs.

Personalmente esto me gusta bastante ya que refuerza la marca personal además de ayudar al usuario a recordar si los artículos de dicha persona le suelen gustar o no. Pero vamos al grano:

Primero tenemos que enlazar el sitio que queremos que nos salga el rich snippet desde nuestro perfil de Google+. Para hacerlo iremos al apartado “Sobre mi” de nuestro perfil y lo editaremos. Podemos enlazar más de un sitio, siempre y cuando sigamos el mismo proceso para todos.

Ahora hay dos formas de que salga tu foto en el snippet.

1) Poniendo el código en cada página:

Dentro de este apartados hay dos opciones:

- Podemos usar _<a href=”http://tuPerfilAgooglePlus.com/algo?rel=author”> Google+</a>_ No olvidemos poner el ?rel=author en el link y en el anchor poner Google+ (si con el símbolo +).
- Este caso es lo mismo pero el author es pasado como atributo del enlace. Poniendo _<a href=”http://tuPerfilAgooglePlus.com” rel=”author”> Tu Nombre </a>_

2) La otra forma de poner el rich snippet de Authorship es poniendo el código en la página  que hayas escrito, exceptuando la home y páginas que por si solas carezcan de contenido. Primero pondremos _<a href=”http://laUurlDeAboutMeDeTuSitio” rel=”author”>Tu Nombre</a>_ en cada página de tu sitio para hacerlo es mejor que modifiques el tema del blog. Ahora en la página “About Me” de tu blog tendremos que poner _<a href= ”http://tuPerfilAgooglePlus.com” rel=”me”>Pon aquí lo que quieras</a>._

Esto era todo! Fácil eh! ;)

_**Bonus:** Podemos comprobar como ha quedado usando este [verificador](http://www.google.com/webmasters/tools/richsnippets) que nos indicará si lo hemos hecho bien y nos mostrará como queda._

Para mas información podemos ir al [support de google](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=1229920)
