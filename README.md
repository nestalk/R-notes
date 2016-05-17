R-notes
=======

Notes on using R for statistics


- [Basics](basics.md): basic commands and utilities
- [Packages](packages.md): usefull packages and how to use them
- [Linear Regression](linear-regression.md): How to do a linear regression
- [Logistic Regression](logistic-regression.md): How to do logistic regression
- [Regression Trees](regression-trees.md): how to do a regression tree
- [Natural Language Processing](language-processing.md): analysing text
- [Clustering](clustering.md): cluster analysis


Linear regression
-----------------

Good for predicting a continous outcome, numeric value. Simple, and works on
small and large datasets. Assumes a linear relationship.

Logistic regression
-------------------

Good for predicting a binary outcome, two categorical value. Creates probabilities on the
outcome. Assumes a linear relationship.

Regression Trees (CART)
-----------------------

Good for prediction an outcome, or continous outcome. Can handle datasets without a linear
relationship and is easy to explain. Small datasets may not work.

Random Forests
--------------

Similar to CART but can improve accuracy. Needs more setup and not as easy to interpret.

Hierarchial Clustering
---------------------

Good for finding similar groups of data. No need to know how many clusters you need, easy
to visulise. Difficult to use on large datasets.

K-Means clustering
-------------------

Similar to hierachial. Need to know number of clusters beforhand.