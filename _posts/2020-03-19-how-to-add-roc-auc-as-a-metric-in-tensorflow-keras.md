---
title: "How to add ROC AUC as a metric in Tensorflow / Keras"
date: "2020-03-19"
categories: 
  - "scripts"
---

The way to **add the ROC AUC as a metric on your Tensorflow / Keras** project is to copy this function that computes the ROC AUC and use the function name in the model. The function only requires a little customized tf code.

<script src="https://gist.github.com/rocreguant/c6430501efd9c74838c51a59f81f0a96.js"></script>

To use the function in the model. We first need to compile with the function passed directly and not a string (as it is shown in the example below).

<script src="https://gist.github.com/rocreguant/6c76ec9e20d8f6897d5dbf4ed523e677.js"></script>

Then we can use it in the callbacks but we need to refer to it as a string (so this time between the "" as shown in the snippet below).

<script src="https://gist.github.com/rocreguant/7122cac139593e56d9715ea61671b9c8.js"></script>

Other customized functions follow the same pattern.

The function **tf.keras.metrics.AUC already implements the Area Under the Curve natively in TensorFlow in the Keras module**. You can **[check the documentation](https://www.tensorflow.org/api_docs/python/tf/keras/metrics/AUC)** for further information in this regard.
