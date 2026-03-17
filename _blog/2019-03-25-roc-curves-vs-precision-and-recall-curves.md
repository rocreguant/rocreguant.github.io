---
title: "ROC curves vs Precision and recall curves"
date: "2019-03-25"
categories: 
  - "machine-learning"
---

ROC curves are widely used but not always descriptive. The ROC curve is a plot of the true positive rate (TPR) against the false positive rate (FPR). It defines how many true positives are vs how many false positives. The higher the area below the curve the better it is, this area can be defined as a number. Then with the The precision-recall curve we get the tradeoff between precision and recall. Again, the bigger the area below the curve the better.

Due to the properties of the ROC curve and the precision-recall curve we can get few conclusions.Precision depends on how rare is the positive class. So the ROC curve is less informative than the precision–recall curve for unbalanced data sets.
