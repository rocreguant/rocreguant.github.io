---
title: "Optimizadores de tensor flow"
date: "2017-10-03"
categories: 
  - "analitica"
  - "big-data"
  - "machine-learning"
  - "manual"
tags: 
  - "analitica-2"
  - "big-data"
  - "machine-learning"
  - "manual-2"
  - "programacion-2"
  - "tensorflow"
---

Continuando el [anterior post dónde introducí tensor flow](http://rocreguant.com/introduccion-a-tensorflow/1093/) hoy vengo con los optimizadores de funciones. Tensor flow ofrece optimizadores que cambian las variables para minimizar la funcion de perdida (loss function). El más simple es el de gradiente descendiente. Computan las derivadas simbólicas (symbolic derivatives) simplemente usando el modelo y la función tf.gradients. Por ejemplo:

\[code language="python"\] optimizer = tf.train.GradientDescentOptimizer(0.01) train = optimizer.minimize(loss) sess.run(init) # reset values to incorrect defaults. for i in range(1000): sess.run(train, {x:\[1,2,3,4\], y:\[0,-1,-2,-3\]}) print(sess.run(\[W, b\])) los resultados finales \[array(\[-0.9999969\], dtype=float32), array(\[ 0.99999082\], dtype=float32)\] \[/code\]

El modelo completo para la regresión linal es:

\[code language="python"\] import numpy as np import tensorflow as tf # Model parameters W = tf.Variable(\[.3\], tf.float32) b = tf.Variable(\[-.3\], tf.float32) # Model input and output x = tf.placeholder(tf.float32) linear\_model = W \* x + b y = tf.placeholder(tf.float32) # loss loss = tf.reduce\_sum(tf.square(linear\_model - y)) # suma de los cuadrados # optimizer optimizer = tf.train.GradientDescentOptimizer(0.01) train = optimizer.minimize(loss) # training data x\_train = \[1,2,3,4\] y\_train = \[0,-1,-2,-3\] # training loop init = tf.global\_variables\_initializer() sess = tf.Session() sess.run(init) # reset values to wrong for i in range(1000): sess.run(train, {x:x\_train, y:y\_train}) # evaluate training accuracy curr\_W, curr\_b, curr\_loss  = sess.run(\[W, b, loss\], {x:x\_train, y:y\_train}) print("W: %s b: %s loss: %s"%(curr\_W, curr\_b, curr\_loss)) # When run, it produces #W: \[-0.9999969\] b: \[ 0.99999082\] loss: 5.69997e-11 \[/code\] tf.contrib.learn te simplifica la vida con las funciones: ejecución, entrenamiento, iteraciones, evaluaciones entre otros

\[code language="python"\] import tensorflow as tf import numpy as np features = \[tf.contrib.layers.real\_valued\_column("x", dimension=1)\] estimator = tf.contrib.learn.LinearRegressor(feature\_columns=features) x = np.array(\[1., 2., 3., 4.\]) y = np.array(\[0., -1., -2., -3.\]) input\_fn = tf.contrib.learn.io.numpy\_input\_fn({"x":x}, y, batch\_size=4, num\_epochs=1000) estimator.fit(input\_fn=input\_fn, steps=1000) print(estimator.evaluate(input\_fn=input\_fn)) # Result: {'global\_step': 1000, 'loss': 1.9650059e-11} \[/code\]
