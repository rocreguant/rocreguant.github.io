---
title: "Como calcular distancias entre dos arrays con variables binarias"
date: "2018-07-08"
categories: 
  - "analitica"
  - "big-data"
  - "bioinformatics"
  - "machine-learning"
tags: 
  - "algoritmo"
  - "array"
  - "binario"
  - "distancias"
  - "lista"
  - "metodo"
---

El computo de distancias es un procedimiento básico para poder procesar datos. Las distancias nos sirven en el mundo real para poder desplazarnos con efectividad pero también podemos usar las distancias en el mundo no-físico para medir la similitud entre dos entidades. Cuando hablamos de entidades no-físicas nos referirnos por ejemplo a palabras, objetos o conceptos abstractos. Por ejemplo, ¿Cual es la similitud entre dos palabras? Dependiendo del enfoque podemos obtener resultados muy distintos. En este caso estoy interesado en los distintos métodos para calcular distancias entre dos vectores binarios por ejemplo \[0,1,0,0,0,1,1\] y \[0,0,1,0,0,1,0\]. Si fueran vectores normales los podríamos tratar en el plano euclidiano calculando distancias como lo haríamos sobre un mapa pero usando 7 dimensiones, pero al ser binarios cada dimensión solo puede ser 0 ó 1 (y ningún otro valor intermedio). La solución no pasa por asignar otros números a las variables porque substituyendo el "uno" por un "tres" no cambia nada. Por ejemplo, las palabras binarias pueden servir para codificar si eres hombre (0) o mujer (1). ¿Cual es la distancia entre un hombre y una mujer? Lo mismo pasa con palabras, cual es la distancia entre "hola" y "guacamole" No hay un solo método universal que nos sirva para todos los problemas, por esta razón he hecho esta lista para que os pueda servir en un futuro. Los métodos de esta lista calculan la distancia entre vectores con elementos binarios. Cada método - o algoritmo - tiene sus ventajas e inconvenientes obligando al usuario a entender el problema y escoger la solución más adecuada para cada caso.

Todas las formulas siguen el mismo patrón. En la siguiente tabla hay todas las opciones que las variables pueden tomar:

<table><tbody><tr><td style="text-align: center;"><strong>.</strong></td><td style="text-align: center;"><strong>y = 1</strong></td><td style="text-align: center;"><strong>y = 0</strong></td><td style="text-align: center;"><strong>Total</strong></td></tr><tr><td style="text-align: center;"><strong>x = 1</strong></td><td style="text-align: center;">n11</td><td style="text-align: center;">n10</td><td style="text-align: center;">n1•</td></tr><tr><td style="text-align: center;"><strong>x = 0</strong></td><td style="text-align: center;">n01</td><td style="text-align: center;">n00</td><td style="text-align: center;">n0•</td></tr><tr><td style="text-align: center;"><strong>Total</strong></td><td style="text-align: center;">n•1</td><td style="text-align: center;">n•0</td><td style="text-align: center;">N</td></tr></tbody></table>

## Coeficiente de Jaccard

