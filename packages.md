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

rpart
=====

Create a regressin tree

``` R
rpart(dependent ~ independent, data = fram, method="class", minbucket=25)
```

rpart.plot
==========

plot the rpart regression tree

``` R
prp(rpart-tree)
```

randomforest
============

Create a random forest tree

``` R
randomForest(independent ~ depenedent, data = Train, ntree=200, nodesize=25 )
```

caret
======

Create number of folds for the train function

``` R
numFolds = trainControl( method = "cv", number = 10 )
```

Create a data frame from all combinations of the supplied vectors or factors

``` R
cpGrid = expand.grid( .cp = seq(0.01,0.5,0.01))
```

Calculate the optimal cp for regression tree

``` R
tr <- train(independent ~ dependent, data = Train, method = "rpart", trControl = numFolds, tuneGrid = cpGrid )

#Get best tree
tr$finalModel
```

Normalize data, all data is set with mean of 0 and a standard deviatian of 1

``` R
# preprocess 
preproc = preProcess(airlines)
# normalize
airlinesNorm = predict(preproc, airlines)
```


e1071
======

Misc statistics functions

tm
===

Create text documents.

``` R
Corpus(VectorSource(text-vector))
```

``` R
# Convert all text to lowercase
tm_map(corpus, tolower)
# convert back to plain text document
tm_map(corpus, PlainTextDocument)
# convert to lowercase without having to convert back to plain text
tm_map(corpus, content_transformer(tolower))
# remove punctuation
tm_map(corpus, removePunctuation)
# remove words
tm_map(corpus, removeWords, c("other-word", stopwords("english")))
# stem document, will use `SnowballC`
tm_map(corpus, stemDocument)
```

``` R
# Get single document
corpus[[1]]
# Get single document as text
as.character(corpus[[1]])
corpus[[1]]$content
```

``` R
# Create sparse matrix of words in the corpus
DocumentTermMatrix(corpus)
# inspect matrix
inspect(frequencies[1000:1005,505:515])
# convert to data frame
as.data.frame(as.matrix(sparse))
```

``` R
# find most popular words
findFreqTerms(frequencies, lowfreq=times-it-appears)
# remove low used words, words used in less than 1-theshold of documents
# for words that are in 0.3% or more documents: threshold = 1-0.003 = 0.997
removeSparseTerms(frequencies, threshold)
```

``` R
# make sure all variable names are R friendly
colnames(dataframe) = make.names(colnames(dataframe))
```

SnowballC
==========

Porter stemmer, load along with `tm` library.

flexclust
=========

Apply clusters from one to new data

``` R
# use existing kmeans and original data
KMC.kcca = as.kcca(KMC, healthyVector)
# apply to new data
tumorClusters = predict(KMC.kcca, newdata = tumorVector)
```