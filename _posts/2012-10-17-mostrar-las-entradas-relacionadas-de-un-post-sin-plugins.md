---
title: "Mostrar las entradas relacionadas de un post sin plugins"
date: "2012-10-17"
categories: 
  - "manual"
  - "programacion"
  - "trucos"
  - "wordpress-2"
tags: 
  - "entradas-relacionadas"
  - "manual-2"
  - "programar"
  - "sin-plugins"
  - "tutorial"
  - "worpdress"
---

Como ya sabréis los plugins relentece el rendimiento de Wordpress, por eso cuantos más evitemos instalar mejor. Para esto voy a intentar realizar una saga para insertar algunos plugins en el mismo código de Wordpress. Así que este primero se trata de mostrar las entradas relacionadas de un post sin la necesidad de plugins.

Para empezaremos accederemos al fichero functions.php y añadiremos este código:

 

> function getRelatedPosts ($post\_id){
> 
> $taxs = wp\_get\_post\_tags( $post\_id );
> 
> if ( $taxs ) {
> 
> $tax\_ids = array();
> 
> foreach( $taxs as $individual\_tax ) $tax\_ids\[\] = $individual\_tax->term\_id;
> 
>  
> 
> $args = array(
> 
> 'tag\_\_in' => $tax\_ids,
> 
> 'post\_\_not\_in' => array( $post->ID ),
> 
> 'showposts' => 5,
> 
> 'ignore\_sticky\_posts' => 1
> 
> );
> 
>  
> 
> $my\_query = new wp\_query( $args );
> 
>  
> 
> if( $my\_query->have\_posts() ) {
> 
> while ($my\_query->have\_posts()) : $my\_query->the\_post();
> 
> ?><h3><a href=" <?php the\_permalink();?> " rel="bookmark" title=" <?php the\_title(); ?> "> <?php the\_title() ?></a></h3> <?php
> 
> endwhile;
> 
> } else {
> 
> echo "<h2>No related posts found!</h2>";
> 
> }
> 
> }
> 
> $post = $backup;
> 
> wp\_reset\_query();
> 
> }

Éste código lo que hace es relacionar tags y mostrar los 5 posts que tengan tags similares. Los escribe por pantalla.

Ahora abriremos el fichero single.php (dentro de tu theme) y allí escribiremos el siguiente código dónde queramos que aparezcan las entradas relacionadas.

> <div class=”related\_posts”>
> 
> <?php
> 
> getRelatedPosts ( get\_the\_ID() );
> 
> ?>
> 
> </div>

y para terminar al fichero style.css (dentro de tu tema) añadiremos el siguiente código para darle formato a los posts relacionados.

> .content .related\_posts {width: 580px; font-size:10pt;font-family: Arial; font-size: 11px; color: #333;} .content .related\_posts a {color: #2f99c9;}

Espero que os haya gustado! Alguna propuesta para el próximo no plugin?
