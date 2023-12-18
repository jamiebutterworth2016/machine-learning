# Unsupervised learning
- Use to discover patterns in data.
- The algorithm classifies the data but doesn't label the class.
- We label the class.
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
- Examine the points on the scatterplot.
- Manually select a point to be the centroid of the first cluster.
- Repeat for remaining clusters.
- Each point is assigned to the nearest cluster - measured by the Euclidean distance.
- Calculate the average X and y values (the mean) of the points in each cluster.
- Take the mean value of the points in each cluster and plug in those x and Y values to update the centroid coordinates on the scatterplot.

![k-means clustering](/images/k-means%20clustering%202.png "k-means clustering")

*Euclidian distance*
![euclidian distance](/images/euclidean%20distance.png "euclidian distance")
