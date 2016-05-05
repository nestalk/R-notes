Logistic Regression
====================

For predicting a qualitative (categorical) value based on one or more independent variables. 
e.g. predict if an outcome will be true or false based on conditions.

Probability equation / Logistic Response Function: 
P(y = 1) = 1/(1+e<sup>-(B<sub>0</sub>+B<sub>1</sub>X<sub>1</sub>+ ... +B<sub>n</sub>X<sub>n</sub>)</sup>)

**Odds** is the likelyhood of the value. > 1 if y=1 is more likely, < 1 if y=0 is more than likely.

Odds = P(y = 1)/P(y = 0)

Odds = e<sup>(B<sub>0</sub>+B<sub>1</sub>X<sub>1</sub>+ ... +B<sub>n</sub>X<sub>n</sub>)</sup>

log(Odds) = B<sub>0</sub>+B<sub>1</sub>X<sub>1</sub>+ ... +B<sub>n</sub>X<sub>n</sub>

**Logit** = log(Odds)

The larger the Logit, the bigger P(y=1)

Creating logistic model

``` R
glm(predict-variable ~ variable1 + variable2, data = frame, family=binomal)
glm(predict-variable ~ ., data=frame, family=binomal)
# you can do combinations using variable1:variable2
```

View the model details, similar to linear model. Coefficients > 0 contribute to P(y=1). AIC is
the quality of the model, less is better, only comparible to models on the same data set.

``` R
summary(model)
```

The Coefficient is the log odds increase for that variable, to calculate the actual odds it is the `exp(Coefficient)`


Predict based on the model.

``` R
predict(model, newdata=test-data-frame, type="response") # as probabilities
predict(model, newdata=test-data-frame) # probabilities on the logit scale
```

To predict based on the probabilities you need to set a threshold value *t*. Probability >= t is true, < is false.

Classification matrix, can be generated with the `table` function:

``` R
table(actual, probibility-pridicted > threshold)

         | predicted=0     | predicted=1
actual=0 | True Negatives  | False Positives
actual=1 | False Negatives | True Positives
```

Acuracy of correct positive results:
**Sensitivity** = TP/(TP+FN)

Acuracy of correct negative results:
**Specificity** = TN/(TN+FP)

**Acuracy** = (TN+TP)/N

**Baseline Accuracy** = (TN+FP)/N

**Error Rate** = (FP+FN)/N

Higher theshold will have a higher Sensitivity and a lower Specificity.

A ROC curve plot can help decide the correct threshold. The Area under the curve (AUC) will give
an absolute measure of the quality and accuracy of the model.