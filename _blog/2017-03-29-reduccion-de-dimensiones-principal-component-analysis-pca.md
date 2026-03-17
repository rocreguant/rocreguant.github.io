---
title: "Reducción de dimensiones: Principal Component Analysis (PCA)"
date: "2017-03-29"
categories: 
  - "analitica"
  - "big-data"
tags: 
  - "pca"
  - "principal-component-analysis"
  - "reduccion-de-dimensiones"
---

Principal Component Analysis o PCA en corto es un método de reducción de dimensiones bastante conocido y comúnmente usado. Este método transforma ortogonalmente las observaciones (quizás relacionadas) en un conjunto de puntos linealmente no relacionados. De esta forma se consigue que el primer componente tenga la varianza mayor. El siguiente componente será el que tendrá la varianza mayor de los restantes y es ortogonal al anterior componente, y así sucesivamente. Este método es sensible a la escala de las variables. Para evitar que los valores sean un problema tendremos que escalar las variables estandardizándolos antes de usar PCA.
