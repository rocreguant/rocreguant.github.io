---
title: "Como trakear las arañas de los buscadores usando Google Analytics en Wordpress"
date: "2011-09-02"
categories: 
  - "analitica"
  - "manual"
  - "seo"
  - "trucos"
tags: 
  - "analitica-2"
  - "bots"
  - "buscadores"
  - "google-analytics"
  - "manual-2"
  - "spiders"
  - "wordpress"
---

Ser capaz de trakear lo que las arañas de los buscadores están rastreando en tu página web te puede ayudar a obtener mas información útil sobre tu sitio. En muchos casos no podemos ver como las spiders interactúan con nuestro site ya que el código está en Javascript nos perdemos mucha cantidad de información. Pero ahora he encontrado un modo de poder ver lo que hacen las arañas en nuestro sitio y además mostrarlo de un modo visual bonito.

Lo que he encontrado ha sido un plugin de Wordpress WP Bots Analytics [http://wordpress.org/extend/plugins/wp-bots-analytics/](http://wordpress.org/extend/plugins/wp-bots-analytics/) sacado de la web [http://www.stayonsearch.com/tracking-search-engine-bots-with-google-analytics-on-wordpress](http://www.stayonsearch.com/tracking-search-engine-bots-with-google-analytics-on-wordpress?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+stayonsearch+%28StayOnSearch%29) (inglés) y que a su vez ha obtenido la idea de aquí _http://www.web-analytics.fr/google-analytics-seo-comment-mesurer-les-vistes-des-robots-et-crawlers-sur-votre-site/ (francés)._ _<-{__Ya no funciona}_

Para hacer que funcione el plugin tienes que:

1. Crear un nuevo perfil poniendo la url que quieras por ejemplo robots.sitio.com y anotar el ID de propiedad web.
2. Luego tienes que ir al sitio al cual has instalado el plugin y buscar la cookie del sitio que tenga de nombre \_\_utma y luego escoges los primeros números antes que el punto. Ver imagen.
    

\[caption id="attachment\_84" align="aligncenter" width="300"\][![Cokie Editor](images/cookies11-300x174.jpg "cookies1")](http://rocreguant.com/wp-content/uploads/2011/09/cookies11.jpg) Cokie Editor\[/caption\]

Para esto yo he usado el plugin para Firefox Edit Cookies.

1. Con ambos números nos vamos a Ajustes en administración de nuestro blog, y allí escogeremos WP Bots Analytics dónde pondremos ambos números y guardaremos.

Ahora solo nos queda esperar que analytics vaya recogiendo los datos. Pero que hacemos con esos datos?

- Podemos saber cuales son las paginas de mas interés para los buscadores y mejorarlas.

- Potenciar las páginas menos atractivas para conseguir que tengan mas peso.

- Ver que bots nos gastan mucho ancho de banda y quizás bloquearlos.

- Ver si las arañas acceden a páginas restringidas, ver porque no siguen nuestras restricciones y reparar el robots o introducir código html en la página que haga el hecho.

- También puede suceder al revés, páginas que queremos que sean indexadas y concurridas pero que no sea así y conseguí algunos enlaces o revisar la accesibilidad.

¿Se os ocurre algo más que se pueda hacer con esta información?
