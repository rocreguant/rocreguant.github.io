---
title: "Reducción de dimensiones: Introducción a los espacios multidimensionales"
date: "2017-01-09"
categories: 
  - "analitica"
  - "big-data"
tags: 
  - "espacios-multidimensionales"
  - "introduccion"
  - "reduccion-de-dimensiones"
---

En inteligencia artificial y machine learning en la mayoría de ocasiones se usan espacios multidimensionales. Los espacios multidimensionales son espacios en los que los datos requieren más de un valor. Los espacios multidimensionales son espacios con puntos repartidos por el espacio. Un espacio 2D tiene dos dimensiones, las típicas X, Y. Un espacio 3D tiene tres dimensiones X, Y, Z. Las dimensiones las puedes llamar X, Y, Z pero también perro, gato, conejo. Como seres humanos estamos limitados a poder visualizar espacios a 3D máximo. Aunque no puedas visualizar dimensiones superiores a tres, puedes llegar a entenderlo. Imagínate que quieres ir a un restaurante a 10km máximo de tu casa. Esto en un mapa son dos dimensiones norte/sur y este/oeste. Ahora si decides que quieres ir a un restaurante italiano ya hemos añadido otra dimensión. Si no quieres pagar más de 10€ por la cena ya has añadido otra dimensión. Por lo que ya tenemos un espacio de 4D. Dos para las dimensiones del mapa norte/sur, este/oeste, otra para que tipo de restaurante y la cuarta para los precios. Se le podría sumar otra dimensión si añadiéramos en que planta esta el restaurante. Virtualmente podríamos añadir infinidad de dimensiones.

Un vector o un punto en nuestro espacio es un conjunto de valores para todas las dimensiones. Un valor (o dato) puede ser indefinido o ausente, no tiene porque tener un valor concreto. Un punto es asociado a la persona o el elemento de la acción. Tu puedes ser ese vector/punto. Con el ejemplo anterior nuestro punto sería (23, 31, italiano, 10) que hacen referencia a norte/sur, este/oeste, tipo de comida y precio máximo. Las variables pueden ser categóricas y cuantitativas. Las categóricas es “italiano” no tiene un valor númerico asociado. Otros ejemplos de variables categóricas pueden ser el sexo de una persona o su color preferido. Las variables cuantitativas son los números.

La pregunta del millón es: cómo podemos pensar en un espacio de más de tres dimensiones en el que una de ellas es “italiano”? Simplemente no podemos. Nuestro cerebro no puede visualizar más de tres dimensiones. Estos espacios sólo tienen sentido matemáticamente. Por lo que para trabajar en este tipo de espacios si queremos visualizarlos de algún modo tenemos que pensar en tres dimensiones máximo y extrapolarlo. Otra opción también puede ser usar distintas técnicas de reducción de dimensiones. En los próximos posts describiré distintos métodos para la reducción de dimensiones.
