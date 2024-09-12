---
title: "Introducción a la implementación continua o Continuous Deployment"
date: "2013-08-07"
categories: 
  - "programacion"
tags: 
  - "automatico"
  - "implementacion-continua"
  - "lean"
  - "produccion"
  - "tests-unitarios"
---

Hace poco di con el blog de [Timothy Fitz](http://timothyfitz.com/) principalmente porqué era citado en [libro Lean Startup de Eric Ries](http://rocreguant.com/resena-del-libro-the-lean-startup-de-eric-ries/554/)  ya que explicaba en método de implementación continua de software. Considero y supongo que Eric Ries también que están ligados con los métodos Lean en las empresas.

**La implementación continua consiste en que cada vez que se haga un commit el sistema ejecutará los tests anteriormente desarrollados sobre una copia real de los datos para comprobar que el trozo de código no contiene ningún error.** Si es así luego se pasan a producción automáticamente.

Lo que menciona Timothy es que pasan el código a producción pero sólo para una porción de los usuarios durante X tiempo, si pasado ese tiempo no genera problemas el código se extenderá a todos los usuarios.

Los tests tienen que ser de tres tipos para asegurar la integridad de la aplicación. Los **tests unitarios**, son la base de la pirámide y de los que debería haber más. Luego están los **tests de integración** que pretenden encontrar problemas con otras partes del software o con otro software y los **tests de interfaz** (GUI) que son los minoritarios pero también son necesarios.

El objetivo de todo esto es **tener un repositorio con todo el código** y que **los commits se hagan a diario** evitando que los desarrolladores hagan piezas inmensas que luego no funcionen. También se pretende que se **automatice la implementación** desarrollando a más velocidad y **comprobando siempre la fiabilidad** en datos reales y **obteniendo un feedback** rápido de integraciones conflictivas, conflictos de integración y demás problemas habituales.

Todos los puntos anteriores juntos permiten **ver los resultados** de cualquier implementación además de tener siempre las **últimas piezas de código funcionales** “a mano”.

Como contrargumentos, o desventajas, se tiene que preparar el entorno antes de empezar, esto conlleva un **“elevado” coste en tiempo de implementación y de desarrollo de tests**.

_**Bonus:** Os dejo los links en inglés todo, de dónde he sacado la información para si queréis leéroslo vosotros. [Continuous integration](http://en.wikipedia.org/wiki/Continuous_integration) , [Getting Started with Continuous Deployment]( http://timothyfitz.com/2012/11/25/paths-to-continuous-deployment/) , [Scaling Up Continuous Deployment](http://timothyfitz.com/2012/12/03/scaling-up-continuous-deployment/)  y [Continuous Deployment at IMVU: Doing the impossible fifty times a day](http://timothyfitz.com/2009/02/10/continuous-deployment-at-imvu-doing-the-impossible-fifty-times-a-day/)_
