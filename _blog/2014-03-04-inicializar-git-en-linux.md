---
title: "Inicializar git en Linux"
date: "2014-03-04"
categories: 
  - "gnulinux"
  - "manual"
  - "programacion"
tags: 
  - "git"
  - "github"
  - "linux"
  - "manual-2"
  - "tutorial"
---

Según [wikipedia](http://es.wikipedia.org/wiki/Git): _“**Git es un software de control de versiones**, pensando en la eficiencia y la fiabilidad del mantenimiento de versiones de aplicaciones cuando estas tienen un gran número de archivos de código fuente.”_

## 1- Instalar Git

```
$ sudo apt-get install git-core
```

## 2- Asignar una identificación

```
$ git config --global user.name "Paco"
```

```
$ git config --global user.email paco@ejemplo.com
```

Ahora para enlazar nuestro pc con la cuenta en [github](https://github.com/).

## 3 – Comprobando los certificados

```
$ cd ~/.ssh
```

```
$ ls -al
```

Si con los comandos anteriores encontramos alguno de los siguientes ficheros _id\_rsa.pub_ o _id\_dsa.pub_ puedes saltarte la **generación de una nueva clave SSH** e ir directamente a **añadir tu clave en Github, paso 5**.

## 4- Generar una nueva clave SSH

```
$ ssh-keygen -t rsa -C "paco@ejemplo.com"
```

```
$ ssh-add id_rsa
```

Te pedirán que entres una frase de contraseña (passphrase) dos veces (guardatela).

## 5- Añadir tu clave SSH a Github

Puedes printar por consola el texto usando el siguiente comando:

```
$ cat ~/.ssh/id_rsa.pub
```

Y luego desde pantalla copiar el texto.

Finalmente **en Github** iremos a **Account settings** en el apartado de **SSH keys** y una vez allí en el **campo de la Key pegaremos el output de la consola** anteriormente copiado.

**Para comprobar** que lo hemos hecho todo correctamente podemos usar el siguiente comando:

```
$ ssh -T git@github.com
```
