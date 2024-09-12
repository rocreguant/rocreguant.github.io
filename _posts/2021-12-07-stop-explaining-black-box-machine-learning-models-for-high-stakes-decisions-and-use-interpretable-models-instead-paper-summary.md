---
title: "Stop explaining black box machine learning models for high stakes decisions and use interpretable models instead (paper summary)"
date: "2021-12-07"
categories: 
  - "deep-learning"
  - "machine-learning"
tags: 
  - "black-box"
  - "deep-learning"
  - "explainability"
  - "interpretability"
  - "machine-learning"
---

Deep learning models are usually regarded as black boxes. That is because they are not transparent about the way they reach the prediction. Humans cannot directly interpret the model with millions of parameters. Choosing ignorance can lead to unforeseen dangers. This is inherently a bad practice that should be minimized as much as possible. Current deep learning explainability tools aim to simplify the process to the outcome but does not really explain the "thinking process" that the model followed. This is especially vital for high-risk enterprises such as healthcare.

Instead of trying to develop tools that explain the machine learning models, we should all be working towards developing models that are inherently explainable. When we use tools to explain the models, we do exactly that: explain the models. We do not explain how the world works.

The first critique against explainable models is the performance. It is not true that explainable models have lower accuracy than non-explainable ones. With the right pre-processing both models can achieve the same accuracy. Removing parts of a more complex model to achieve explainability will of course reduce accuracy but that is not representative of a real-world analysis. The model should be developed with interpretability in mind and not post-hoc.

Naturally interpretable models can help to correct the data and reveal false assumptions. The best predictors are constructed through an iterative process. Otherwise, the risk of garbage-in garbage-out increases. The "hidden patterns" that the black boxes seem to find may not be real. Those patterns can arise from data artifacts. However, if they are true signals, an interpretable model should be able to extract and use them correctly.

The use of explainability tools can be misleading. The use of correct labels to explain the model's path to the prediction hides some of the artifacts of the tool. For example, saliency maps offer similar explanations for the same image regardless of the class (Figure 1).

\[caption id="attachment\_2138" align="aligncenter" width="640"\][![Saliency map](images/saliency_map-1024x272.png)](https://rocreguant.com/?attachment_id=2138) Saliency map discrimination based on the clas\[/caption\]

Black boxes are harder to replicate and therefore can be used as a moat for the business model. One can develop a model for mortality in the Intensive Care Unit. If that model is a black box can be sold to hospitals. However, if it's a regression with 10 parameters making money out of it may be harder. If hospitals buy the black box solution, they assume that the data the model was trained on is similar to the one at the hospital. That means that the population follows a similar age and sex distribution as the input data, as well as, doctors follow similar diagnoses and treatment procedures. If those assumptions fail the model is likely to fail to achieve similar accuracies. The model would be making predictions for widely different cases than the ones it was trained for.

This leads to an accountability discussion. The AI providers do not want responsibility for the prediction failure of their models. That leads to different incentives than the assumed ones. The company's goal is to aim for obscurity and marketability instead of model simplicity. Private models performances should be updated with real-world data and not only with the training data to have a truthful view of the actual performance.

One could argue that open models could be reverse-engineered. But that should not be a problem. First, if the model can be gamed it was not properly designed. Second, a genuine alignment to the system to perform better may lead to better outcomes. Let's think about an insurance company that predicts mortality. If you quit smoking your mortality risk decreases and your insurance premium as well. Congratulations you successfully gamed the model! Was that a bad thing? Or is it a win-win? Transparent models are difficult to build. They require domain knowledge and are quite application-specific. It is generally easier to throw everything into a box and optimize for the highest performance possible. The costs of domain expert analysts are high compared to the computation ones.

\[1\] _Rudin, C. (2019). Stop explaining black box machine learning models for high stakes decisions and use interpretable models instead. Nature Machine Intelligence, 1(5), 206-215._
