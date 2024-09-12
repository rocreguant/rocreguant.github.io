---
title: "Como crear ramas (branches) con git"
date: "2014-12-03"
categories: 
  - "manual"
  - "programacion"
tags: 
  - "branches"
  - "git"
  - "manual-2"
---

Ahora que ya tenemos [git inicializado](http://rocreguant.com/inicializar-git-en-linux/731/)  y [hemos aprendido unos primeros pasos](http://rocreguant.com/primeros-pasos-con-git/812/) tocará empezar con unos conceptos un poco más avanzados. En este post aprenderemos a crear ramas. Normalmente los proyectos usan ramas para mantener la rama master “más limpia”, evitar commits a medias y evitar conflictos.

Para que nos entendamos la rama master es la rama principal y en las otras ramas es dónde hacemos los cambios. Para crear una rama empezaremos con:

```
 git checkout -b NombreRama
```

Como ya vimos después de aplicar los cambios en nuestra rama tocará subir los cambios al directorio remoto haciendo un:

```
 git push
```

Una vez terminados todos los cambios y dar la rama por acabada realizaremos el merge. Que básicamente es mezclar nuestros cambios con la rama master. Para esto usaremos el comando:

```
git merge nombreRama
```

Algunas veces esto ocasionará conflictos que deberemos solventar. Para ver los conflictos podemos usar:

```
 git diff <source_branch> <target_branch>
```

Y si hemos intentado hacer un “merge” que ha sido fallido debido a los conflictos deberemos volver a hacer un:

```
git add nombreArchivo
```

Una vez terminado del todo lo que podemos hacer es volver a la rama master con:

```
git checkout master
```

Y finalmente borrar la rama con el comando:

```
git branch -d feature_x
```

Cabe mencionar que la rama “no está disponible para terceros” a menos que se haga un push al repositorio remoto. Esto se puede hacer con el comando:

```
git push origin
```

Para los que les haya interesado este post sobre como crear ramas (branches) en git quizás les interese [indagar un poco más en este \[EN\]](http://nvie.com/posts/a-successful-git-branching-model/) modelo de creación de ramas con git. Haciendo un resumen rápido, tienen la rama principal, luego la rama developer y a partir de aquí crean ramas de features.
