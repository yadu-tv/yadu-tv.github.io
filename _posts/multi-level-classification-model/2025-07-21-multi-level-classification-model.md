---
title: Multi level classification model
date: 2025-07-21 17:48:00 +05:30
description: This article talks about how i came up with a multi level classification model which includes both supervised and unsupervised models.
---

This article talks about how i came up with a multi level classification model which includes both supervised and unsupervised models.

#### TL;DR

When labels are messy or partially wrong, a single supervised model isn’t enough. I stack two explainable supervised classifiers (Logistic Regression, Naive Bayes) with two unsupervised/anomaly models (e.g., Isolation Forest, DBSCAN/KNN) and feed their outputs into a weighted voting classifier that produces both a final prediction and a confidence score. High‑confidence predictions can be auto‑accepted; low‑confidence or conflicting results are routed for manual review. I track model quality using Accuracy, F1, Cohen’s Kappa, and NMI (for clustering/anomaly alignment) to judge overall reliability and guide iteration.

#### Why this matters?

Let's just say you have some sort of data, assume that its cleaned and all the preprocessing is done. What if the data itself is not correct? How will your model learn in such case if its supervised learning models? When ground truth values are itself incorrect, it's not straight forward and we need to use complex solutions.

#### What's the proposed solution?

A complex model built on top of 5 other models. 2 supervised, 2 unsupervise and a voting classifier in the final layer. The outputs of supervised and unsupervised models are taken as input in voting classifier model which then makes the final prediction. This way the prediction made by majority of the model wins. 

#### What models to use in supervised and unsupervised?

Supervised models can be any classification model such as Logistic Regression and Naive Bayes. Logistic Regression and Naive Bayes because both of them are highly explainable. Explainability is important in a scenario where the ground truth in itself might be wrong. Not to mention both of these models have really good performance as well.

Unsupervised models can be something like Isolation Forest, KNN and [DBScan](https://github.com/mhahsler/dbscan). You might wonder why DBScan? DBScan is excellent at clustering similar nodes. This allows us to find anomalies which cannot be placed in one of the classes/clusters. I have also tried other methods for unsupervised models such as [Annoy](https://github.com/spotify/annoy) by spotify which is also excellent at clustering and generating recommendations.

#### How does the voting classifier work?

The voting classifier also doesn't work on its own. It also needs to be trained and provided with all sorts of input and output data. It is also supervised learning. The classifier is also trained to give a confidence score which says how confident it is with a prediction - which is a very useful metric to have. 

#### What happens when models disagree?

The voting classifier is also given the weightages for each of the models. More weightage will allow the model to predict accordingly. The confidence scores generated also allows us to filter at later stage to even consider the prediction or not as something with low confidence is not preferrable or has a high probability of being wrong. Predictions with low confidence are then used for manual reviewing and see how such cases of inputs are handled by the model step by step.

#### Evaluation metrics

I used Accuracy, F1 score, [Cohen's Kappa](https://en.wikipedia.org/wiki/Cohen%27s_kappa) and [NMI](https://en.wikipedia.org/wiki/Mutual_information) for unsupervised learning. These allowed me to get a good idea of how good the models work. 

#### Conclusion

Building a multi-level classification model by combining supervised and unsupervised approaches with a voting classifier can greatly enhance robustness, especially when data quality is uncertain. The inclusion of confidence scores and evaluation metrics like F1, Cohen’s Kappa, and NMI ensures that predictions are reliable and actionable. This architecture not only handles anomalies effectively but also offers transparency and flexibility for future improvements.