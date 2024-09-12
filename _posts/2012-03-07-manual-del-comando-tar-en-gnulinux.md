---
title: "Manual del comando tar en GNU/Linux"
date: "2012-03-07"
categories: 
  - "gnulinux"
  - "manual"
tags: 
  - "comando"
  - "consola"
  - "gnulinux-2"
  - "manual-2"
  - "tar"
---

Antes de nada quiero aclarar que los archivos .tar son ficheros comprimidos, y la comanda tar para la consola es usado para almacenar archivos y directorios en un solo archivo.

Teniendo en cuenta que las opciones entre \[ \] son opcionales, usaremos la comanda básica de la siguiente forma:

```
tar [opciones] [fichero] [directorio]
```

Las opciones se ponen todas seguidas, sin espacio y sin los \[ \]. Aquí os dejo algunas de las opciones, que he considerado más importantes:

<table cellspacing="0" cellpadding="4" width="643"><colgroup><col width="147"> <col width="478"></colgroup><tbody><tr valign="TOP"><td width="147">c</td><td width="478">Sirve para indicar que queremos creer el archivo .tar</td></tr><tr valign="TOP"><td width="147">z</td><td width="478">Comprime el archivo .tar usando Gzip, reduciendo así el tamaño total del archivo.tar deseado</td></tr><tr valign="TOP"><td width="147">f</td><td width="478">Cuando se usa con la opción -c sirve para forzar la crearcion del fichero.tar indicado</td></tr><tr valign="TOP"><td width="147">x</td><td width="478">Extrae, y descomprime si se da el caso, los directirios y archivos que se encuentren dentro del fichero.tar específico</td></tr><tr valign="TOP"><td width="147">v</td><td width="478">Esta opción al igual que en otras comandas permite que se muestre por pantalla todos los pasos que se vayan realizando. Si no se pone se realizarán las mismas operaciones pero no lo veremos por pantalla</td></tr></tbody></table>

Dicho esto veamos algunos ejemplos.

Para empezar, podemos empaquetar sin comprimir. En este ejemplo empaquetaos el directorio /etc/toda-la-musica creando un fichero musica.tar que se creará en el directorio /home. Nótese que está la opción de verbose. Comando:

```
tar cvf /home/musica.tar /etc/toda-la-musica
```

Ahora para desempaquetar el archivo anteriormente creado usaremos el siguiente comando, tengo que añadir que el archivo desempaquetado se creará en el directorio dónde esté ubicada la termianl. Comando:

```
 tar xvf /home/musica.tar
```

Ahora comprimiremos el paquete haciendo que tenga menos peso. Al comprimir el fichero teóricamente la extensión pasa de .tar a .tgz. En principio sigue el mismo esquema anterior pero en ambos casos añadiremos la opción -z.

Por ejemplo para empaquetar y comprimir podemos usar:

```
 tar cvfz /home/musica.tar /etc/toda-la-musica
```

_Para desempaquetarlo podemos usar:_

```
 tar xvfz /home/musica.tar
```

Y eso es todo amigos! Para cualquier cosa dejad un comentario, y que los comandos de la consola os acompañen.
