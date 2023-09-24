# Pre-model algorithms
An extension of data scrubbing.\
Unsupervised learning algorithms can be used to clean and reshape data.\
This occurs before the use of a supervised learning algorithm to build the model.\
Dimension reduction techniques and k-means clustering are examples.

## Principal component analysis (PCA)
A popular dimension reduction technique.\
Known as general factor analysis.\
Reduce data complexity.\
Visualise data in fewer dimensions.\
Find a low-dimensional representation of the dataset which preserves the original shape as much as possible.\

### Components
PCA recreates dimensions as a linear combination of features called components.\
It then ranks components that contribute most to data patterns.\
You can then drop the components which contribute the least.\



## Practical
https://www.kaggle.com/fayomi/advertising/data/

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

#Import StandardScaler
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
scaler.fit(df)
scaled_data = scaler.transform(df)

from sklearn.decomposition import PCA
pca = PCA(n_components=2)
pca.fit(scaled_data)
scaled_pca = pca.transform(scaled_data)

#Query the number of rows and columns in the scaled dataframe
scaled_data.shape

#Query the number of rows and columns in the scaled PCA dataframe
scaled_pca.shape

#State the size of the plot
plt.figure(figsize=(10,8))

#Configure the scatterplot’s x and y axes as principal components 1 and 2, and color-coded by the variable Clicked on Ad.
plt.scatter(scaled_pca[:, 0],scaled_pca[:, 1],c=df['Clicked on Ad'])

#State the scatterplot labels
plt.xlabel('First Principal Component')
plt.ylabel('Second Principal Component')
```