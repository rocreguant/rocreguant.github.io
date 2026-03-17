---
title: "Instalando docker en Ubuntu"
date: "2018-02-02"
categories: 
  - "machine-learning"
tags: 
  - "docker"
  - "machine-learning"
  - "manual-2"
  - "tensor-flow"
  - "tutorial"
---

Esa va a a formar parte de una serie de posts. En los que voy a implementar algoritmos de inteligencia artificial en tensor flow. Y porque docker? Docker es un programa que crea virtualizaciones de sistemas operativos con un overhead muy reducido. Las virtualizaciones se llaman containers y requieren pocos recursos para poder virtualizar el entorno correctamente. La ventaja principal es que me permite crear automáticamente una instalación del sistema en cualquier ordenador sin mucho problema. La idea era actualmente hacerlo en el ordenador normal – por lo que seria innecesario usar docker – pero más adelante puede ser que use sistemas externos para realizar los trainings. Además permite separar distintas instalaciones en caso que hayas hecho modificaciones o quieras usar distintas versiones a la vez.

Primero empezaremos instalando la clave GPG oficial de docker

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

y añadiremos el repositorio en nuestras fuentes

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

Seguidamente actualizaremos la lista de paquetes disponibles para nuestra distribución

```
sudo apt-get update
```

y finalmente instalaremos docker (nótese que es docker-ce, las versiones anteriores tenian distintos nombres)

```
sudo apt-get install -y docker-ce
```

para comprobar que la instalación ha finalizado correctamente pondremos en la terminal:

```
sudo docker run hello-world
```

Que nos verificará que la instalación funciona correctamente. Cómo podéis comprobar requiere de sudo para poder usar el _socket TCP_ para comunicarse con el sistema. Si queréis evitar esto. Tendremos que realizar unos pasos extra que _pueden comprometer la seguridad del sistema_.

El primer paso será crear un grupo

```
sudo groupadd docker
```

añadir el usuario al grupo

```
sudo usermod -aG docker $USER
```

para verificar que funciona y podemos evitar el uso de sudo cada vez tendremos que cerrar sesión y volver a logearnos. Una vez dentro ejecutaremos el "hello world" pero esta vez sin el sudo

```
docker run hello-world
```

Si nos sale un "permission denied" significa que algo no ha funcionado. Por el contrario si el comando se ha ejecutado correctamente se imprimirá por pantalla un mensaje algo largo incitandote a usar docker.
