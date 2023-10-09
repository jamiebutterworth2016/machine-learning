# Pre-model algorithms
An extension of data scrubbing.\
Unsupervised learning algorithms can be used to clean and reshape data.\
This occurs before the use of a supervised learning algorithm to build the model.\
Examples are dimension reduction techniques and k-means clustering.

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

![x-axis](/images/practical/x-axis.PNG)

The y axis is perpdendicular to the X axis.

Forms an orthogonal line which is used to create the first two components.
TODO: more.


## Practical
https://www.kaggle.com/fayomi/advertising/data/

pip install scikit-learn

```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
%matplotlib inline

df = pd.read_csv('~/Downloads/advertising.csv')
df.head()

del df['Ad Topic Line']
del df['City']
del df['Country']
del df['Timestamp']
del df['Male']
```

Standardise features by using zero as the mean for all variables and scaling to unit variance.
```
#Import StandardScaler
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
scaler.fit(df)
scaled_data = scaler.transform(df)

from sklearn.decomposition import PCA
pca = PCA(n_components=2)
pca.fit(scaled_data)
scaled_pca = pca.transform(scaled_data)
```
Query the number of rows and columns in the scaled dataframe (rows, columns)
```
scaled_data.shape
```
Query the number of rows and columns in the scaled PCA dataframe
```
scaled_pca.shape

#State the size of the plot
plt.figure(figsize=(10,8))

#Configure the scatterplot’s x and y axes as principal components 1 and 2, and color-coded by the variable Clicked on Ad.
plt.scatter(scaled_pca[:, 0],scaled_pca[:, 1],c=df['Clicked on Ad'])

#State the scatterplot labels
plt.xlabel('First Principal Component')
plt.ylabel('Second Principal Component')
```