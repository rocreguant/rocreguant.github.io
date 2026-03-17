---
title: "The new software: Advantages and disadvantages"
date: "2020-09-29"
categories: 
  - "deep-learning"
  - "thoughts"
tags: 
  - "deep-learning"
  - "pros-and-cons"
  - "software"
  - "thoughts"
  - "vision"
---

Recently I published a post about [the new software paradigm](https://rocreguant.com/the-new-software-less-coding-more-data/1738/). The new paradigm of software is the one that the coder does not directly program each of the cases for any of the given inputs. The new paradigm uses training data to let the computer learn the outputs for each input. The computer programs itself while the coder and the software developer's job is to prepare the data and set the target. The new paradigm seems to bring new challenges that need balancing. It has, like everything, some advantages and disadvantages.

On the advantage side, deep learning requires easier hardware. Even though deep learning is more complex than traditional software, **neural networks only consists of two basic operations: matrix multiplication and thresholding**. Traditional software has many more basic operations like conditionals, loops, etc. Because of that traditional CPUs are required to be able to run many more distinct operations increasing the overall complexity of the hardware. Where traditional software uses CPUs, deep learning uses GPUs. GPUs are developed to perform matrix multiplications making them ideal for neural networks.

Since deep learning is inherently less complex on hardware, one could easily **embed already trained models into chips** to perform certain tasks. This will make chips low power and specifically designed for defined tasks. If the task at hand is better defined and specific, hardware can be developed so that it is more efficient making it prone as well to scale economies. Imagine a manufacturing chip that performs speech analysis. In a way, this is more portable than code. The code often needs to be recompiled on the system to ensure that works and has optimal performance. A chip would have everything integrated from the microphone to the model.

Once the neural network is trained. **Execution time and memory use are constant**. Deep learning prediction only requires one forward pass which always requires the same amount of operations and memory. Traditional software different branches of the code require different amounts of resources which leads to a wide range of execution times and resource consumption (i.e. memory allocation). At the same time with traditional software, the branching adds complexity for the developer to not forget any case open, untreated, or even an infinite loop. An infinite loop of the traditional software would render the program unresponsive for eternity. This specific bug does never happen in neural networks.

Contrary to the traditional software that remains untouched for most of their life, deep learning models have the ability to evolve, mutate, and mature to reach and maintain the global optimum. In traditional software calls, APIs, and modules are created alone and die alone. Unless changed software stays the same forever. In this new paradigm, your call helps the model to find a better solution, and be faster and therefore adapt and improve. The more use the better the whole system becomes. You browsing through the internet would help to build a better internet. This software would learn from usage.

Even though there are instances where certain coders would be able to write better code than deep learning, in general, neural networks are better pieces of code. The same holds for high- and low-level languages. Even though most coders do a good job programming high-level languages and let the compiler do their magic, there is an extremely small fraction of people that are able to tune assembly instructions to improve the performance. Small local improvements do not reflect global gains.

But not everything that glitters is gold. Neural networks may be able to achieve 99% accuracy but it may be impossible to understand how this is reached. In some cases, a 90% accuracy that humans comprehend may be preferable. This is a tradeoff that should be assessed case by case. Would you rather get a treatment 99% certain without knowing what is it, or 95% certain but a doctor can explain to you?

Maybe humans don't trust machine learning models because they may be [picking up biases](https://www.vice.com/en_us/article/nz7798/weve-already-taught-artificial-intelligence-to-be-racist-sexist). If it's true it is on everyone's best interest to prevent that. It's in humanity's best interest that technology remains neutral. But this may be harder than we thought. [Microsoft trained a twitter bot on twitter and it turned out to be racist](https://www.theverge.com/2016/3/24/11297050/tay-microsoft-chatbot-racist), the reason is that some data cleaning is required, not everything has value. And [amazon built a misogynist HR algorithm](https://www.reuters.com/article/us-amazon-com-jobs-automation-insight-idUSKCN1MK08G) because they have biased data to start with. So it turns out that machines reflect what's there without the power to argue against it.

In a way we want the machines to judge the outputs. For everyone's comfort maybe we should be supervising all algorithms. Deep learning will provide an answer to the data. It may not always be the right answer, but sometimes it may be so wrong that a person will easily pick up. Models do not tell you when they don't know, if it was not properly trained on specific regions of the data it will provide an embarrassingly wrong result.

Malicious people may use this lack of judgment to benefit from AI. This new software will require new security measures. Attacks against neural networks are different in nature than the attacks that can be done on traditional software. Misleading is as easy as finding a way to mislead the algorithm. If they are somehow public it's a matter of time until somebody realizes that some tweaks produce vastly different results.

This new paradigm will require new tools. The old software needed debuggers, profilers, and IDEs. The new paradigm is done by accumulating, cleaning, and processing datasets. The new debugging will be done by adding new data with the labels the model fails to recognize. The IDEs may show the model architecture, the training data, and labels but it may also show which data points may be relevant to include so that the model gains certainty on the prediction. Maybe the new era Github is about datasets and trained models.
