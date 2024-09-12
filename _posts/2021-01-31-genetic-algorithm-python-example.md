---
title: "Genetic Algorithm Python Example"
date: "2021-01-31"
categories: 
  - "programming"
---

Genetic Algorithms (GA) are a subclass of evolutionary algorithms that emulate natural evolution. Darwin's theory on natural selection states that the fittest individuals are the ones which reproduce. Following this theory, genetic algorithms are composed of three main phases: selection, reproduction, and mutation that attempt to copy the working mechanisms of nature. Genetic algorithms are principally used to find the global optimal solution heuristically.

## Genetic Algorithm Applications

Genetic algorithms have been applied to many different problems in a wide spectrum of industries. This set of algorithms are widely used by computer science students to solve problems like the **travel salesman problem** (TSP) or the **knapsack problem** but it is widely used in many fields. All of the following points are also **evolutionary algorithms applications** since they are a bigger set of genetic algorithms.

- In finance portfolio optimization for [real options analysis](https://www.sciencedirect.com/science/article/abs/pii/S0167923610002344) where the authors achieved significant improvements to previous algorithms.

- The airlines implemented a genetic algorithm for [terminal booking](https://dl.acm.org/doi/10.1145/2345396.2345426) in order to improve the decision-making process.

- The authors in this research they use it to find [the best parameters for recurrent neural networks](http://arimaa.com/arimaa/about/Thesis/). Also within computer science other groups have researched the use of [genetic algorithms for feature selection](https://www.kdnuggets.com/2017/11/rapidminer-evolutionary-algorithms-feature-selection.html) with improved outcomes.

## Genetic Algorithm Steps

To program the whole genetic algorithm from scratch in python can be intimidating. Therefore, we'll go through the genetic algorithm step by step. The next figure shows the other of each of the tasks involved to implement the full ga algorithm.

\[caption id="attachment\_1985" align="aligncenter" width="640"\][![Genetic algorithm state diagram](images/genetic-algorithm-steps.jpg)](https://rocreguant.com/wp-content/uploads/2021/01/genetic-algorithm-steps.jpg) Genetic algorithm step by step flow chart.\[/caption\]

### 1\. Start

First, randomly define N possible solutions to the problem. The first thing to do is to randomly generate solutions to the problem. They don't need to be the best or follow any particular pattern, they will be the seed upon which later the best solution will be found. If you feel confident, you can try to create the initial set of possible solutions in the region where the optimal solution may be found. Instead of generating the solutions randomly, you can try to provide pseudo-random guesses on which may be the ideal solution. If you overdo it you may get stuck in the local optima instead of the global best solution.

### 2\. Fitness Evaluation

With a set of N possible solutions is time to evaluate each of them individually and assess the fitness one by one. Fitness is a metric that represents how well each of the individual solutions performs for our model. If a solution is looking nice and well-optimized the fitness will be high whereas a wrong solution will have a low score. However, sometimes we may want to search for the minimal value of the function. If we have a minimization problem, then the best solution will be the one with the lowest value.

### 3\. Progenitors selection

Based on the previously computed fitness the progenitors are selected. The higher fitness an individual solution has the higher the probabilities it has to mate and produce offspring (descendants). We simply need to select a set of progenitors based on their mating probability. The selection process is executed as many times as necessary until we obtain enough progenitors to produce N kids to replace the original set of N solutions. It should be noticed that each progenitor can mate more than once and with different partners. To select the parents there are several strategies (sorted from most to least common):

#### Roulette Wheel Selection

The [roulette wheel is a selection method](https://rocreguant.com/roulette-wheel-selection-python/2019/) based on fitness probabilities. So, to do that you need to add up all the fitness metrics for each of the solutions and give each solution a probability of being chosen so that probability is individual\_fitness/total\_fitness.

#### Rank Selection

As the name indicates one should rank the solutions using the fitness function from worse to best. Then number them so that the worse is 1, the second worse is 2, etc. Then we add up these numbers and compute the probability as before individual\_rank/sum\_ranks.

#### Tournament Selection

This selection strategy is slightly longer. We randomly select a subset of solutions and pick the best enough times as solutions we need. Notice that if the subset has a size of 1 we're effectively picking at random.

### 4\. Mating or reproduction

Two different solutions are expected to mate. For simplicity here we will assume that reproduction is done between two solutions although there seems to be [evidence](https://link.springer.com/chapter/10.1007/3-540-58484-6_252) that more progenitors increase the performance of the algorithm. The mating consists of merging the two solutions into one keeping bits of each of the parents. The mating can be done by exchanging fixed sections of the solution, but also selecting random bits of each parent. In either case, we need to make sure that the solution is still consistent. For example, if no repeats are allowed, we need to check that no repeats exist in the offspring, otherwise, that needs to be corrected so the solution satisfies the problem constraints.

### 5\. Mutating

The mutation step is important to prevent that our algorithm gets stuck at the local optima. The local optimum is a solution that seems the best if we look at nearby solutions but it's not the best possible solution. The best possible solution or global optima may be behind a dip and therefore we need randomness to jump across hills. The mutation step generates this so necessary randomness. Depending on the selected randomness, the mutation step changes different parts of the solution arbitrarily. If it's too little we get stuck at the local optima, if it's too much it will break the best solutions preventing them from consolidating and keep improving the general population fitness. There should be noted that some implementations do have inclusion criteria for the offspring. Some applications have a filter that prevents really bad offspring to be added to the set of solutions. Other solutions include mechanisms to prevent that the generated offspring are too similar for the sake of variation. The higher the variation the higher the chances of achieving a better solution, otherwise it can converge to all the solutions being the same.

### 6\. Stopping criteria

If the stopping criteria are met, then we stop the execution. Otherwise, we go to step two and repeat the whole process again. Since the best solution is unknown a set of rules can be defined in order to stop the computation.

- There is a solution that satisfied the minimum criteria. That means that there is a solution that has a fitness equal or better than we expected to be satisfied.
- We already performed too many iterations. The algorithm has looped enough times so we assume that nothing better can be found.
- We spent the budget. The computation/time/money has been used and there are no more resources left to continue iterating.
- The solution has plateaued. The solution does not seem to improve and maybe it is not worsening either. The algorithm seems unable to find something better.
- We think that the solution is good enough. After checking the results manually we can decide that we're satisfied with the results and decide to stop the experiment.
- A combination of all. We can merge all of them and find the best stopping rule for our taste.

## Genetic Algorithm Example

Let's get our hands dirty and code a genetic algorithm in python for optimization. To keep the consistency of methods, the evolutionary algorithm in python is going to be the genetic algorithm (GA). We first will tackle the **traveling salesman problem** using the genetic algorithm and then the **knapsack problem** also with the genetic algorithm and python. You'll find both genetic algorithm python code in GitHub as a link at the end of each problem description.

### Traveling Salesman Problem Genetic Algorithm Python

We'll go through this genetic algorithm example step by step. The [traveling salesman problem](https://en.wikipedia.org/wiki/Travelling_salesman_problem) or TSP is a classic problem where you have a set of cities and there is the need to find a round trip route across all cities without repeating any.

#### Initialization

<script src="https://gist.github.com/rocreguant/4e0ec9c16847b44b9a05b3e04f656985.js"></script>

#### Fitness assessment

<script src="https://gist.github.com/rocreguant/e0abf4b20d03542f77ae3278f88e22c4.js"></script>

#### Selection

<script src="https://gist.github.com/rocreguant/e89b2efde4246c1d91847b467064776b.js"></script>

#### Crossover

<script src="https://gist.github.com/rocreguant/69ab5e9146b38c859c25ff6a90796b37.js"></script>

#### Mutation

<script src="https://gist.github.com/rocreguant/933ba3ff22c325390d17a7fbe906fe75.js"></script>

#### Stopping criteria

<script src="https://gist.github.com/rocreguant/b4fa8ef573dbb63c2072a0d86804cf2d.js"></script>

A fully working implementation of the TSP problem implemented using a Genetic Algorithm in Python can be found on the [**jupyter notebook in Github**](https://github.com/rocreguant/personal_blog/blob/main/Genetic_Algorithm_Python_Example/Traveling_Salesman_Problem.ipynb).

### Knapsack Problem Genetic Algorithm Python

This is the second ga algorithm in python. The knapsack problem provides us with a set of items with a weight and a value. Based on that we need to find which objects include in the collection so that the total weight is less than or equal to the limit and the total value is as large as possible.

#### Initialization

<script src="https://gist.github.com/rocreguant/77b82e4deccab8f531b551516b81794a.js"></script>

#### Fitness assessment

<script src="https://gist.github.com/rocreguant/a46f0df0d499528cdadf4d1f218e2f4c.js"></script>

#### Selection

<script src="https://gist.github.com/rocreguant/59863a98621f9774b5b041dd79e06baf.js"></script>

#### Crossover

<script src="https://gist.github.com/rocreguant/e4a0b7e63c4f3219805a4fd8b751e1e8.js"></script>

#### Mutation

<script src="https://gist.github.com/rocreguant/e239834877c61b827a665c05b4aebc43.js"></script>

#### Stopping criteria

<script src="https://gist.github.com/rocreguant/925082e87f13640d196b31f4364e9a93.js"></script>

The full working implementation on [jupyter notebooks and python using a genetic algorithm of the Knapsack problem](https://github.com/rocreguant/personal_blog/blob/main/Genetic_Algorithm_Python_Example/Knapsack_problem.ipynb) can be found on the GitHub.

## Advanced: Tricks to improve your code

Each problem has a different set of rules, but researchers have found out a different set of techniques that if properly used can improve the performance of the algorithm.

- **Good initial solutions** Instead of setting the problem with random solutions you can start with bets on how the solution is going to look like. In this way, the algorithm will be directed and hopefully closer to the best solution the problem has.
- **Elitism** consists on keeping the best N solutions of the problem as they are. You should keep them as they are to the next generation. By ensuring that the best solutions are passed over generations the algorithm will avoid that the overall quality of the population decreases. Keeping the best will enable an improvement over the existing solution.
- **Adaptive hyperparameters** enables adaptation for the crossover and the mutation rate depending on the state of the solution. Higher variation may be desired at the start but once we're close to the solution we should aim to search in the nearby space.

## Short video explanation

This is a short video explanation of genetics algorithms. After the presentation, the speaker shows his Traveling Salesperson Problem (TSP) implementation and how different parameters affect the performance of the algorithm. Different population sizes or mutation rates affect performances at various rates. It is very well explained and clear.

https://www.youtube.com/watch?v=XP8R0yzAbdo

Thanks for reading. If you have any further questions leave a comment!
