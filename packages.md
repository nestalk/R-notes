Usefull Packages
==================

zoo
---

Create an ordered series

``` R
zoo(frame$vector)
```

Use with lag to create an offset of a vector

``` R
lag(zoo(vector), offset, na.pad=TRUE)
```

Get vector back from zoo series

``` R
coredata(zoo-series)
```

caTools
-------

Utility functions

Randomly split dataframe into training and test data.

``` R
# Set a seed to make split reproducable
set.seed(number)
# Create vector of logical values
split <- sample.split(vector, SplitRatio= ratio)
# Subset dataframe
train <- subset(frame, split == TRUE)
test <- subset(frame, split == FALSE)
```

ROCR
----

Create ROC (Receiver Operator Caracteristic) curve plots for logistic regression


``` R
# Create prediction functions
pred <- prediction(predictions, actuals)
# Performance function (true positives vs false positives)
perf <- performance(pred, "tpr", "fpr")
# Plot function
plot(perf)
# Plot with colour and labels
plot(perf, colorize=TRUE, print.cutoffs.at=seq(0,1,bi=0.1), text.adj=c(-0.2,1.7))
```

Calculate Area under Curve

``` R
as.numeric(performance(prediction-function, "auc")@y.values)
```

mice
=====

Handle missing data using imputation

``` R
set.seed(number)
imputed = complete(mice(simple-data-frame))
```