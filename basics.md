R Basics
=========

Set working directory

<small>Note: Always use '/' and not '\' in the path, even on windows</small>

``` R
setwd("directory")
```

Get working directory

``` R
getwd()
```

Read CSV file into a variable

``` R
Variable <- read.csv("filename")
# read in file with other type of seperator
read.table("filename", header=FALSE, sep="|",quote="\"")
```

Display stucture of data frame

``` R
str(variable)
```

Show summary of variable

``` R
summary(variable)
```

Get vector from frame

``` R
Frame$vector
```

Get vector names of a frame

``` R
names(Frame)
ls(Frame)
```

Get frame index number

``` R
which(condition)
which.max(vector)
which.min(vector)
```

Find index of value in frame

``` R
match(value, frame$vector)
```

Get row of data frame

``` R
frame[index,]
```

Get vector value of row

``` R
frame$vector[index]
```

Get subset of a data frame

``` R 
subset(Frame, condition)
``` 

Get number of rows in frame

```
nrow(frame)
```

Get standard deviation

``` R
sd(frame$vector, na.rm=TRUE)
```

Plot two values

``` R 
plot(x-vector, y-vector, xlab="X label", ylab="Y Label", main="plot title", col="colour")
```

Add additional plot to existing plot

``` R
lines(x-vector, y-vector, col="colour")
```

Add line to existing plot

``` R
abline(v=value-on-x-axis, lwd=line-width)
```

Create histogram

``` R
hist(vector)
hist(vector, xlim=limit-vector, breaks=num-of-breaks)
```

Create boxplot

``` R
boxplot(vector)
```

Count/compare number of values in vector

``` R
table(vector)
table(vector1, vector2)
```

Apply function to comparison of values

``` R
tapply(vector-to-be-applied, vector2, function, na.rm=TRUE)
```

Convert string to time

``` R
strptime(vector, format)
```

Jitter values to prevent overlapping on plots

``` R
jitter(vector)
```

View correlation between two vectors

``` R
cor(frame$vector, frame$vector)
cor(frame)
```

Create an offset of a vector

``` R
lag(vector, offset, na.pad=TRUE)
```

Reduce a data frame to selected vectors

``` R
dataframe[c(vector-name, vector-name2,...)]
```

Remove vectors from a data frame

``` R
frame[,names(frame) %in% vector-of-names-to-remove)
frame$vector <- NULL
```

``` R
# Fix column names
colnames(data_frame_name) <- make.names(colnames(data_frame_name))
```

Show help

``` R
# For command
?command
# for package
help.start()
help(package="package-name")
```

``` R
# dimensions of a vector
dim(flowerClusters) = c(50,50)
```