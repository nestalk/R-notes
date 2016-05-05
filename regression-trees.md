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

Complexity Parameter (cp) - like R<sup>2</sup>, smaller cp makes a bigger tree. Too many splits cause
model to overfit training data.

**RSS** Residual sum of squares - the sum of the square differences.

Goal with splits is to minimise sum-of(RSS-at-each-leaf)+lambda*splits. Lambda is the penalty,
between 0 and 1, the higher it is the less splits you will make.

cp = lambda/RSS-with-no-splits

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

``` R
# example penalty matrix
matrix(c(0,1,2,3,4,2,0,1,2,3,4,2,0,1,2,6,4,2,0,1,8,6,4,2,0), byrow=TRUE, nrow=5)

     [,1] [,2] [,3] [,4] [,5]
[1,]    0    1    2    3    4
[2,]    2    0    1    2    3
[3,]    4    2    0    1    2
[4,]    6    4    2    0    1
[5,]    8    6    4    2    0

# Calculate error
errors <- as.matrix(table(actuals, predictions))*PenaltyMatrix
sum(errors)/number-of-observations

# Add penalty function to tree
rpart(bucket2009 ~ ., data=ClaimsTrain, method="class", cp=0.00005, parms=list(loss=PenaltyMatrix))
```

Produce a chart that for each variable measures
the number of times that variable was selected for splitting
(the value on the x-axis).

```R
vu = varUsed(MODEL, count=TRUE)

vusorted = sort(vu, decreasing = FALSE, index.return = TRUE)

dotchart(vusorted$x, names(MODEL$forest$xlevels[vusorted$ix]))
```

Produce a chart on the impurity, how homogenous each leaf of the tree is.
In each tree in the forest, whenever we select a variable and perform
a split, the impurity is decreased. Therefore, one way to measure the
importance of a variable is to average the reduction in impurity, taken
over all the times that variable is selected for splitting in all of the
trees in the forest

```R
varImpPlot(MODEL)
```
