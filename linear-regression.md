Linear Regression
==================

For predicting a quantative (numeric) value based on one or more independent variables. e.g. predict a score based on conditions.

Basic equation: Y = B<sub>0</sub>+B<sub>1</sub>X<sub>1</sub>+...+B<sub>n</sub>X<sub>n<sub>

B<sub>0</sub> is the intercept, B<sub>1</sub> through B<sub>2</sub> are the coefficients.

**SSE** is the Sum of Squared Errors, the difference between each predicted and
actual values squared and added together:
 SSE = (x<sub>1</sub> - y<sub>1</sub>)<sup>2</sup>+ ... + (x<sub>21</sub> - y<sub>2</sub>)<sup>2</sup>
 
**SST** is the Sum of Squared Erros from the baseline, the difference between the predicted
values and the mean value squared and added together. Same Formula as SSE.

**RMSE** is the Root mean squared error, the square root of the SSE divided by the number of rows:
RMSE = sqrt(SSE/number-of-rows)

**R<sup>2</sup>** is the accuracy of the model. R<sup>2</sup> = 1 - (SSE/SST)

Creating linear model

``` R
lm(predict-value ~ variable1 + variable2 + ... + variableN, data= Frame)
lm(predict-value ~ . , data=Frame) # Use all values other than the predict-value
lm(predict-value ~ . - vector-name, data=frame) # all values excect the on specified
```

View model details, shows R<sup>2</sup>, coefficients and which variables are significant
to the prediction. Adjusted R<sup>2</sup> is the R<sup>2</sup> adjusted by the number of
variables used, if you add a new variable and it goes down but R<sup>2</sup> stays the same,
that variable has no effect on the accuracy of the model.

``` R
summary(model)
```

Get errors of model

``` R
model$residuals
```

Predict using the model, returns a vector of the predicted values.

``` R
predict(model, newdata= test-data-frame)
```
