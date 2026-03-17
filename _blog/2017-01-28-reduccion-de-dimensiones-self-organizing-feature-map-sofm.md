---
title: "Reducción de dimensiones: Self-organizing feature map (SOFM)"
date: "2017-01-28"
categories: 
  - "analitica"
  - "big-data"
tags: 
  - "espacios-multidimensionales"
  - "neural-networks"
  - "redes-neuronales"
  - "reduccion-de-dimensiones"
  - "sofm"
  - "som"
  - "visualizacion-de-datos"
---

**Self-organizing map (SOM)** o **self-organizing feature map (SOFM)** es un método que usa redes neuronales (neuronal networks) para reducir las dimensiones de un vector de datos. Para reducir las dimensiones lo que hace es usar los vecinos de un punto en concreto para moverlo al nuevo espacio dimensional manteniendo la misma topografía que en el espacio original.

Una de las ventajas de SOFM es que es un método _unsupervised_, esto quiere decir que no necesitamos un _training dataset_ para entrenar nuestra red neuronal. Normalmente para la inteligencia artificial (y el machine learning) se requiere que el training dataset esté etiquetado. Un data set etiquetado son puntos del input que ya se sabe cual tiene que ser el resultado. De este modo la maquina es capaz de identificar que resultado tiene que producir.

Para explicar con más detalle este método voy a usar la foto de la wikipedia que lo hace más visual.

\[caption id="" align="aligncenter" width="1000"\]![Somtraining](https://upload.wikimedia.org/wikipedia/commons/9/91/Somtraining.svg) SOMF training\[/caption\]

En la imagen vemos la malla que representa el input en un espacio multidimensional y la zona azul que representa un espacio 2D al que queremos extrapolar nuestros puntos. El primer paso es seleccionar nuestro punto en el espacio de origen que se acerque mas al espacio 2D. El segundo paso es mover ese punto en concreto al espacio 2D. El tercer paso, y ultimo, consiste en mantener las distancias entre puntos en el nuevo plano. Si se consigue mantener las distancias entre los puntos conseguiremos una reducción de dimensiones satisfactoria.

El paper original lo podéis encontrar [aquí](http://link.springer.com/article/10.1007%2FBF00288907). Pero si no tenéis ninguna afiliación académica quizás os interese [checkear este otro post](http://rocreguant.com/consigue-todos-las-publicaciones-cientificas-que-quieras/957/).
