---
title: "Como mejorar nuestra página web para que cargue más rápido"
date: "2012-05-16"
categories: 
  - "seo"
  - "trucos"
  - "web-performance-optimization"
tags: 
  - "cache"
  - "gzip"
  - "optimizacion"
  - "rendimiento"
  - "web-performance-optimisation"
  - "wpo"
---

El motivo principal para deberíamos plantearnos que nuestro sitio cargue más rápido es que mejora la experiencia del usuario haciendo así que se incrementen las ventas. A parte de engrosar nuestro orgullo :P

Nunca mejor dicho el tiempo es oro. Vamos a tratar los factores que influyen en el rendimiento de nuestro sitio web. Pues manos a la obra!

## 1- Reduce el número de peticiones HTTP

Las peticiones HTTP posiblemente sea lo que haga que tarde más en cargar un sitio. Cada petición es un request y answer, o lo que vendría a ser se envía información al servidor y este envía otra de vuelta. Como más veces lo hagamos más va a tardar. Lógico. He leído que el botoncito de “me gusta” de Facebook hace 30 peticiones así por vena, lo cual es bastante malo para el rendimiento. Así que el consejo es pon los mínimos botones sociales. Pero tranquilos! Tengo algunos tips para reducir peticiones.

- Poner todos los CSS en un fichero. Pero si hay algunas páginas de nuestra web que usan ficheros CSS muy grandes y son apenas visitadas podemos poner este CSS separado.
    

- Cargar los Javascript de forma asíncrona evitando así que sólo se cargue el Javascript.
    
- Utilizar sprites. De esta forma combinamos diversas imágenes en una sola evitando conexiones innecesarias.
    

## 2- Utiliza la caché

Ahora está de moda usar todas las caches posibles, y la verdad es que mola, pero también es interesante no tener un código, consultas a las BD y servidores horrendos. Usando Expires Header podemos indicar al navegador hasta cuando su versión de la página es válida.

Evita poner los ficheros CSS y Javascript dentro del código de la página, ya que estos pueden ser cacheados por le navegador y la segunda vez que se acceda a la página no volverán a ser cargados.

## 3-Comprime los ficheros usando Gzip

He dicho Gzip porque no lo hace nada mal, es gratuito y además los navegadores más usados lo soportan. Pero amigos, NO lo comprimamos todo! La mayoría de imágenes ya deberían estar optimizadas, por lo que comprimirlas pasaría a ser una sobrecarga inútil para el servidor además de que el tamaño de la imagen podría aumentar. Por lo que por regla general comprimiremos solamente los ficheros HTML, CSS y scripts como Javascript.

## 4-Minimiza los ficheros

Con esto me refiero a que a los documentos HTML, Javascript, CSS... quites los espacios en blanco, comentarios, saltos de linea, tabulaciones... Todo esto son caracteres que se envían a través de la red pero no sirve de nada y ocupa un ancho de banda precioso.

## 5-Evita las redirecciones

Las redirecciones tienen un tiempo de carga considerable, por lo que debemos intentar evitarlas siempre que sea posible. Sé que las redirecciones solucionan muchos problemas, pero es mejor no ponerlas. El problema radica en que primero se conecta a la página que redirige y luego se conecta a la página que toca, y esto es un tiempo muy valioso. No hace falta decir que encadenar redirecciones es ya mortal...

## 6-Otros consejos

- Supongo que no hace falta decir que tengamos en cuenta de no poner scripts duplicados ya que por un despiste nos puede salir caro.
- Poner los CSS para importarlos en el header. Aunque esto no mejora el rendimiento en si mismo si que da la impresión de que carga más rápido. Eso es debido a que los navegadores no muestran la página hasta que haya cargado el CSS por lo tanto cuanto antes lo cargue antes la mostrará.
- Es recomendable poner los scripts después del body ya que al cargar los scripts no se carga nada más y además impide el renderizado de la página.

Finalmente y para terminar debemos tener en cuenta que no todas las mediciones usando la misma herramienta pueden dar las mismas mediciones. Esto es debido a que el servidor nuestro puede tener más o menos tráfico o también puede deberse a que el lugar del servidor de la herramienta puede estar situado en otro país distinto a la última vez.

Pero recuerda que no todo se basa en el rendimiento, no debemos empobrecer la expericencia de usuario quitando botones sociales o haciendo una web en texto plano, debemos encontrar el termino medio entre rendimiento y funcionalidades.
