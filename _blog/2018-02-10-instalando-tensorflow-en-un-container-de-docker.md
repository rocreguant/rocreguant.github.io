---
title: "Instalando tensorflow en un container de docker"
date: "2018-02-10"
categories: 
  - "machine-learning"
tags: 
  - "docker"
  - "machine-learning"
  - "manual-2"
  - "tensor-flow"
  - "tutorial"
---

Con el docker instalado podremos instalar el tensor flow en un container de docker. Ejecutaremos el siguiente comando para iniciar el container con tensor flow. La primera vez que lo ejecutemos docker se bajará todos los archivos necesarios para poder correr el container, por lo que por lo que puede tardar un poco en estar listo. A partir de la segunda vez ya tendremos todo el software requerido en el ordenador y se ejecutará sin ningún problema.

```
docker run -it -p 8888:8888 gcr.io/tensorflow/tensorflow
```

la opción _\-p 8888:8888_ es usada para conectar el puerto interno de docker con el de la maquina física. Importante si queremos usar Jupyter notebooks. El formato es _hostPort:containerPort._ Y la url _gcr.io/tensorflow/tensorflow_ contiene la imagen binaria para CPU. Hay otra con GPU, y sus respectivas con el código fuente. Aquí dejo una lista por si quieres la imagen con el codigo fuente o usar la versión GPU.

- gcr.io/tensorflow/tensorflow: TensorFlow CPU
- gcr.io/tensorflow/tensorflow:latest-devel: CPU y codigo fuente
- gcr.io/tensorflow/tensorflow:latest-gpu: TensorFlow GPU
- gcr.io/tensorflow/tensorflow:latest-devel-gpu: GPU codigo fuente
