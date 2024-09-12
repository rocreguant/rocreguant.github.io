---
title: "Primeros pasos con git"
date: "2014-11-21"
categories: 
  - "manual"
  - "programacion"
tags: 
  - "git"
  - "manual-2"
  - "tutorial"
---

Como dije ya en su momento, **git es un sistema de control de versiones**. Ahora que [ya tenemos git inicializado](http://rocreguant.com/inicializar-git-en-linux/731/ "Inicialización de git") tenemos que aprender las posibilidades más básicas que nos ofrece.

Para empezar tendremos que crear un repositorio. Para esto usaremos:

```
git init
```

En caso de que algún colega ya tenga un repositorio lo que haremos será:

```
git clone username@host:/path/to/repository
```

 En el caso que esté alojado en github, este link lo encontraremos en el lado derecho debajo de “_SSH clone URL_”.

Ahora que tenemos los ficheros en nuestro ordenador, tocará trabajar con ellos. Una vez hayamos hecho el cambio que queríamos tenemos que proponer un cambio. Para esto usaremos:

```
git add nombreArchivo
```

o si simplemente queremos subirlo todo haremos

```
git add *
```

Pero para realmente remitir los cambios tendremos que usar:

```
git commit -m “mensaje que queramos”
```

 Cabe indicar que cuanto más descriptivos los mensajes mejor, ya que cuando haya conflictos nos servirá para entender mejor como debemos proceder.

Ahora después del commit, tenemos los cambios “guardados” en el fichero HEAD de nuestro ordenador. Ahora tocará enviar nuestros cambios al directorio remoto. Para esto usaremos el siguiente comando:

```
git push origin master
```

Espero que os haya servido ya que va a haber algunos más! :)
