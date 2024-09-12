---
title: "Hidden technical debt in machine learning systems (paper summary)"
date: "2021-11-30"
categories: 
  - "deep-learning"
  - "machine-learning"
tags: 
  - "code-smells"
  - "deep-learning"
  - "machine-learning"
  - "software-engineering"
  - "technical-debt"
---

Machine learning systems are wonderful. Many shapes and forms of machine learning algorithms are currently in use. Different models such as clustering like k-means, prediction methods like trees, or more advanced deep learning methods suffer from technical debt. In traditional software engineering, technical debt can be found in specific shapes. In addition to the "traditional" software engineering problems, machine learning systems also face new challenges. The following paragraphs present the different technical debt found in machine learning systems.

## 1\. Encapsulation

Isolation of the different software components is considered a good practice. Encapsulating objects enables easier code maintenance by derisking future changes (regardless of their goal). **Entaglement** Machine learning models are inherently coupled to data. Different features affect the model differently. If the input distribution of a single feature changes, then the model output is susceptible to change as well. The model interconnects all inputs so no input is really independent. To solve this issue it is recommended to monitor the input features as well as the output of the model to notice changes over time. If either changes, it may be an indicator that it is time to update the model.

**Correction cascades** Sometimes the model does not behave the way we want it to behave. To solve this we can add fitter, calibrations, heuristics, or thresholds. These hotfixes can pile up in a correction layer that hides the special cases that the model could not handle correctly. As the layer increases, it is harder to differentiate the model from everything else surrounding it. Improving small parts of the system may lead to global detriments. The solution to solve this is to create a model that corrects for everything instead of coupling several layers on top.

**Undeclared customers** Generally, there are no restrictions on whom can use the output of a model. By allowing different systems to use the output of a model it may create unintended and poorly understood dependencies. Sometimes hidden feedback loops may arise. To prevent this tighter restriction access should be put in place to track usage dependencies.

## 2\. Data dependencies

Code dependencies can be studied with static analysis. However, there are no similar tools for data analysis. That can lead to a build-up of dependency chains difficult to untangle.

**Unstable data dependencies** Data can be consumed from another machine learning system that can change over time. The source model provides an outcome distribution that can change when the model is updated. If that is the case, the downstream models will be affected. This brings a higher complexity to identify the source of the changes. A solution would be to track the versions for each of the models and specifically tag each model. However, this in return creates a higher complexity of maintaining several signals over time.

**Underutilized data dependencies** Underutilized data dependencies are input signals that bring little improvement to the model. Moreover, changes in these signals can lead to unintended effects on the final outcome. It can be that a feature made sense in the past but now, without really being used, it is still in the model. Other effects of underutilized inputs leading to problems may be correlated features or bundled features. Features that bring marginal performance increases with unclear relevance are included at a cost of model complexity and overhead.

**Static Analysis of data dependencies** Like with traditional code, there are tools to perform static analysis for data. This is essential for tracking changes, migrations, and, if necessary, force updates. This can make automatic checks to make sure that the right dependency trees are correctly resolved.

## 3\. Feedback loops

Machine learning models usually influence their own behavior over time. A priory, it is difficult to assess how much it will affect the model. These feedback loops are difficult to assess and address especially when it happens over time.

**Direct Feedback Loops** In a direct way, the model influences its own future training data. One of the ways to solve this is to apply randomization. Another way is by leaving portions of the data untouched.

**Hidden Feedback Loops** Direct feedback loops are challenging to identify and fix, but even more with hidden feedback loops. The hidden ones consist of two or more systems that influence each other through the real world. For example, two different investment companies have developed two different investment algorithms. Both of their actions are tightly influenced by each other and may influence the buy/sell behavior of the other.

## 4\. Machine learning system anti-patterns

As sexy as it may seem, the ML model is only a fraction of all the code required. All the data pre-processing filtering and post-processing is required and often underappreciated.

**Glue Code** Packaging the whole system into one solution inhibits improvements. It makes it harder to analyze, update and tweak the parts individually.

**Pipeline Jungles** This anti-pattern occurs when new signals and information sources are found and added sequentially without care.

**Dead Experimental Codepaths** Within the production code, it is common to create new branches of execution to test new hypotheses or experiment with new methods. However, with time this creates a code complexity that needs to be scrapped out, or otherwise it can lead to fatal errors. It is good coding practice to examine regularly all the branches and delete the unused ones.

**Abstraction Debt** There seems to be no consensus on the right abstraction in the ML community. Map-reduce started being the predominant abstraction; however, it seems that the parameter-server pattern is more robust.

**Common Smells** Multiple-language smell. If it is possible, avoid using different languages for the same system. Otherwise, it increases its complexity. Prototyping smell occurs when the production system is scaled from small prototypes. Prototypes do not always reflect the reality of the full-scale system.

## Configuration Debt

An obscure place where the technical debt of a machine learning system can be hidden is in the configuration. A large system has many configuration options such as algorithm learning settings, pre- and post-processing methods, verification procedures, etc. It is easy to make configuration errors that may lead to at least waste computing power or even worse production errors. Redundant or settings should be detected and removed. Ideally one could easily visualize how the different configurations affect the system.

## Dealing with Changes in the External World

Machine learning systems are often developed to interact with the real world. That comes at a cost. The cost of interacting with the real world is that real-world data shows little stability and has the potential to change.

**Fixed Thresholds in Dynamic Systems** Generally, the thresholds are selected manually. However, that is time-consuming and not scalable. The best way to select thresholds is to have a hold-out validation set to adjust automatically the value.

**Monitoring and Testing** Unit testing is used for software development but for machine learning systems it is difficult. One cannot predict fixed values if the system is intended to adapt to new input distributions over time. As mentioned above, it is possible to monitor the input and output distributions of the values and issue warnings if they change. In the event of a significant change, it may be worth revisiting and, if necessary, updating the system. Some manual limits can also be placed. It may make sense to prevent trading algorithms to invest all the money in one stock or prevent it to set a book price to ridiculous amounts.

## Other Areas of ML-related Debt

**Data Testing Debt** As mentioned earlier, testing the data for at least outliers is critical to the well-functioning of a system. More advanced methods, of data distributions evaluation, are useful for more subtle changes.

**Reproducibility Debt** Reproducibility is important to real-world ML systems usage. Once developed, the model should perform similarly to the real data as it did during the development phase.

**Process Management Debt** As the number of systems increases, manual management gets more time-consuming. Therefore, it is important to try to simplify and remove manual steps and create more streamlined pipelines.

**Cultural Debt** There shouldn't be a hard line between engineering and research departments. They both should interact and collaborate. That helps to reduce system complexity and increases reproducibility; thus, leading to long-term better system health.

I hope this post helps you to be mindful of the type of debt encountered in ML systems and how to avoid it or at least minimize it.

_\[1\] Sculley, D., Holt, G., Golovin, D., Davydov, E., Phillips, T., Ebner, D., Chaudhary, V., Young, M., Crespo, J.F. & Dennison, D. (2015). Hidden technical debt in machine learning systems. Advances in neural information processing systems, 28, 2503-2511._
