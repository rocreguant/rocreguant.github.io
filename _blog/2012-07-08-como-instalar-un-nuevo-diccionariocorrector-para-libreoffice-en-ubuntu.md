---
title: "Como instalar un nuevo diccionario/corrector para LibreOffice en Ubuntu?"
date: "2012-07-08"
categories: 
  - "gnulinux"
  - "manual"
  - "trucos"
tags: 
  - "consola"
  - "corrector-otrografico"
  - "diccionarios"
  - "libre-office"
  - "terminal"
  - "ubuntu"
---

Todo lo que tienes que hacer para instalar un diccionario para corregir los errores ortográficos en Libre Office. En el caso de Ubuntu se consigue ejecutando el siguiente comando en la consola:

```
sudo apt-get install myspell-<pack de idioma>
```

Dónde <pack de idioma> lo tenemos que sustituir por el idioma que deseamos. Usando el ejemplo anterior para instalar el paquete de español quedaría:

```
sudo apt-get install myspell-es
```

Aunque por ejemplo en catalán en vez de "es" pondríamos "ca". Pueden instalarse muchos idiomas pero en el caso del Alemán, al estar en más de un país se tiene que indicar el país quedando "de-de" (alemán de Alemania) , solo tienes que saber la abreviación del idioma.

Fuente: [http://askubuntu.com/questions/72099/how-to-install-a-libreoffice-dictionary-spelling-check-thesaurus](http://askubuntu.com/questions/72099/how-to-install-a-libreoffice-dictionary-spelling-check-thesaurus)
