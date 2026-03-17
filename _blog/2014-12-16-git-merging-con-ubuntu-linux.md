---
title: "Git Merging con Ubuntu (Linux)"
date: "2014-12-16"
categories: 
  - "programacion"
tags: 
  - "comparacion"
  - "control-de-versiones"
  - "git"
  - "github"
  - "gui"
  - "herramienta"
  - "kdiff3"
  - "meld"
  - "merging"
  - "programacion-2"
  - "tool"
---

Como muchos programadores de Linux ya os habréis dado cuenta, **no hay una aplicación nativa de GitHub para Linux** (a diferencia de Windows y Mac). Sinceramente me parece algo ilógico ya que los programadores tenemos una tendencia a gravitar hacia Linux. Pero a grandes males grandes remedios, no? Cuando en un repositorio tenemos conflictos (merge conflict) y hay que solventarlos, **una herramienta de merge nos va a ser bastante útil más que resolver el conflicto a mano** o usando la consola. Una GUI, aunque no lo parezca, es bastante útil en algunos casos.

He probado kdiff3 y meld. A mi parecer no tienen punto de comparación, claramente l**a mejor herramienta es meld** por algunas simples razones.

## Kdiff3:

[![Captura de pantalla de la GUI de kdiff3](images/kdiff3.png)](http://rocreguant.com/wp-content/uploads/2014/12/kdiff3.png)

- Me parece que usa una GUI obsoleta y poco intuitiva.
- No encontré la opción para cambiar el idioma (la instalé des de Alemania y estaba en alemán).

## Meld

[![Captura de pantalla de la GUI de meld](images/meld.png)](http://rocreguant.com/wp-content/uploads/2014/12/meld.png)

- Por el contrario su GUI es más intuitiva y algo más moderna.
- Estaba en inglés des del principio.
- No me gustó que creara dos ficheros, para el archivo remoto y otro para el local (además del que se sube a la rama).

**Para usar estos merge tools usaremos esta linea** en la consola (cambiando meld por kdiff3 si te gusta más este):

```
 git mergetool -t meld
```

Puede ser que no los tengas instalados, usando el siguiente comando lo instalaremos (o kdiff3 en vez de meld):

```
sudo apt-get install meld
```

Finalmente una vez convencido de la herramienta podremos usar la siguiente linea para **guardar la herramienta deseada** e iniciar el programa que más nos haya gustado cada vez que surja un merge conflict.

```
git config --global merge.tool meld
```

Si conoces una herramienta mejor no puedes en dejarlo en los comentarios. Me encantará conocerla! :)

[Fuente e imágenes](http://www.gitguys.com/topics/merging-with-a-gui/)
