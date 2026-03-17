---
title: "Resumen del paper: Análisis de datos topológicos"
date: "2018-07-17"
categories: 
  - "academia"
  - "analitica"
  - "big-data"
  - "data-mining"
  - "investigacion"
  - "manual"
tags: 
  - "academia-big-data"
  - "analisis-de-datos-topologicos"
  - "data-mining"
  - "paper"
  - "resumen"
  - "tda"
---

Recientemente me encontré un par de papers relevantes para la minería de datos (data mining). Incluso hay una empresa que basa su business model en este concepto (Ayasdi). El concepto como habéis podido leer en el titulo es análisis de datos topológicos. ¿Que significa esto? La ida principal, tal y como se expone en la Figura 1 (sacada del paper \[1\]), se basa en que los datos tienen forma y la forma es consistente. Por ejemplo, la letra "A" seguirá siendo la misma letra a pesar de que le apliquemos distintas transformaciones ya que la información obtenida es calculada en base a las distancias relativas. Podemos rotar los datos, hacia un lado u otro. Podemos cambiar la tipografía o la forma (aplastarla o extenderla) que seguirá siendo la misma letra. Al final la letra "A" esta formada por millones de puntos que no vemos. Quizás perdemos algo de detalle especifico pero se gana en visión global.

\[caption id="attachment\_1306" align="aligncenter" width="1080"\]![descripción gráfica de la letra A](images/Screen-Shot-2018-07-01-at-18.43.07.png) Figura 1: Transformaciones aplicadas a la letra A siguen formando la misma letra. Extraído de \[1\]\[/caption\]El primer paso consiste en agrupar en sub-poblaciones en bins (contenedores). En el segundo paso estas divisiones son analizadas. Cada uno de los contenedores contiene puntos que son similares el uno al otro. Como los bins han sido divididos de tal forma que solapan entre ellos por lo que cada punto de nuestros datos pueden estar en más de un grupo. Finalmente para construir la red (network) dibujamos un link entre los distintos clusters de la network final.

Para empezar a construir la red tenemos que escoger la métrica y la lente. La métrica la usaremos para medir la similitud (o distancia) entre dos puntos mientras que la lente es una función matemática para observar los datos. Cualquier métrica que sirva para producir un numero de un punto puede ser una lente. Una lente puede ser la media, max, min, el centro, PCA-score, distancia SVM, entre otros. Se pueden agrupar los resultados de distintas lentes multiplicando el resultado de los outputs.

El vector unitario producido por a lente es dividido en subgrupos que se solapan. Todos los puntos que tienen valores de lentes en el mismo subgrupo se agrupan juntos en un contenedor. De esta forma distintas particiones son obtenidas para todos los puntos gracias al resultado de la lente. Como las lentes producen sets que solapan es posible que un punto este en múltiples contenedores. Todos los puntos en un contenedor son agrupados ya que todos los puntos son altamente similares entre si y este grupo representa un simple nodo de nuestra red. El color que le asignaremos es la media del color de la lente de este grupo. El nodo en su representación gráfica tiene un tamaño proporcional al numero de puntos que tenga el cluster.

Habiendo hecho lo pasos anteriores tendremos distintos nodos en nuestra red, con diferentes tamaños y colores. Los nodos se conectaran entre si cuando tengan puntos en común. Estos links generaran la red topológica final.

Tenemos que tener en cuenta que esta implementación tiene dos parámetros. Uno es la resolución que indica el numero de contenedores en los cuales vamos a partir los datos. Una baja resolución genera unos pocos nodos gruesos sintetizando la información generada por el algoritmo. Contrariamente si la incrementamos genera muchísimos nodos pero de un tamaño mas pequeño perdiendo similitud entre nodos incluso generando clusters aislados. El segundo parámetro se llama ganancia y controla las regiones que se solapan entre contenedores. Como mas grande sea la ganancia mas aristas (conexiones entre nodos) vas a obtener el tu red. Este parámetro resalta las relaciones entre los elementos de tus datos.

No hay unos valores óptimos para la resolución y la ganancia. Cada red es singular y sus parámetros tienen que ser escogidos acordemente. También depende de lo que se quiera observar en la red. Por lo que cada análisis requerire una afinación (tuning). Tened en cuenta que una resolución alta no siempre es lo mejor, ya que al final lo que puede producir un resultado muy similar al observar los datos directamente

Ya hemos explicado todas las ventajas ahora toca exponer algunas de sus desventajas. No es ninguna "magic bullet" puede funcionar para muchos casos pero hay otros en los que este algoritmo no sea el mejor para nuestros datos. No hay una sola solución que sea buena para todos los casos. Parte del problema es que es una ciencia con un alto componente matemático. Como los principios del deep learning, hasta que no haya implementaciones eficientes y fáciles de usar, la "gente normal" se va a abstener de usarlo. Finalmente, el coste computacional. Calcular todos los pasos es extremadamente costoso ya que se tienen que hacer distintos barridos sobre los datos e incluso calcular las distancias entre pares.

Para los que os vaya la marcha os dejo un vídeo de youtube. Se trata de un seminario en Standford donde se explica extremadamente bien el concepto (en ingles). Luego os dejo una presentación en slideshare donde se explica el concepto detalladamente. Y para terminar os dejo tres referencias que he usado para escribir este post y que si entendéis inglés las recomiendo encarecidamente que les echéis un vistazo.

 

https://www.youtube.com/watch?v=x3Hl85OBuc0

 

### Archivos multimedia para profundizar en el TDA

https://www.slideshare.net/ColleenFarrelly/topology-for-data-science

 

### Referencias:

 

1. Offroy, M., & Duponchel, L. (2016). **Topological data analysis: A promising big data exploration tool in biology, analytical chemistry and physical chemistry.** _Analytica chimica acta_, _910_, 1-11.
2. Nielson, J. L., Paquette, J., Liu, A. W., Guandique, C. F., Tovar, C. A., Inoue, T., ... & Lum, P. Y. (2015). **Topological data analysis for discovery in preclinical spinal cord injury and traumatic brain injury.** _Nature communications_, _6_, 8581.
3. Chazal, F., & Michel, B. (2017). **An introduction to Topological Data Analysis: fundamental and practical aspects for data scientists.** _arXiv preprint arXiv:1710.04019_.
