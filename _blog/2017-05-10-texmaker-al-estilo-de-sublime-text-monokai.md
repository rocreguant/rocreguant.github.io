---
title: "Texmaker al estilo de Sublime text (monokai)"
date: "2017-05-10"
categories: 
  - "gnulinux"
  - "manual"
---

Sublime text, aunque es un editor de texto que me gusta mucho, he estado buscando alternativas. He encontrado textmaker. **Texmaker es  un editor de latex** que nos permite compilar el documento pdf además de añadir otras interesantes features. Lo que no me gustaba era el tema (theme) que tenía por defecto. Así que buscando di con la solución. Usar el theme de Sublime text, llamado monokai.

Para cambiarlo simplemente tenemos que ir a **$HOME/.config/xm1** (tanto en linux, como en MacOS y editar el fichero **texmaker.ini** y reemplazar las siguientes lineas de la principio del fichero:

```
Color\Background=@Variant(\0\0\0\x43\x1\xff\xff\0\0++66\0\0)
Color\Command=@Variant(\0\0\0\x43\x1\xff\xff&&\x8b\x8b\xd2\xd2\0\0)
Color\Comment=@Variant(\0\0\0\x43\x1\xff\xffllqq\xc4\xc4\0\0)
Color\Highlight=@Variant(\0\0\0\x43\x1\xff\xff\a\a66BB\0\0)
Color\Keyword=@Variant(\0\0\0\x43\x1\xff\xff\xdc\xdc\x32\x32//\0\0)
Color\KeywordGraphic=@Variant(\0\0\0\x43\x1\xff\xff\x85\x85\x99\x99\0\0\0\0)
Color\Line=@Variant(\0\0\0\x43\x1\xff\xff\a\a66BB\0\0)
Color\Math=@Variant(\0\0\0\x43\x1\xff\xff**\xa1\xa1\x98\x98\0\0)
Color\NumberGraphic=@Variant(\0\0\0\x43\x1\xff\xff\xcb\xcbKK\x16\x16\0\0)
Color\Standard=@Variant(\0\0\0\x43\x1\xff\xff\x83\x83\x94\x94\x96\x96\0\0)
Color\Todo=@Variant(\0\0\0\x43\x1\xff\xff\xd3\xd3\x36\x36\x82\x82\0\0)
Color\Verbatim=@Variant(\0\0\0\x43\x1\xff\xff\xb5\xb5\x89\x89\0\0\0\0)
```
