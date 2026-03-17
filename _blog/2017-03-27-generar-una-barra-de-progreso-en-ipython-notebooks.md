---
title: "Generar una barra de progreso en ipython notebooks"
date: "2017-03-27"
categories: 
  - "manual"
  - "programacion"
tags: 
  - "barra-de-progresso"
  - "ipython-notebooks"
  - "jupyter"
  - "programacion-2"
  - "python"
---

Manual con [código para generar una barra de progreso](https://github.com/rocreguant/I-have-time/blob/master/progress-bar.ipynb) en nuestro código para saber en que porcentaje de compleción estamos sin llenar el output con números. Muchos de los que usáis jupyter (el nuevo ipython notebooks) podéis imprimir por pantalla la iteración en la que vuestro loop reside. Eso es solo posible para una cantidad pequeña de iteraciones. Cuando llegamos a varios miles se puede generar un output bastante engorroso. Googleando un poco encontré la solución. Este código nos genera una clase que luego podemos llamar para obtener la barra de progreso junto con el porcentaje completado.

\[code language="python"\] import sys, time try:     from IPython.core.display import clear\_output     have\_ipython = True except ImportError:     have\_ipython = False

class ProgressBar:     def \_\_init\_\_(self, iterations):         self.iterations = iterations         self.prog\_bar = '\[\]'         self.fill\_char = '\*'         self.width = 40         self.\_\_update\_amount(int(0))         if have\_ipython:             self.animate = self.animate\_ipython         else:             self.animate = self.animate\_noipython

    def animate\_ipython(self, iter):         try:             clear\_output()         except Exception:             # terminal IPython has no clear\_output             pass         print '\\r', self,         sys.stdout.flush(),         self.update\_iteration(iter + 1)              def update\_iteration(self, elapsed\_iter):         self.\_\_update\_amount((elapsed\_iter / float(self.iterations)) \* 100.0)         self.prog\_bar += '  %d of %s complete' % (elapsed\_iter, self.iterations)

    def \_\_update\_amount(self, new\_amount):         percent\_done = int(round((new\_amount / 100.0) \* 100.0))         all\_full = int(self.width - 2)         num\_hashes = int(round((percent\_done / 100.0) \* all\_full))         self.prog\_bar = '\[' + self.fill\_char \* num\_hashes + ' ' \* (all\_full - num\_hashes) + '\]'         pct\_place = int((len(self.prog\_bar) / 2) - len(str(percent\_done)))         pct\_string = '%d%%' % percent\_done         self.prog\_bar = self.prog\_bar\[0:pct\_place\] + \\             (pct\_string + self.prog\_bar\[pct\_place + len(pct\_string):\])

    def \_\_str\_\_(self):         return str(self.prog\_bar)         

\[/code\]

Y el siguiente código vemos un ejemplo de como llamaremos la clase para obtener la funcionalidad deseada

\[code language="python"\] c = ProgressBar(1000) for i in range(1000):     c.animate\_ipython(i) \[/code\]

Para los interesados encontré el código [aquí](https://github.com/ipython/ipython/issues/1527/).