El [coeficiente de Jaccard](https://en.wikipedia.org/wiki/Jaccard_index) o el índice de Jaccard es una de las distancias mas intuitivas. Computa la cardinalidad de la intersección de los dos conjuntos (el numero de elementos que están en los dos grupos a la vez) dividido por su unión (todos los elementos que forman parte de un grupo o del otro). Dividiendo usando la unión de los conjuntos evita que conjuntos grandes con poca similitud dominen el espacio.

\[mathjax\]

$$ Coeficente de Jaccard = \\frac{n11}{n1•+n•1}$$

## Coeficiente de Sørensen–Dice

[Este método](https://en.wikipedia.org/wiki/S%C3%B8rensen%E2%80%93Dice_coefficient) fue originalmente desarrollado para la botánica. Sørensen y Diece lo desarrollaron de forma independiente con 3 años de diferencia. Muy parecido al anterior, este se basa en dos veces la intersección dividido por la cardinalidad de los conjuntos. El numerador es multiplicado por dos porque en el denominador la unión de estos conjuntos contiene la intersección de los conjuntos duplicada, hay un conjunto de elementos que están en el grupo A y el grupo B.

$$ Sørensen-Diece = \\frac{2\*n11}{n•1+n1•}$$

## Coeficiente de correlación de pearson

Quizás esta sea la métrica más avanzada de este post. A pesar de que algunos estadistas la han usado no tengo tan claro que sea una buena métrica para comparar arrays binarios. A pesar de esto lo voy a dejar al gusto del lector comprobar su validez con los datos.

$$ Coef pearson = \\frac{ (n11-\\frac{n01\*n10}{N})}{sqrt(n10-N\*n10/n^2)\*sqrt(n01-N\*n01/n^2)}$$

## Coeficiente de Phi

El [coeficiente Phi o coeficiente de correlación de Matthews](https://en.wikipedia.org/wiki/Phi_coefficient) es una medida para la asociación de dos variables binarias. En teoría si calculamos el coeficiente de correlación pearson para dos variables binarias nos dará el mismo resultado que con el coeficiente Phi.

$$Phi = \\frac{n11\*n00 - n10\*n01}{sqrt(n0•\*n1•\*n•0\*n•1)} $$

## Distancia de Yule

Con la distancia [distancia de yule](https://docs.scipy.org/doc/scipy-0.14.0/reference/generated/scipy.spatial.distance.yule.html) no es extrapolable a otras métricas. Como estamos pudiendo ver todas las métricas se parecen mucho. Se busca lo común entre los conjuntos y se divide por el computo global o similar para corregir para el tamaño de los grupos.

$$ Yule distance = \\frac{2\*(n10+n01)}{n11+n01+n10+n01} $$

## Russell-rao

En este caso la métrica es algo distinta. Las otras métricas miran lo que tienen en común los grupos, este algoritmo hace lo contrario. [Rusell-rao buscan lo que no tienen en común](http://reference.wolfram.com/language/ref/RussellRaoDissimilarity.html). Aunque siguen normalizando el resultado para conseguir valores relativos.

$$Russel-Rao = \\frac{N-n11}{N}$$

## Sokal-Michener

Por esta distancia y la siguiente no encontré mucha información, por lo que usé [los detalles de implementación de la libreria de python scipy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.distance.sokalmichener.html).

$$ Skoal-Michener = \\frac{2\*(n1•+n•1)}{(2\*(n1•+n•1)+n11+n00)}$$

## Rogers-Tanmoto

Al igual que el anterior aquí os dejo el [link a la implementación de scipy](https://docs.scipy.org/doc/scipy-0.14.0/reference/generated/scipy.spatial.distance.rogerstanimoto.html).

$$ Rogers-Tanmoto = \\frac{n11+n00}{n11+n00+2\*(n10+n01)} $$

## Mutual information

O en español [información mutua](https://en.wikipedia.org/wiki/Mutual_information) mide la interconexión entre dos variables. Puesto de otra forma, mide la incertidumbre de una variable habiendo observado otra (conocido como entropía). Esta métrica también es avanzada y aunque no se como funciona en comparación a pearson me da mejores vibraciones. Me ha resultado difícil/ineficiente implementarlo yo mismo completamente así que os dejo un snippet con el código en python.

\[code language="python"\]

from sklearn.metrics import mutual\_info\_score

def calc\_MI(x, y, bins): c\_xy = np.histogram2d(x, y, bins)\[0\] mi = mutual\_info\_score(None, None, contingency=c\_xy) return mi

\[/code\]

## Kulczynski-2

En teoría [Kulczynski](https://www.ibm.com/support/knowledgecenter/SSLVMB_22.0.0/com.ibm.spss.statistics.algorithms/alg_proximities_kulczynski2.htm) consiguió mejorar la facilidad de crear clusters. Lo mismo que hace Jaccard y que Russell-Rao mejoraron. Este es la segunda versión, más sofisticada.

$$ Kulczynski-2 = \\frac{\\frac{n11^2}{(n11+n01)\*(n11+n10)}}{2} $$

## Ochiai

En teoría [ochiai](https://en.wikipedia.org/wiki/Cosine_similarity) - también conocido como _cosine similarity_\- consigue mejorar Kulczynski-2 y consecuentemente Jaccard y Rusell-Rao.

$$ Ochiai = sqrt(\\frac{a^2}{(n11+n10)\*(n11+01)} $$

Yo lo dejo aquí pero podéis encontrar más métricas en los siguientes enlaces:

Search Results _[Binary Vector Dissimilarity Measures for Handwriting Identification](http://www.cedar.buffalo.edu/papers/articles/SPIE03_hwidiss.pdf)_ consta de varias métricas, algunas ya señaladas en los anteriores apartados. Tengo que decir que las formulas que exponen me parecen algo raras, no se si las han adaptado al caso en concreto.

Para una [descripción en profundidad de Kulczynski y Ochiai](https://stats.stackexchange.com/questions/61705/similarity-coefficients-for-binary-data-why-choose-jaccard-over-russell-and-rao)

[Spearman's rank correlation coefficient or Spearman's rho](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient) para vuestro disfrute.
