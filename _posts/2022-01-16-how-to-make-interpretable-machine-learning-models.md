---
title: "How to make interpretable machine learning models"
date: "2022-01-16"
categories: 
  - "deep-learning"
  - "machine-learning"
tags: 
  - "deep-learning"
  - "explainability"
  - "interpretability"
  - "machine-learning"
---

Generally, deep learning models are not interpretable. That poses a challenge especially when those models are intended for public use. Interpretable models can achieve the same performances providing better feedback to the developers and the users. Through an iterative process, the data fed into the model can be processed and tailored so that the number of data artifacts is reduced or even removed. With interpretable models, we also understand the way the prediction is made and remove the wrong interpretations usually done via black-box models.

## 1\. Optimal logical models

A logical model consists of "or", "and, "if-then", etc. operators to produce a prediction. These are logical trees similar to the expert systems built during the last century. These trees are large and do not reflect a global optimal performance. These trees should be built as a tradeoff between the number of statements and the performance increase. For example, every new statement should decrease the performance error by at least 1%. In this way, we obtain a model that is easy to interpret and yet achieves good performance without the risk of overfitting. In spite of the model simplicity, finding the optimal number of statements and tree depth is not a trivial task and can be computationally expensive.

## 2\. Optimal scoring systems

A scoring system is a linear model that combines different weights (scores) to predict a final value. This unique value is the summary of all single features of the model. However, in this instance, we know how much each of the features contributed to the final outcome. If possible it is desired that the number of features is reduced to the minimally significant ones.

## 3\. Define interpretability for specific domains

Deep learning took off thanks to its power to classify images. Computer vision has been creating tools to explain the system but not to adequately interpret it. As it is right now, a deep learning model learns to classify images and the explainability tool detects the hot regions (generally without much of a meaning). What some have suggested is a deep learning model that is able to segment the images and find similar patterns to other images. Then by summing the weighted similarities one can extract the final class of the model. With that, we can then understand the reasoning where the model says _this_ part of the image looks like _that_.

These are some ways of building interpretable and robust machine learning models. These models can replace the black box and obscure models without compromising on accuracy. The whole community should strive for more interpretable tools.
