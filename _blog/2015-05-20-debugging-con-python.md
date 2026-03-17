---
title: "Debugging con python"
date: "2015-05-20"
categories: 
  - "programacion"
  - "trucos"
---

Para hacer debugging en python normalmente pongo prints pero a medida que el código crece los prints aumentan en número y al final me paso un buen rato buscando los sitios dónde los tengo. Por lo que al final he implementado una solución en la que puedes imprimir la linea y el mensaje deseado.

Lo que hace simplemente es usar el numero de linea que nos da la librería “inspect”. Aquí el código:

```
import inspect

def debug(message):
    print 'Debug in line', inspect.currentframe().f_back.f_lineno,':'
    print message

if __name__ == '__main__':
    debug('message')
    print '.'
    print '.'
    debug('message2')
```
