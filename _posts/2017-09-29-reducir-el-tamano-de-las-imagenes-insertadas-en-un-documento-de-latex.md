---
title: "Reducir el tamaño de las imágenes insertadas en un documento de Latex"
date: "2017-09-29"
categories: 
  - "scripts"
tags: 
  - "bash"
  - "conversion"
  - "latex"
---

El otro día estaba escribiendo mi tesis en latex y me di cuenta que las páginas que tenían figuras tardaban mucho en cargar. Llegué a la conclusión que era debido a la complejidad de la imagen. Por lo que después de hacer un poco de investigación encontré la solución. Tenia que convertir todos los pdf a png (u otro tipo de formato de imagen).

El script convierte todos archivos de un directorio de pdf a png. Con cada iteración del script convierte cada archivo. Cara archivo tarda unos cinco minutos, así que paciencia.

```
for file in /Users/roc/Desktop/th/aux/* #hesis-plots/*
do
  y=${file%.*}
  convert -density 300 $y.pdf $y.png
done

```
