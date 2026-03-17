---
title: "Como ejecutar DALI para el alineamiento de proteínas con las librerías de Fortran originales"
date: "2017-08-07"
categories: 
  - "gnulinux"
  - "trucos"
tags: 
  - "dali"
  - "dalilite"
  - "fortran"
  - "gcc"
  - "libraries"
---

DALI es un programa de comparación de estructuras de proteínas de finales del siglo pasado. A pesar de ser un programa ampliamente usado, el código hace décadas que no ha sido tocado por lo que sigue usando librerías de unos 20 años de antigüedad. Librerías Fortran que ya no están en la versión actual del gcc.

El problema que me daba es:

**error while loading shared libraries: libg2c.so.0: cannot open shared object file: No such file or directory**

Como quería usar este programa tuve que encontrar una solución. Al final lo que **conseguí es instalar una versión antigua de gcc** para poder usar las librerías usando el compilador antiguo de Fortran (gfortran).

Al final encontré la única solución. Consiste en instalar el compilador de GNU y después compilar y ejecutar dalilite usando la versión antigua.

Para empezar nos bajaremos la versión antigua del compilador de GNU, la versión gcc-3.4.6

```
wget https://ftp.gnu.org/gnu/gcc/
```

descomprimiremos el archivo comprimido, y crearemos el directorio dónde pondremos las librerías

```
tar -zxvf gcc-3.4.6.tar.gz
cd gcc-3.4.6
mkdir build
cd build
```

Configuraremos gcc-3.4.6

```
../configure --enable-shared –prefix=/cualquier/directorio --disable-multilib --disable-bootstrap # /cualquier/directorio puede ser por ejemplo /home/roc/herramientas/gcc-3.4.6
```

Ahora hacemos un build y lo instalamos. Esto va a tardar un rato y se instará en el directorio previamente seleccionado

```
make -j 4
make install
```

Ahora que ya tenemos nuestra copia de gcc-3.4.6 instalada en /cualquier/directorio necesitamos hacer las librerías visibles.

```
export PATH=/cualquier/directorio/bin:$
export LD_LIBRARY_PATH=/cualquier/directorio/
```

Ahora dalilite debería funcionar. Recuerda en recompilarlo con el Makefile. Además cada vez que quieras ejecutarlo deberías usar las dos lineas anteriores

Espero que os haya servido!
