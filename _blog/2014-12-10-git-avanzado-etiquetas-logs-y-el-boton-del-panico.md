---
title: "Git avanzado: Etiquetas, logs y el botón del pánico"
date: "2014-12-10"
categories: 
  - "manual"
  - "programacion"
tags: 
  - "etiquetas"
  - "git"
  - "gui"
  - "log"
  - "manual-2"
  - "recovery"
  - "tags"
  - "tutorial"
---

Una vez [inicializado git](http://rocreguant.com/inicializar-git-en-linux/731/), conocidos [los primeros comandos](http://rocreguant.com/primeros-pasos-con-git/812/) y aprendido a hacer [ramas con git](http://rocreguant.com/como-crear-ramas-branches-con-git/822/) ahora **toca aprender un poco sobre etiquetas (tags), logs y que hacer cuando la lías parda**.

Las etiquetas sirven básicamente para etiquetar commits. ¿Y para que quiere uno **etiquetar commits**? Bien, pues para indicar en que momento se definió una versión de la aplicación. Para crear una etiqueta usaremos:

```
 git tag NumeroVersion idCommit
```

El id del Commit son los primeros 10 caracteres del commit al que queremos etiquetar. Te preguntarás, ¿y como se esos 10 caracteres? Pues fácil te vas al log, y para **ver el log** usarás el comando:

```
 git log
```

Si quieres algo más sofisticado y con menos ruido puedes **filtrar por autor**:

```
 git log --author=NombreUsuario
```

Sólo que archivos fueron cambiados:

```
 git log –name-status
```

O si aun así quieres ver todo el árbol con todas las ramas y etiquetas puedes usar el comando:

```
 git log --graph --oneline --decorate --all
```

En cualquier caso si quieres indagar más profundamente échale una ojeada a:

```
 git log --help
```

En el hipotético caso de que **la hayas liado parda** y no sepas como solucionar el problema eliminando todos los cambios locales y commits hechos **trayendo la versión de la rama master más reciente**. Ten en cuenta que sobre-escribirás todos tus ficheros, pero si aun así lo deseas deberás usar los siguientes comandos:

```
 git fetch origin
 git reset --hard origin/master
```

Para los que hayáis llegado tan lejos decir que git tiene incorporado algo parecido a una interfaz gráfica. **Recordar que no hay para linux una GUI que permita hacer push y toda la mandanga, solo está en Mac y WIndows.** Pero para acceder a su sucedáneo se puede acceder escribiendo en la consola:

```
gitk
```

Pero si aun así preferís seguir usando la linea de comandos quizás os interese colorear un poco el output con el comando

```
git config color.ui true
```

o en los logs simplemente mostrar sólo una linea por commit con:

```
 git config format.pretty oneline
```
