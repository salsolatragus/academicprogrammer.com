---
title: Predicting Likelihood of Requirement Implementation within the Planned Iteration
categories:
  - MSR17
  - ICSE17

---

The work was motivated by IBM's desire to predict whether a feature would make it in the planned iteration. The work builds on previous work that predicts completion time, completion effort, and completion probability, as well as experience from IBM developers collected in interviews.

The goal is to predict whether a feature makes it within the planned iteration as early as possible. The authors looked at prediction quality on day-1 of an iteration, as well as after the 1st, 2nd, and 3rd quater. They used RandomForest learning technique with 29 features that characterize:

* The creator, owner, and creation date of the feature,
* the feature's complexity,
* the progress of work on the feature,
* the prioritization of the feature,
* the stability of the feature definition,
* stakeholder involvement, and
* the number of sub-elements of the feature.

The evaluation on 3 IBM projects shows that the precision of the prediction is up to 76% on day 1 and rises up to 84%, which is reached already after the 2nd quarter. Since IBM valued precision over recall, they applied cost-sensitive learning to give precision a 3-times-higher weight. This led to precision of up to 94% on day 1.

The results also show that the time remaining in the iteration, the creator of the feature in the tracking system, the time since the last change to the feature definition, the number of times the feature was already pushed to a later iteration, the days the feature had no owner assigned, and a large number of child tasks are the most important features (in decreasing order) with regard to the prediction quality.

---

This work was done by Ali Dehghan, Adam Neal, Kelly Blincoe, Johan Linåker, and Daniela Damian. Kelly Blincoe presented the work in Ali's name, who could come to ICSE due to Visa issues.

[See paper preprint](http://aliweb.me/wp-content/uploads/2017/04/Predicting-Likelihood-of-Requirement-Implementation-within-the-Planned-Iteration-An-Empirical-Study-at-IBM.pdf)
