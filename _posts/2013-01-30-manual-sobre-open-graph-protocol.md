---
title: "Manual sobre “Open Graph Protocol”"
date: "2013-01-30"
categories: 
  - "analitica"
  - "consejos-2"
  - "manual"
  - "programacion"
  - "social-media"
  - "trucos"
  - "usabilidad"
tags: 
  - "analitica-2"
  - "facebook"
  - "manual-2"
  - "open-graph-protocol"
  - "social-media-2"
  - "tags"
---

Hasta hace poco Facebook “escaneaba” la página y con ella extraía los elementos que consideraba más interesantes, como el título, un breve resumen del sitio, un vídeo o una imagen si existían, etc. Con “**Open Graph Protocol**” puedes definir en cualquier página web el valor los elementos del objeto que se muestra en Facebook. Lo que resumiendo sería que si pones esto el usuario al compartir (o darle like) a tu página posiblemente mostrará más información que antes.

En este link podéis encontrar un vídeo (en inglés) sobre Open Graph Protocol, explicado por uno de los ingenieros de Facebook (tiene mucho acento indio, espero que no os cueste entenderle).

Estas “metas” se ponen dentro del head de la página. En los ejemplos lo ponen justo debajo del tag <title> yo lo pondría después de las meta “normales”, aunque cada cual que lo ponga dónde más le guste.

Probablemente **las que vayas a necesitar** estén dentro de este listado:

> <meta property="og:title" content="Manual Open Graph Protocol"/> <meta property="og:url" content="http://rocreguant.com/Manual-sobre-Open-Graph-Protocol"/> <meta property="og:description"content="Brebe introducción sobre Open Graph protocol (impulsado Facebook), para implementarlo de forma simple en cualquier sitio web."/>

Luego también se puede añadir metas como imágenes o vídeos (estos ejemplos han sido sacados de la web oficial)

> <meta property="og:image" content="http://ia.media-imdb.com/rock.jpg"/> <meta property="og:video" content="http://example.com/bond/trailer.swf" />

Pero esto no termina aquí! Utiliza Open Graph Protocol para que Facebook trate tu URL como una Fanpage! (\[EN\] [fuente]( http://www.insidefacebook.com/2010/04/21/with-the-open-graph-protocol-any-url-can-be-treated-just-like-a-facebook-page/))

Esto lo puedes conseguir añadiendo una de las siguientes lineas de código.

> <meta property="fb:admins" value="USER\_ID1,USER\_ID2" /> (dónde USER\_ID2 y USER\_ID2 serian los administradores)

O bien usando:

> <meta property="fb:app\_id" value="1234567" /> (dónde value sería el ID de vuestra app en facebook)

Con esto podrás acceder a tu panel de analytics como el de las Fanpages, en el que te muestra los usuarios activos diarios, los likes, los nuevos usuarios...

Para más información podéis consultar **la web oficial de [Open Graph Protocol](http://ogp.me/)**.

_**Bonus:** Lo que se comenta en las altas esferas es que puedes usarlo para “engañar” a Facebook. Por ejemplo, tu haces un vídeo relacionado sobre el post que has escrito pero sin ponerlo como embedded. Lo pones como meta, y la gente al darle al like a la página sin vídeo comparte el vídeo. ([link black](http://www.socialmediaexaminer.com/how-to-triple-your-youtube-video-views-with-facebook/))_
