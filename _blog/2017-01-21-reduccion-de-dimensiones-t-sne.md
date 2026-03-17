---
title: "Reducción de dimensiones: T-SNE"
date: "2017-01-21"
categories: 
  - "analitica"
  - "big-data"
tags: 
  - "espacios-multidimensionales"
  - "reduccion-de-dimensiones"
  - "t-sne"
  - "visualizacion-de-datos"
---

Como ya explicamos en el post anterior los ordenadores si que pueden procesar grandes cantidades de datos multidimensionales. Pero los humanos a veces necesitamos “ver” y entender los datos. Cuando estamos trabajando en un espacio multidimensional no podemos imaginarnos nuestro dataset. Para solventar este problema se ha desarrollado T-SNE. Éste es un algoritmo pensado especialmente en reducir dimensiones (a 2 o 3) para que podamos visualizar los datos. En el [paper original](http://www.cs.toronto.edu/~hinton/absps/tsne.pdf) se expresa de forma explícita que el algoritmo está pensado para la visualización de datos. **Usar T-SNE para la reducción de dimensiones** puede causar efectos desconocidos. Así que si lo usas para evitar “[la maldición de la dimensionalidad](https://es.wikipedia.org/wiki/Maldici%C3%B3n_de_la_dimensi%C3%B3n)”  allá tu ;)

**El concepto principal consiste en que los puntos cercanos (en el espacio multidimensional) se atraen y los distantes se repelen.** Para conseguir este objetivo el algoritmo tiene unos cuantos parámetros que se permiten alterar. La “**perplexity**” es la cantidad de vecinos que un simple punto puede afectar. Por lo que he visto hasta ahora un valor entre 30-50 suele ser el óptimo. Luego tenemos **epsilon** que nos sirve para determinar el tamaño de los pasos de aprendizaje. Valor pequeño el algoritmo le cuesta más a encontrar el óptimo. Con un valor grande te lo puedes pasar. Finalmente la **cantidad de iteraciones** o steps para conseguir la convergencia. A más iteraciones en teoría más cerca del valor óptimo, pero como es evidente como más iteraciones más tiempo de computación requieres.

Para los que queráis visualizar como funciona y un poco sus efectos cambiando los parámetros [podéis verlo en vuestro navegador](http://distill.pub/2016/misread-tsne/). Si por el contrario queréis implementarlo en Javascript [aquí](https://github.com/karpathy/tsnejs) podéis encontrar una versión oficial del desarrollador principal (es la que estoy usando). Pero si sois tan _malotes_ que queréis implementarlo vosotros mismos mejor que os [leáis el paper original](http://www.cs.toronto.edu/~hinton/absps/tsne.pdf).

_**Bonus:** En el paper para computar las distancias se usa la distancia euclidiana (la "normal") quizás otro tipo de distancias puede ir mejor para vuestro problema._
