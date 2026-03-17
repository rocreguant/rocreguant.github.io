---
title: "▷ Como ver los comentarios y anotaciones de documentos PDF"
date: "2015-04-28"
categories: 
  - "gnulinux"
  - "manual"
---

Los comentarios en pdf no siempre estan visibles o no es fácil visualizarlos en cualquier sistema operativo. Si un pdf tiene comentarios normalmente los veremos como si fueran un globo de dialogo tipicamente amarillo tal y como se ve en la siguiente figura

![Globo de diálogo de un comentario en un pd](images/Screen-Shot-2020-11-08-at-11.06.12.png)

Si ponemos el cursor encima veremos lo que hay escrito en la nota adhesiva. Si el texto se ve cortado o queremos editarlo o añadir comentarios podemos hacer doble click en la nota y se nos abrirá una ventana que podremos con todo el texto y sus comentatios como la siguiente

![Comentario en un pdf con ventana de texto](images/Screen-Shot-2020-11-08-at-11.12.52.png)

Si lo queremos editar podemos hacer doble click sobre el comentario y cambiarlo. Por lo contrario si queremos añadir un comentario lo podemos hacer directamente en el cuadro de texto vacío directamente debajo del texto.

### Para usuarios de Linux (Ubuntu)

El visualizador de documentos de Adobe para Linux no es muy avanzado. Básicamente lo que nos permite es simplemente “visualizar” el documento y no ofrece otras funcionalidades que aporta a otros sistemas operativos. Una de esta funcionalidad es la de visualizar anotaciones (simplemente se ve el subrayado).

Indagando un poco por la web he encontrado la solución. Lamentablemente no es una aplicación nativa para Ubuntu (las existentes al parecer solo muestran el documento), por lo que se tiene que hacer cosas un poco raras para ver las anotaciones. Así lo he solucionado yo:

**Instalar Wine** (aplicación nativa para Ubuntu que simula los procesos Windows para poder ejecutar programas que solo funcionan en Windows).

Si intentamos instalar Adobe PDF en Wine no nos va a funcionar (ninguna de las versiones). Por lo que tuve que encontrar otra aplicación. La aplicación que recomiendo es “**PDF-XChange Viewer**” tiene una versión pro (de pago) y una free. Para lo que necesitaba con la gratis me bastaba. Lo instalas y abres el documento abriendo primero el programa y luego yendo a buscar el archivo.

Espero que haya servido! :)
