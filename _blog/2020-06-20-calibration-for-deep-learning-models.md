---
title: "Calibration for deep learning models"
date: "2020-06-20"
categories: 
  - "deep-learning"
tags: 
  - "calibration"
  - "deep-learning"
  - "expected-calibration-errorplatt"
  - "reliability-diagram"
  - "sklearn"
---

Wikipedia's **definition for calibration** is _calibration is the comparison of measurement values delivered by a device under test with those of a calibration standard of known accuracy_. Put in a context that means that the distribution of predicted probabilities is similar to the distribution observed probabilities in training data. If we rephrase it again means that if your model is predicting cat vs dog and the model states that a given image is a cat with 70% probability then the image should be a cat 70% of the time. If the model deviates too much from that it would mean that the model is not correctly calibrated.

Then you may be thinking: **Why calibration is important if the model has a high accuracy?** Well then let me tell you. For critical decisions such as a car deciding to break or not. The model should be confident enough to give the breaking signal. If there is reasonable doubt then the system should rely on other sensors and models to take the critical decision. The same applies to human doctors and support systems. Decision models in medicine should pass the decision making to human doctors when there is not enough confidence that the model is choosing the right treatment. And last but not least it also helps with model interpretability and trustworthiness.

Originally models were well-calibrated \[1\] but it seems that the calibration in newer models is less reliable. In this post I do not aim to point architecture flaws. They fall out of the scope. Instead, I want to point ways of visualizing, assessing, and improving the calibration of deep learning models for your architectures. **These approaches are framework and model agnostic**, meaning that they work in TensorFlow, Keras, PyTorch, or whatever framework you would like to use but also regardless of the architecture model implemented.

The next pair of images show what we want in this post. We want to go from an uncalibrated model to a calibrated one.

| From this | to this |
| --- | --- |
| ![Poorly calibrated deep learning model example](images/poorly-calibrated-model.png) | ![Well calibrated deep learning model example](images/well-calibrated-model.png) |_Figure 1: The ECE stands for Expected Calibration Error (the lower the better). The blue bars are counts of occurrences in a certain bin, and the red area is the difference between expected occurrences and actual ones. So we can see that the first image shows a poorly calibrated model with high ECE (consequently lots of red) whereas the second plot there is very little red and the ECE is very low._

**To visually inspect the calibration of the model we can plot a reliability diagram** (Figure 1). A reliability diagram plots the expected sample accuracy as a function of the confidence. Any deviation from the diagonal represents a miscalibration. Since we probably don't have infinite samples to compute the calibration as a line, we need to first bin the predictions into _M_ bins. Then for each prediction in the bin, we need to assess whether the predicted label corresponds to the true label or not and divide the result by the number of predictions within the bin. For those of you that like formulas:

![Formula for the reliability diagram for each bin](images/reliability-diagram-bin-construction.png)

The Bm are the set of samples whose predicted confidence falls into the interval of the desired bin (in this case, the bin _m_). Both, y and ŷ, are the predicted label and the true label. Notice that in the reliability plot there is no display on the number of samples. Therefore, we cannot estimate how many samples are correctly placed in a bin or the overall model calibration. For that, we need a measure that is able to summarize the calibration of the model into a single scalar value. **There are several formulas to compute the general model calibration. In this post, we'll see the Expected Calibration Error (ECE) \[2\] which is the one displayed in the images above.**

ECE follows on the intuition of the bar plot. It takes the weighted average of the difference between accuracy and confidence for each of the bins. The confidence of a bin is the desired value and is obtained by getting the left and right sides of the bin and computing the average (i.e. dividing it by 2). And the accuracy is the formula presented in the previous paragraph. Then we compute the difference between accuracy and confidence, we multiply it for the number of samples in the bin and divide it by the total number of samples. So formula:

![Expected calibration error formula](images/expected-calibration-error-formula.png)

Now after we do this, we can visualize and assess numerically how good the calibration of our model is. We can also use the [sklearn library to plot the calibration curve](https://scikit-learn.org/stable/modules/generated/sklearn.calibration.calibration_curve.html) which is the equivalent of the bins approach we did above where a perfectly calibrated model should produce a line that fits x=y. We can use the sklearn library and plot the curve using the following example:

<script src="https://gist.github.com/rocreguant/916176d570eab91703f596754059eb95.js"></script>

If you made it this far you may be thinking: Now I know if the model is well-calibrated or not but I have no clue how to fix it. So today is your lucky day! **Platt scaling \[3\] is a parametric approach to calibration**. The non-probabilistic predictions (a.k.a. the predicted probabilities of your model) of a classifier are used as features for a logistic regression model trained on the validation set to return probabilities. At this stage we don't train the model anymore, the parameters are fixed.

<script src="https://gist.github.com/rocreguant/cccaabc1be933e0885675e34555f5272.js"></script>

All of these concepts and gists are going to provide you with enough knowledge to assess the model calibration and correct it if necessary. But it shall not affect much other metrics such as accuracy or [ROC AUC](https://rocreguant.com/how-to-add-roc-auc-as-a-metric-in-tensorflow-keras/1681/).

## References:

**Main paper: [Guo, Chuan, et al. "On calibration of modern neural networks." Proceedings of the 34th International Conference on Machine Learning-Volume 70. JMLR. org, 2017.](https://dl.acm.org/doi/pdf/10.5555/3305381.3305518?download=true)**

\[1\] [Niculescu-Mizil, Alexandru and Caruana, Rich. Predicting good probabilities with supervised learning. In ICML, pp. 625–632, 2005](https://dl.acm.org/doi/pdf/10.1145/1102351.1102430)

\[2\] [Naeini, Mahdi Pakdaman, Cooper, Gregory F, and Hauskrecht, Milos. Obtaining well calibrated probabili- ties using bayesian binning. In AAAI, pp. 2901, 2015.](https://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/view/9667/9958)

\[3\] [Platt, John et al. Probabilistic outputs for support vector machines and comparisons to regularized likelihood methods. Advances in large margin classifiers, 10(3): 61–74, 1999.](https://www.researchgate.net/profile/John_Platt/publication/2594015_Probabilistic_Outputs_for_Support_Vector_Machines_and_Comparisons_to_Regularized_Likelihood_Methods/links/004635154cff5262d6000000.pdf)
