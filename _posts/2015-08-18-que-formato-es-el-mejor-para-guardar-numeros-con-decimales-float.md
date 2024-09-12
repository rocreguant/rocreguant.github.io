---
title: "Que formato es el  mejor para guardar números con decimales (float)?"
date: "2015-08-18"
categories: 
  - "analitica"
  - "big-data"
  - "investigacion"
  - "programacion"
  - "scripts"
tags: 
  - "comparacion"
  - "csv"
  - "formato-de-fichero"
  - "hdf5"
  - "json"
  - "script"
  - "sqlite"
  - "texto-plano"
  - "tsv"
---

Hace ya algunos días que le estoy dando vueltas al crear un script que me cogiera determinados datos y los fuera guardando en un archivo. Como quiero guardar muchos datos durante un largo periodo de tiempo he pensado que quizás debería empezar por lo básico. Que formato de archivo es mejor para almacenar este tipo de datos.

Para averiguar que formato es el ideal para tal propósito he ideado un script en python que lo que hace es generar cuatro números aleatorios entre -10 y 10 por cada una de las 100.000 hileras disponibles (en total 400.000 valores). Luego, usando el mismo data set, he almacenado esta información usando distintos formatos. Los formatos que he usado son texto plano, CSV, TSV, JSON, SQLite y HDF5. Estos formatos son los que me han parecido adecuados para este tipo de tarea. He dejado fuera XML porque me pareció que tiene gran similitud con JSON y realmente no necesito la jerarquía ni flexibilidad que este formato me ofrece.

Véase que el mismo script indica el tamaño de cada fichero. El tiempo de ejecución es de unos 65 segundos en mi laptop.

## El script:

\[code language="python"\]

import numpy as np import os from os import listdir from os.path import isfile, join

import json import csv import sqlite3 import h5py #pip install h5py

#generated 4 rows with number\_of\_floats data def data\_generation(number\_of\_floats): ret = np.ndarray((number\_of\_floats, 4)) for i in range(number\_of\_floats): ret\[i\] = np.random.uniform( -10, 10, 4 ) return ret

#standard text saving def save\_text\_file(data): f = open('text.txt', 'w') for el in data: f.write(str(el).strip('\[\]')) f.write('\\n') f.close() return True

#saving with json files def save\_json(data): f = open('json.json', 'w') j=json.dumps(data.tolist()) json.dump(j, f) f.close() return True

#saving numbers on csv def save\_csv(data): with open('csv.csv', 'w') as csvfile: fieldnames = \['Col\_A', 'Col\_B', 'Col\_C', 'Col\_D'\] writer = csv.DictWriter(csvfile, fieldnames=fieldnames) for el in data: writer.writerow({'Col\_A': str(el\[0\]), 'Col\_B': str(el\[1\]),'Col\_C': str(el\[2\]),'Col\_D': str(el\[3\])}) return True

#Tab Separated Values (TSV) def save\_tsv(data): with open('tsv.tsv', 'w') as tsvfile: writer = csv.writer(tsvfile, delimiter='\\t') for el in data: writer.writerow(el) return True

#save data in sqlite def save\_sqlite(data): conn = sqlite3.connect('data.sqlite3') cur = conn.cursor() cur.execute('DROP TABLE IF EXISTS Data ') cur.execute('CREATE TABLE Data (Col\_A REAL, Col\_B REAL, Col\_C REAL, Col\_D REAL)') for el in data: cur.execute('INSERT INTO Data VALUES ('+str(el\[0\])+', '+str(el\[1\])+', '+str(el\[2\])+', '+str(el\[3\])+')') conn.commit() conn.close()

#save the data in a hdf file def save\_hdf(data): h = h5py.File('data.hdf5', 'w') dset = h.create\_dataset('data', data=data)

#check the file size def show\_file\_size(): mypath = '.' onlyfiles = \[ f for f in listdir(mypath) if isfile(join(mypath,f)) \] for fil in onlyfiles: statinfo = os.stat(fil) print 'name: '+str(fil) print 'size: '+str(statinfo.st\_size) print ' ' print onlyfiles

############################## # # Main # ##############################

data = data\_generation(100000) save\_text\_file(data) save\_csv(data) save\_json(data) save\_csv(data) save\_tsv(data) save\_sqlite(data) save\_hdf(data) show\_file\_size() print 'Done'

\[/code\]

## Finalmente los resultados:

[![data-format-comparsion-plot](images/data-format-comparsion-plot.png)](http://rocreguant.com/wp-content/uploads/2015/08/data-format-comparsion-plot.png)

| Formato | Tamaño (Bytes) |
| --- | --- |
| Texto plano | 4806060 |
| CSV | 5900742 |
| TSV | 7901330 |
| JSON | 8109034 |
| SQLite | 4468736 |
| HDF5 | 3202144 |

Como se puede observar HDF5 es el ganador claramente siendo casi un 30% menor en tamaño que Sqlite que está ocupando el segundo lugar. No es de extrañar puesto que HDF es un formato de fichero diseñado especialmente para organizar y almacenar grandes cantidades de datos (ideado para supercomputadores). Para nuestra suerte las librerías tienen licencia BSD permitiendo mejoras y creación aplicaciones por parte de terceros. Lo que no me esperaba es que TSV obtuviera un tamaño similar a JSON y no a CSV. Sinceramente pensaba que CSV y TSV eran básicamente lo mismo.

_**Bonus:** Para los interesados [el script está en github](https://github.com/rocreguant/I-have-time/blob/master/number-storage.py)._
