---
layout: post
title:  "Roulette Wheel Selection in Python"
date: 2021-03-22 18:19:50 +0000
categories: algorithms python
---


The roulette wheel selection (also known as fitness proportionate selection) is a function used by genetic algorithms for selecting potentially useful solutions for recombination.

The crossover individual probability is computed based on the individual's fitness divided by the sum of all population fitness. The following is the formula for it:

[//]: # (<a href="https://rocreguant.com/?attachment_id=2024" rel="attachment wp-att-2024"><img class="aligncenter size-full wp-image-2024" src="http://rocreguant.com/wp-content/uploads/2021/03/roulette_wheel_chromosome_probability.png" alt="roulette wheel chromosome probability" width="122" height="71" /></a>)
[broken image]

where pi is the probability of each chromosome equals the chromosome frequency divided by the sum of all fitness. Let's imagine that the roulette wheel selection algorithm is like a pie chart. Each individual has a fitness value and the sum of all is the circle. So the probability of selecting a potential mate depends on your fitness with respect to the rest. The following illustration shows the probability of selecting each of them depends on how much space they take in the pie.

[//]: # (<a href="http://rocreguant.com/wp-content/uploads/2021/03/roulette_wheel_selection_example.png"><img class="aligncenter size-full"  src="http://rocreguant.com/wp-content/uploads/2021/03/roulette_wheel_selection_example.png" alt="Roulette wheel selection pie chart example" width="500" height="460" /></a>)
[broken image
]
## Roulette wheel selection in genetic algorithm python

An example of the genetic algorithm roulette wheel selection in python. Easy python implementation without pseudo code.

<script src="https://gist.github.com/rocreguant/b14ab2c2ecb58f98ee44b4d75785b8af.js"></script>

If you desire to apply this genetic algorithm operation as a minimization problem all you have to do is reverse the probabilities of the function. the roulette wheel selection for the minimization problem requires updating the probabilities to 1-prob. Below the python example:

<script src="https://gist.github.com/rocreguant/e9f2481f4e9842dd76e9c61f653eb7c0.js"></script>^M\

I hope that was clear, if not leave a comment and I'll do my best to clarify it.

