# Pre-model algorithms
An extension of data scrubbing.\
Unsupervised learning algorithms can be used to clean and reshape data.\
This occurs before the use of a supervised learning algorithm to build the model.

Examples:
-  Principal component analysis (PCA)
-  k-means clustering

## Principal component analysis (PCA)
A popular dimension reduction technique.\
Known as general factor analysis.\
Reduce data complexity.\
The goal is to find a low-dimensional (2D or 3D) plot of the dataset.\
Also to preserve the original shape as much as possible.

### Components
PCA recreates dimensions as a linear combination of features called components.\
PCA then ranks components that contribute most to data patterns.\
You can then drop the components which have the least impact on data variability.

### Creating the plot
The X axis should hold the feature with the most varied data points.

Each point of this feature has a different value. The points are varied so this component is the perfect candidate for the X axis.

![x axis](/images/practical/x-axis.PNG)

The y axis is perpdendicular to the X axis.

Forms an orthogonal line which is used to create the first two components.
TODO: more.


## Practical

### Info
Dataset is located at `~\practical\data\advertising.csv`.\
Install scikit with `pip install scikit-learn`.

### Import libraries
```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline
```

### Import data
```
df = pd.read_csv('~/Downloads/advertising.csv')
df.head()
```

### Remove features
```
del df['Ad Topic Line']
del df['City']
del df['Country']
del df['Timestamp']
del df['Male']
```

### Scale data
StandardScaler is used wth PCA to rescale and standardise features.\
Gives the dataset the properties of a distribution with a mean of zero and a deviation of one.\
*Is this finding the feature with the most variance?*
```
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(df)
scaled_data = scaler.transform(df)
```

### Set algorithm
Import the PCA algorithm.\
Reshape the features into a number of components.\
PCA finds the two components which best explain variability in the data.
```
from sklearn.decomposition import PCA
pca = PCA(n_components=2)
pca.fit(scaled_data)
scaled_pca = pca.transform(scaled_data)
```
Query the number of rows and columns in the scaled dataframe (rows, columns).
```
scaled_data.shape
```
Query the number of rows and columns in the scaled PCA dataframe.
```
scaled_pca.shape
```
PCA has reshaped the data from 5 features to 2 features.

### Plot data
2D plot.\
Principal component 1 is marked on the x axis.\
Principal component 2 is marked on the y axis.

State the size of the plot.
```
plt.figure(figsize=(10,8))
```
Configure the plot’s x and y axes as principal components 1 and 2, and color-coded by the variable Clicked on Ad.
```
plt.scatter(scaled_pca[:, 0],scaled_pca[:, 1],c=df['Clicked on Ad'])
```
State the plot labels.
```
plt.xlabel('First Principal Component')
plt.ylabel('Second Principal Component')
```

## k-means clustering
Use k-means clustering to split data into natural groupings.

### Import libraries
```
import numpy as np
from sklearn.datasets import make_blobs
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt
%matplotlib inline
```

### Create blobs
Generate a dataset instead of importing.\
300 samples, 2 features, 4 centers (groups) with a cluster deviation of 4.\
*What is the different between a center and cluster deviation?*\
Plot the data to check what it looks like so far.
```
X, y = make_blobs(n_samples=300, n_features=2, centers=4, cluster_std=4, random_state=10)
plt.figure(figsize=(7,5))
plt.scatter(X[:,0],X[:,1])
```
![blob plot](/images/practical/blob-plot.png)

### Set algorithm
Use k-means clustering to find 4 groups of points, each sharing similar attributes.
```
model = KMeans(n_clusters=4)
model.fit(X)
```

### Create groups
Generate and print the 4 centroid coordinates.\
[x y]
```
model_predict = model.predict(X)
centroids = model.cluster_centers_
print(model.cluster_centers_)
```

### Plot groups
300 points are grouped into 4.\
Reduces a dataset with a high number of points into a more manageable number of cluster centroids.
```
plt.figure(figsize=(7,5))
plt.scatter(X[:,0], X[:,1], c=model_predict, s=50, cmap='rainbow')
plt.scatter(centroids[:,0], centroids[:,1], c='black', s=200, alpha=1)
```

![cluster plot](/images/practical/cluster-plot.png)

### Scree plot
Use a scree plot to find the appropriate number of clusters.\
*Does this need to happen before we specify the number of clusters?*\
Visualises the degree of scattering (variance) by comparing the distortion for each variation of clusters.\
Distortion is the distance between the centroid and other points in the cluster.\
To determine the optimal number of clusters, we select the value of k where distortion subsides to the left of the plot before it reaches a point of negligible change with the cluster variations to the right.\
From the optimal point (elbow point), distortion starts decreasingly linearly to the right.\
The optimal number is 4.\
This is the same number of centers used to generate the dataset.

![scree plot](/images/practical/scree-plot.png)

```
distortions = []

K = range(1,10)

for k in K:
    model = KMeans(n_clusters=k)
    model.fit(X,y)
    distortions.append(model.inertia_)

plt.figure(figsize=(16,8))
plt.plot(K, distortions)
plt.xlabel('k')
plt.ylabel('Distortion')
plt.show()
```