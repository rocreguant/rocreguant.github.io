---
title: "Introducción a TensorFlow"
date: "2017-05-20"
categories: 
  - "analitica"
  - "big-data"
  - "machine-learning"
  - "manual"
  - "programacion"
tags: 
  - "machine-learning"
  - "tensorflow"
---

La web oficial de TensorFlow tiene muy buenos recursos. En esencia lo que hay en este post proviene del "[get started](https://www.tensorflow.org/get_started/get_started)" de la web oficial.

En el primer ejemplo importaremos TensorFlow. Crearemos dos constantes y las imprimiremos en pantalla.

\[code language="python"\] import tensorflow as tf node1 = tf.constant(3.0, tf.float32) node2 = tf.constant(4.0) # También tf.float32 de forma implícita sess = tf.Session() print(sess.run(\[node1, node2\])) node3 = tf.add(node1, node2) print("node3: ", node3) #Esta linea muestra las propiedades del tensor print("sess.run(node3): ",sess.run(node3)) # Aquí se imprime el resultado\[/code\]

También podemos aplicar operaciones a los tensors. Las operaciones producen más tensores. En el siguiente ejemplo sumamos dos variables (tensores) y luego las sumamos. Un tensor es capaz de procesar listas también como veremos.

\[code language="python"\] a = tf.placeholder(tf.float32) b = tf.placeholder(tf.float32) adder\_node = a + b print(sess.run(adder\_node, {a: 3, b:4.5})) # 7.5 print(sess.run(adder\_node, {a: \[1,3\], b: \[2, 4\]})) # Itera sobre la lista: 3 y 7 \[/code\]

Podemos multiplicar

\[code language="python"\] add\_and\_triple = adder\_node \* 3. print(sess.run(add\_and\_triple, {a: 3, b:4.5})) \[/code\]

E incluso podemos crear modelos lineales

\[code language="python"\] W = tf.Variable(\[.3\], tf.float32) b = tf.Variable(\[-.3\], tf.float32) x = tf.placeholder(tf.float32) linear\_model = W \* x + b \[/code\]

Las constantes son inicializadas con _tf.constant_, y su valor no puede ser cambiado. Contrariamente las variables son creadas usando tf.Variable y no son inicializadas en el inicio. Para inicializar las variables  tenemos que usar una función especial como en el siguiente ejemplo:

\[code language="python"\] init = tf.global\_variables\_initializer() sess.run(init) \[/code\]

Lo importante es usar init. Es un "handle" que inicia el grafo, inicializando las variables que hasta entonces habían permanecido sin inicializar.

Ya que la X es la variable podemos evaluar el modelo usando distintos valores simultáneamente de la siguiente manera:

\[code language="python"\] print(sess.run(linear\_model, {x:\[1,2,3,4\]})) # Output: \[ 0, 0.30000001, 0.60000002, 0.90000004\] \[/code\]

La función de pérdida (loss function) puede medir la distancia entre el modelo actual y los datos proporcionados. Usaremos la función de pérdida estándar para hacer una regresión lineal que sume los cuadrados de las distancias entre el modelo actual y los datos. El modelo crea un vector en el que cada posición corresponde a una distancia de error. Cuando usamos tf.square estamos elevando al cuadrado el error. Luego sumamos los errores para crear un simple escalar que abstrae el error de todos los puntos usando tf.reduce\_sum:

\[code language="python"\] y = tf.placeholder(tf.float32) squared\_deltas = tf.square(linear\_model - y) loss = tf.reduce\_sum(squared\_deltas) print(sess.run(loss, {x:\[1,2,3,4\], y:\[0,-1,-2,-3\]})) \[/code\]

El valor producido es:  23.66

Podríamos mejorar el modelo manualmente asignando nuevos valores a W para obtener resultados perfectos de -1 y 1. Una variables es inicializada por el valor proporcionado por tf.Variable pero puede ser cambiada si usamos operaciones como tf.assign. Por ejemplo, W=-1 y b=1 son los parámetros óptimos de nuestro modelo. Podemos cambiar W y b acordemente:

\[code language="python"\] fixW = tf.assign(W, \[-1.\]) fixb = tf.assign(b, \[1.\]) sess.run(\[fixW, fixb\]) print(sess.run(loss, {x:\[1,2,3,4\], y:\[0,-1,-2,-3\]}) #resultado: 0 \[/code\]

Hemos adivinado el valor perfecto para W i b aunque este no es el objetivo de  machine learning. El objetivo es encontrar los parámetros correctos para el modelo automáticamente. Pero esto lo vais a encontrar en la próxima entrega ;)

_**Bonus:** En matemáticas y en física, un tensor es cierta clase de entidad algebraica de varias componentes, que generaliza los conceptos de escalar, vector y matriz de una manera que sea independiente de cualquier sistema de coordenadas elegido. ( [wikipedia](https://es.wikipedia.org/wiki/C%C3%A1lculo_tensorial) )_
