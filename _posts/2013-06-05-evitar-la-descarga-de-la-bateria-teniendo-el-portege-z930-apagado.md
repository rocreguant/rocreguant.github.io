---
title: "Evitar la descarga de la batería teniendo el portege z930 apagado"
date: "2013-06-05"
categories: 
  - "manual"
  - "trucos"
tags: 
  - "bateria"
  - "battery-life"
  - "bios"
  - "portege-z930"
  - "solucion"
  - "ultrabook"
---

Hace ya un tiempo me tenía preocupado ya que mi ultrabook, el problema era que estando **apagado perdía batería** y lo peor es que es relativamente nuevo (con menos de un año).

Buscando por internet en todos los idiomas que conozco y formulando distintas querys a Google y otros buscadores siempre encontraba los comentarios que decían eso es el que tienes el “wake up on lan” activado pero en mi caso no era así, por lo que seguía buscando sin encontrar la solución.

Finalmente opté por algo más a lo bestia para solucionar el problema, cerrar todos los servicios desde la bios que creía que podían consumir energía estando el ordenador apagado.

Para **acceder a la bios en portege z930 se tiene que pulsar F2 al inicio**. Y luego para evitar la descarga de la batería **deshabilité los siguientes servicios**:

De la pestaña de **power management**:

- Wake up on lan (WOL)
    
- Wake up on keyword
    
- Intel turbo boost (no he notado que tarde más al iniciarse)
    
- Intel display power
    

De la pestaña **advanced**:

- Intel rapid start
    
- Sleep and charge (sinceramente creo que esta “feature” era la que me consumia la bateria)
    
- System on CPD charge node
    
- USB Power in sleep mode
    

Antes de terminar comentar que tengo Lubuntu instalado (si con L).
