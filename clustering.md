Clustering
===========

Unsupervised learning algorithm. 

Group data into clusters.

Content filtering: filter based on details of current data.
Collaborative filtering: filter based on how others compare.

Distance betweeen data points.

Euclidean distance: d<sub>ij</sub> = sqrt((x<sub>i1</sub>-x<sub>j1</sub>)<sup>2</sup> + ... + (x<sub>ik</sub>-x<sub>jk</sub>)<sup>2</sup>)

```
# Calculate distances between each value, results in n*(n-1)/2 distances.
dist(movies[2:20], method = "euclidean")
```

Maximum coordinate distance: only consider where the data points deviate the most.

Mininmum distance between clusters, Maximum distance between clusters, Centroid distance is the
average of all the data points in cluster.

Normalize data variables used in dataset, higher scale variables can dominate distances.


Heirachiacal
------------

1. Each data point starts in its own cluster.
2. Combine two nearest clusters, euclidean and centroid
3. Repeat step 2

Creates dendogram. The height of a line represents how far apart the clusters were when combined.
Set a limit on the max distance you want clusters to combine at. Choose cut with a big distance.

Analyse clusters to check if they are meaningfull. Do they have anything in common that was not
used in the clustering.

```
# generate clusters
cluster <- hclust(distances, method = "ward.D")
# plot
plot(cluster)
# view what is in each cluster if you cut it down
rect.hclust(clusterIntensity, k = 3, border = "red")
# cut down cluster
clusterGroup <- cutree(cluster, k = 10)
# how many movies are in each cluster
tapply(movies$Action, clusterGroups, mean)
```

Look at what cluster an object is in, then look at what other objects are in the cluster.

Only for smaller datasets, dist function can generate a massive vector.


K-means
-------

k number of clusters, can be selected with prior knowledge or with experiment.

1. Set number of clusters k
2. Randomly assign each data point to a cluster
3. compute cetroids
4. re-assign data point te closest centroid
5. re-compute cetroids
6. Repeat steps 4 and 5 until no more movement

``` R
# create kmeans cluster
KMC = kmeans(healthyVector, centers = k, iter.max = 1000)
# view details on cluster
str(KMC)
# get cluster
healthyClusters = KMC$cluster
```
