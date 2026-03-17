---
title: "He intentado hacer como Moneyball para predecir el resultado de los partidos de fútbol y he fracasado"
date: "2016-12-15"
categories: 
  - "analitica"
  - "investigacion"
  - "programacion"
tags: 
  - "data-mining"
  - "data-scientist"
  - "futbol"
  - "moneyball"
---

Hace ya algún tiempo leí un post interesante sobre como [un data scientist usó el concepto presentado en el libro Moneyball para escoger mejor los jugadores del FIFA 2016](https://arybressane.github.io/playing-moneyball-on-ea-fifa-16/) cuando jugaba con “Career Mode”. El concepto de Moneyball es básicamente hacer data mining para conseguir el mejor equipo de béisbol con el menor precio. El argumento principal del libro es que al fichar los jugadores de béisbol las personas usan sus propios inclinaciones que normalmente no coinciden con la realidad o que están ancladas al pasado. Como ejemplo en el libro pone que a menudo el resultado de una táctica ofensiva de un jugador se puede medir mejor usando la frecuencia con que el bateador llega a la base en vez de la velocidad con la que batea. La velocidad de bateo ha sido la métrica que se ha usado des del principio pero después de un análisis detallado los analistas descubrieron que otras métricas son más relevantes.

A partir de este concepto [creé mi propio experimento](https://github.com/rocreguant/fifa-players-database). La idea era que normalmente los analistas usan datos reales de los partidos para definir la habilidad del jugador. El problema que tiene esto es que lo que se luce el jugador depende del nivel del contrincante. Por eso mi idea era usar una valoración más o menos neutra y absoluta para predecir la calidad de cada jugador. Estas métricas las usaría para predecir la calidad del once inicial y así poder determinar el resultado final del partido.

Lo primero que hice fue recopilar tanta información como pude de todos los jugadores que pude. Para determinar la [calidad del jugador usé la que usan en el videojuego FIFA 2015](http://www.futhead.com/15/career-mode/players/all/all/all/all/all/all/all/all/all/rating/cards/). El valor de las apuestas que se habían hecho en distintos sitios web de apuestas lo saqué de [football-data](http://www.football-data.co.uk/matches.php). La alineación inicial y el resultado final del partido lo saqué de [11v11](http://www.11v11.com/competitions/premier-league/2016/matches/).

Todo el scrapping que hice puede sonar muy divertido y rápido pero no fue así. Durante el proceso pasé por alto varias cosas importantes. Lo primero es que en la liga española tenemos muchos jugadores españoles y con nombres españoles. El problema de los nombres españoles es que usan caracteres especiales como acentos o la ñ causando problemas con el encoding. El segundo problema es que el scrapping es divertido si la página web es consistente y está bien ordenada. Resultó no ser el caso. Por algún motivo que desconozco algunas de las páginas de la web no tenían un formato consistente con el resto de la web y tuve que programar excepciones. El tercer y último punto es que las webs de dónde extraje la información tenían herramientas para evitar el scrapping. Por suerte no eran muy estrictos con el número de peticiones que un mismo ordenador podía hacer y conseguí toda la información que buscaba en relativamente poco tiempo.

El resultado final fue que no funcionó. Me pareció una idea innovadora pero quizás no muy realista. El fútbol se ha caracterizado por las sorpresas. Usando sólo la información de las apuestas puedo predecir en un 50% cual será el resultado final del partido. Curiosamente con regresión lineal y toda la información de los jugadores se puede predecir también con un 50% quién será el ganador del partido. Si quitamos el empate de la ecuación todos los algoritmos que probé siguen funcionando igual de “bien”. Básicamente podría tirar una moneda en el aire y decir que cara gana el equipo local y cruz el visitante y acertaría el mismo número de veces que todos los algoritmos probados. Una pena que no funcionara pero me alegra haberlo probado.
