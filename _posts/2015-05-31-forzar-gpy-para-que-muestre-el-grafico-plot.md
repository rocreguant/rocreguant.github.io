---
title: "Forzar GPy para que muestre el gráfico (plot)"
date: "2015-05-31"
categories: 
  - "analitica"
  - "programacion"
  - "trucos"
---

Recientemente he estado programando con _Gaussian processes framework in python_ (GPy) y no conseguía mostrar a través de un gráfico los resultados obtenidos. El problema es que al finalizar la ejecución del script la ventana con el gráfico también se cerraba automáticamente. Para solucionar esto se tiene que forzar la librería _matplotlib_ que bloquee la ventana para así poder visualizar los datos. Si ubicamos la siguiente linea después del plot nos congelará la ventana evitando que se cierre al finalizar el la ejecución.

```
matplotlib.pylab.show(block=True)
```
