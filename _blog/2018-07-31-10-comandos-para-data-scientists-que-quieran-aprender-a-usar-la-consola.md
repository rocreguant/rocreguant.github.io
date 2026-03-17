---
title: "11 comandos para data scientists que quieran aprender a usar la consola"
date: "2018-07-31"
categories: 
  - "analitica"
  - "big-data"
  - "scripts"
tags: 
  - "awk"
  - "big-data"
  - "comandos"
  - "consola"
  - "cut"
  - "data-mining"
  - "grep"
  - "head"
  - "paste"
  - "sed"
  - "sort"
  - "split"
  - "terminal"
  - "tr"
  - "uniq"
  - "wc"
---

Algunas veces manipular datos puede resultar costoso. A menudo los data scientists tenemos que manipular grandes cantidades de datos por lo que es bueno conocer algunos tranquillos para optimizar el proceso. Aquí os dejo unos cuantos comandos con algunas opciones para trabajar más eficientemente.

### head

```
head archivo.txt
```

Este comando imprime las 10 primeras lineas del archivo. Si queremos un numero distinto de lineas podemos usar la opción -n.

```
head -n 20 archivo.txt
```

Este último comando nos imprimirá las 20 primeras lineas del archivo. Al imprimir las primeras lineas de un fichero en pantalla nos ayuda a obtener la estructura global del archivo y algunos valores para hacernos una idea general del contenido del archivo.

### tr

Este comando es perfecto para pre-procesar archivos. Por ejemplo podemos cambiar el archivo de tsv a csv.

```
cat tab_delimited.txt | tr "\\t" "," comma_delimited.csv
```

Algo muy interesante de "tr" son las clases. Las clases son funciones de elementos algo más "abstractos". Aquí una lista de algunos:

```
[:alnum:] todas las letras y dígitos
[:alpha:] todas las letras
[:blank:] todos los espacios
[:digit:] todos los dígitos
[:lower:] todas las letras minúsculas
[:upper:] todas las letras mayúsculas
[:punct:] todos los caracteres de puntuación
```

y si los concatenas puedes hacer un script bastante interesante. También puedes usar las expresiones regulares. Aquí ejemplo para pasar de mayúsculas a minúsculas

```
cat filename.csv | tr '[A-Z]' '[a-z]'
```

### wc

Este es un contador de palabras (word count). Basado en mi experiencia uso la opción -l a menudo. Esta opción cuenta el número de lineas en vez de palabras. Otras opciones

- **_wc -m_** imprimer el recuento de caracteres
- _**wc -L**_ imprime la longitud de la linea más larga
- **_wc -w_** cuenta el numero de palabras
- **_wc - l_** cuenta lineas

### split

Nos permite trocear archivos fácilmente para reducir su tamaño. El problema es que no añade la extensión del fichero a los nuevos documentos. Podemos trocear un fichero cada 500 lineas con el siguiente comando.

```
split -l 500 fichero.csv nuevo_fichero_
```

Si queremos poner una extensión a los nuevos ficheros tendremos que usar el siguiente comando en el directorio del output

```
find . -type f -exec mv '{}' '{}'.csv \;
```

Si queremos numerar los archivos partidos tendremos que usar **el flag -d para indicar que el sufijo sea numérico**.

### uniq

Uniq solo opera con lineas contiguas idénticas. Motivo por el cual es interesante añadir el sort antes. El sort nos pone lineas idénticas contiguamente.

### sort

```
# Ordenando la segunda columna alfabéticamente
sort -t, -k2 filename.csv
```

```
# Numericamente 
sort -t, -k2n filename.csv
```

```
# Orden inverso 
sort -t, -k2nr filename.csv
```

- _**sort -f**_ ignora el caso
- _**sort -r**_ ordena inversamente
- **_sort -k_** especifica el identificador
- _**sort -t**_ usa la coma como separador
- **_sort -R_** mezcla el orden
- **_uniq -c_** cuenta el numero de apariciones
- **_uniq -d_** solo imprime las lineas duplicadas

### cut

Sirve para eliminar ciertas columnas en el archivo. Por ejemplo si nos queremos quedar con la primera y tercera columna

```
cut -d, -f 1,3 filename.csv
```

Pero si queremos todas las columnas menos la primera

```
cut -d, -f 2- filename.csv
```

puede servir perfectamente con otros comandos.

### paste

este comando puede ser interesante ya que pone juntamente dos archivos. No pone uno al final del siguiente sino cada fila de lado.

Si tenemos dos ficheros

```
# names.txt 
adam 
john 
zach
```

y

```
# jobs.txt 
lawyer 
youtuber 
developer
```

Los podemos juntar usando el comando

```
# Join the two into a CSV 
paste -d ',' names.txt jobs.txt > person_data.txt
```

Consiguiendo el resultado

```
# Output 
adam,lawyer 
john,youtuber 
zach,developer
```

### grep

Este es uno de los comandos mas famosillos en el mundillo y extremadamente poderoso. Grep busca expresiones regulares y las imprime. Es usado a menudo juntamente con otros comandos.

```
# Buscar recursivamente nombres de ficheros que contengan la palabra "word"
grep -lr 'word' .
```

Algunas opciones interesantes

- **_alias grep="grep --color=auto"_** hace grep más colorido
- **_grep -E_** usa la versión extendida de las expresiones regulares
- **_grep -w_** busca un mach completo de la palabra
- **_grep -l_** imprme el nombre de los ficheros conteniendo la palabra
- g**_rep -v_** invierte el match

### sed

Este comando también es uno de los más potentes. Trabaja linea a linea. La función más básica es _**s/old/new/g**_ . Podemos eliminar las comas de los miles en un fichero csv

```
sed -i '' 's/\([0-9]\),\([0-9]\)/\1\2/g' data.txt 
# balance,name 
# 1000,john 
# 2000,jack
```

o eliminar una linea especifica

```
sed -i '' '/jack/d' data.txt 
# balance,name 
# 1000,john
```

### awk

Este también es un comando de los más usados y el último de hoy. Tiene bastantes de las funcionalidades de grep en su ultima versión.

```
awk '/word/' filename.csv
```

En el siguiente ejemplo awk imprime la 3a y 4a columna de las filas que contengan la palabra word.

```
awk -F, '/word/ { print $3 "\t" $4 }' filename.csv
```

Es capaz de usar múltiples expresiones numéricas

```
# Print line number and columns where column three greater 
# than 2005 and column five less than one thousand
awk -F, ' $3 >= 2005 && $5 <= 1000 { print NR, $0 } ' filename.csv
```

puede hacer un sumatorio de las columnas para las filas que cumplan cierta condición

```
awk -F, '$1 == "something" { x+=$3 } END { print x }' filename.csv
```

Puede imprimir filas duplicadas

```
awk -F, '++seen[$0] == 2' filename.csv
```

O borrar duplicados

```
# lineas consecutivas
awk 'a !~ $0; {a=$0}']
```

```
# Lineas no consecutivas
awk '! a[$0]++' filename.csv
```

```
# Más eficiente
awk '!($0 in a) {a[$0];print}
```

Substituir valores usando gsub

```
awk '{gsub(/scarlet|ruby|puce/, "red"); print}'
```

Fuente: [https://www.kdnuggets.com/2018/06/command-line-tricks-data-scientists.html](https://www.kdnuggets.com/2018/06/command-line-tricks-data-scientists.html)
