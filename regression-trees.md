Regression Trees
=================

Classify categorical results in a form that can be understood by a human. 

Logistic
regression is difficult to understand what factors are more important and it is
hard to evaluate predictions on new data.

Builds a tree that splits on variables. In diagrams, always start from the top and yes
is always to the left.

Minbucket parameter controls number of splits, smaller is more splits.

Prediction of a split is the proportion of results over a threshold value.

Create regression tree, using the rpart package.

``` R 
rpart(dependent ~ independent, data = fram, method="class", minbucket=25)
prp(rpart-tree)
```

Predict results

``` R
predict(tree, newdata=frame, type="class")
```

Generate roc curve using ROCR

```R
# need the probibilities
PredictROC = predict(tree, newdata = Test)

pred = prediction(PredictROC[,2], Test$Reverse)
perf = performance(pred, "tpr", "fpr")
plot(perf)
```

A random forest is more accurate but harder to interpret. Each tree uses random subsets
of the data set with replacements.

`nodesize` = `minbucket`

`ntree` is the number of trees, more takes longer.

Results need to be factors.

create forest

``` R
randomForest(independent ~ depenedent, data = Train, ntree=200, nodesize=25 )
```

Predict

``` R
predict(forest, newdata = Test)
```

K-fold cross validation. Split the training set into k number of folds, build models on each k-1
folds. Compare the accuracy of the models and take the average.

Complexity Parameter (cp) - like R<sup>2</sup>, smaller cp makes a bigger tree

Perform cross validation

``` R
# Define cross-validation experiment
numFolds = trainControl( method = "cv", number = 10 )
cpGrid = expand.grid( .cp = seq(0.01,0.5,0.01))

# Perform the cross validation, return details stating best cp value
train(independent ~ depenent, data = Train, method = "rpart", trControl = numFolds, tuneGrid = cpGrid )

# Create a new CART model
rpart(independent ~ dependent, data = Train, method="class", cp = 0.18)
```

Use a penalty matrix to define asymmetric penalties for errors. An error in on direction is worse than
if it was in the opposite direction.