# Unsupervised learning
- Inputs are labelled (known).
- Outputs are unlabelled (unknown).
- A set of inputs.
- I find patterns between inputs.
- I categorise inputs.

| Issue date (Input) | Mileage (Input) |     |      |
| ------------------ | --------------- | --- | ---- |
| 2000               | 100000          | OLD | HIGH |
| 2005               | 100000          | OLD | HIGH |
| 2010               | 1000            | OLD | LOW  |
| 2015               | 2500            | OLD | LOW  |
| 2020               | 75000           | NEW | HIGH |

# Unsupervised learning algorithms

## k-means clustering
- Grouping points which share similar attributes.
- Split data into k number of clusters.
- k is the number of clusters you want to create.
- Examine the points on the scatterplot.
- Manually select a point to be the centroid of the first cluster.
- Repeat for remaining clusters.
- Each point is assigned to the cluster of the nearest centroid by measuring the Euclidean distance.

![k-means clustering](/k-means%20clustering%202.png "k-means clustering")

*Euclidian distance*
![euclidian distance](/euclidean%20distance.png "euclidian distance")