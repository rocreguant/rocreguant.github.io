---
title: "Como ejecutar una tarea periódicamente en Ubuntu (Linux)"
date: "2015-02-17"
categories: 
  - "gnulinux"
  - "manual"
tags: 
  - "cronjobs"
  - "linux"
  - "ubuntu"
---

**Esta programación periódica de tareas no sirve solamente para el uso en el ordenador personal, si no que también nos puede ser útil en el servidor.** Estas tareas consisten en trabajos que el ordenador tiene que realizar cada determinado periodo de tiempo sin interferir con la interfaz gráfica. Para conseguir tal objetivo todas las distribuciones Linux (incluyendo Ubuntu), y otros sistemas operativos basados en Unix, nos brindan la posibilidad de usar _Crontab_. El nombre proviene del antiguo dios griego Chronos  que era el encargado del tiempo.

Para ver las **tareas que tenemos ejecutándose de forma periódica en nuestro sistema** podremos usar el comando:

```
crontab -l
```

Si queremos modificar el fichero y añadir nuevos _cronjobs_ deberemos usar el comando:

```
crontab -e
```

Este comando nos abrirá nuestro editor por defecto (en mi caso vim). Una vez dentro deberemos escribir una linea parecida a:

```
* * * * * sh /ruta/al/script.sh
```

 y si guardamos tal script será ejecutado regularmente en el margen de tiempo indicado. Cada asterisco representa una unidad de tiempo distinta. Ordenada en:

- minutos ( de 00 a 59)
- horas (de 0 a 23)
- día del mes (de 1 a 31)
- mes (de 1 a 12)
- día de la semana (de 0 a 6) { Se empieza en domingo = 0 }

**Los asteriscos tienen el significado de “todos”**. Por lo que en este ejemplo significa que el script se ejecutará todos los minutos de todas las horas, de todos los días, de todos los meses, de todos los días de las semanas.

Para ejecutarlo el viernes a la 1 de la mañana:

```
0 1 * * 5 sh /ruta/al/script.sh
```

Si queremos ejecutar una tarea en intervalos podemos usar el guión "-". Por ejemplo si queremos ejecutar el script de lunes a viernes pondremos

```
0 1 * * 1-5 sh /ruta/al/script.sh
```

O en intervalos de 10 minutos usaremos las comas para concatenar tiempos

```
0,10,20,30,40,50 * * * * /ruta/al/script.sh
```

 pero también:

```
 */10 * * * * /ruta/al/script.sh
```

Dónde podemos apreciar porciones, evitándonos el uso de comas.

Los asteriscos, o indicaciones de tiempo, se pueden substituir por palabras protegidas.

<table style="width: 100%;"><tbody><tr><td>@reboot</td><td>Se ejecuta una vez al arranque</td><td></td></tr><tr><td>@yearly</td><td>Se ejecuta una vez al año</td><td>"0 0 1 1 *"</td></tr><tr><td>@annually</td><td>(lo mismo que @yearly)</td><td></td></tr><tr><td>@monthly</td><td>Se ejecuta una vez al mes</td><td>"0 0 1 * *"</td></tr><tr><td>@weekly</td><td>Se ejecuta una vez a la semana</td><td>"0 0 * * 0"</td></tr><tr><td>@daily</td><td>Se ejecuta una vez al dia</td><td>"0 0 * * *"</td></tr><tr><td>@midnight</td><td>(lo mismo que @daily)</td><td></td></tr><tr><td>@hourly</td><td>Se ejecuta una vez cada hora</td><td>"0 * * * *"</td></tr></tbody></table>

 

```
*/10 * * * * /ruta/al/script.sh >> /var/log/script_output.log 2>&1
```

 Empezando por el final, **“2>&1” significa que tipo de información deseamos guardar**. El “1” hace referencia al “standard output” y el “2” referencia a los “standard errors”. En el medio vemos “>>” que con solo una flecha significa que el fichero se sobre escribiría pero como lo que queremos es ir guardándolo todo, deberemos poner las dos flechas para que vaya añadiendo las nuevas lineas al final del documento. Tened en cuenta que si el cronjob lo ejecutas a menudo este fichero puede crecer con bastante velocidad causando problemas. Por lo que si queréis desechar lo que salga del script podéis usar

```
*/10 * * * * /bin/execute/this/script.sh > /dev/null 2>&1
```

Dónde “_/dev/null_” es un agujero negro que descarta toda la información que le llega.

Finalmente si queréis hacer limpieza podéis usar el siguiente comando:

```
crontab -r
```

Espero que os haya gustado y os haya servido! :)
