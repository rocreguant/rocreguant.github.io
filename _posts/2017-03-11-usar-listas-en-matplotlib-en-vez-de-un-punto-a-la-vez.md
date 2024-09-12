---
title: "Usar listas en matplotlib en vez de un punto a la vez"
date: "2017-03-11"
categories: 
  - "programacion"
tags: 
  - "listas"
  - "matplotlib"
  - "plot"
  - "punto"
  - "scatterplot"
---

_**TLTR:** Cuando uses matplotlib en python pasa a la función dos listas con todos los puntos en vez de ir uno por uno. Así te ahorras el rendering cada vez que usas la función consiguiendo incrementos de velocidad de varias magnitudes._

Hasta hace poco lo que hacía mayoritariamente cada vez que tenia que hacer una gráfica con matlplotlib era poner un punto cada vez. **ERROR!!!** Hasta el momento asumía que el tiempo de ejecución del script era debido a los algoritmos que usaba. Pero no, era debido a una  malapraxis muy simple de resolver. Últimamente estoy trabajando con cantidades más grandes de datos y la ejecución de mi código en python me tardaba más de lo que debería hasta que descubrí que hacia un error de novato. Poner punto por punto a una gráfica en vez de pasarle la lista entera era lo que causaba una ejecución tan lenta de mi código. Iba punto por punto porque era como me llegaban los datos y no los tenia que guardar, pero resulta que si los pongo en una lista y luego paso la lista a la librería el resultado es infinitamente más veloz y eficaz. La librería se ahorra renderizar la gráfica cada vez si recibe una lista.

El siguiente código tiene una ejecución de más de 6 segundos y como veis es la forma incorrecta de hacer un scatter plot:

\[code language="python"\] start\_time = timeit.default\_timer() for x in range(100): for y in range(10): matplotlib.pyplot.scatter(x,y)

matplotlib.pyplot.show() end\_time = timeit.default\_timer() print(end\_time - start\_time) \[/code\]

El siguiente código es la manera rápida de hacer un scatter plot y tarda unos 300ms (si MILI-segundos).

\[code language="python"\] xlist = \[\] ylist = \[\]

start\_time = timeit.default\_timer() for x in range(100): for y in range(10): xlist.append(x) ylist.append(y)

matplotlib.pyplot.scatter(xlist, ylist) matplotlib.pyplot.show() end\_time = timeit.default\_timer() print(end\_time - start\_time) \[/code\]

He subido un python notebooks (jupyter notebook) a [github](https://github.com/rocreguant/I-have-time/blob/master/scatter-times.ipynb) para que lo ejecutéis vosotros si queréis.
