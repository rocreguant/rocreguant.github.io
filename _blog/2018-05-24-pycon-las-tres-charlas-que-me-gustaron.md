---
title: "PyCon: Las tres charlas que me gustaron"
date: "2018-05-24"
categories: 
  - "programacion"
  - "videos"
tags: 
  - "cython"
  - "dask"
  - "machine-learning"
  - "numba"
  - "numpy"
  - "optimizacion-de-codigo"
  - "pycon"
  - "python"
---

El PyCon2018 fue del 9 al 17 de mayo en Cleveland. La conferencia nos dejó una [gran cantidad de charlas interesantes](https://www.youtube.com/channel/UCsX05-2sVSH7Nx3zuk3NYuQ/videos). A mi personalmente me gustaron tres. Dos de machine learning y una de optimización de código. Aquí dejo los vídeos para que podáis echarles una ojeada. Además dejo un mini-resumen con cada vídeo.

## A practical guide to Singular Value Decomposition in Python

<iframe src="https://www.youtube.com/embed/d7iIb_XVkZs?autoplay=0" width="420" height="315"></iframe>

Esta charla es una introducción a los SVD (Singular Value Decomposition). Los SVD descomponen cada punto en vectores y miden las diferencias basándose en el ángulo de separación entre los elementos. Daniel Pyrathon defiende el uso de este algoritmo gracias a la demostrada efectividad de Netflix. Como ejemplo pone a Netflix, dónde la mayoría de vídeos recomendados nos gustan. Nos gustan porque el algoritmo ha sabido encontrar similitudes entre otros usuarios y entre series/películas. La charla es amena y recomendable.

## Fighting the Good Fight: Python 3 in your organization

<iframe src="https://www.youtube.com/embed/H4SS9yVWJYA?autoplay=0" width="420" height="315"></iframe>

Durante unos 30min muy entretenidos Jason Fried nos explica como entrenó la inteligencia artificial para aprender a jugar al Street fighter. Des del principio el conferenciante engancha y nos explica la pipeline usada dónde el ordenador aprende a “entender” la pantalla (barras de salud, tiempo, y los jugadores) y pasa a optimizar las acciones para maximizar la recompensa. Optimizando para conseguir la mayor recompensa el algoritmo encuentra combinaciones de movimientos para ganar a los sus oponentes.

## Performance Python: Seven Strategies for Optimizing Your Numerical Code

<iframe src="https://www.youtube.com/embed/zQeYx87mfyw?autoplay=0" width="420" height="315"></iframe>

Quizás esta sea la charla más técnica de las tres. Jake VanderPlas nos explica como podemos optimizar la ejecución de nuestro código. En la charla expone siete herramientas que los programadores podemos usar para optimizar nuestro código. Des del uso de librerías para manejar vectores de forma eficiente, hasta compiladores que transforman el código de Python a C. Pasando por herramientas para paralelizar el código. Numpy, Cython, Numba, y Dask son algunas de las herramientas mencionadas.

¿Que te parecieron a ti las otras charlas? ¿Tienes alguna que recomiendes?
