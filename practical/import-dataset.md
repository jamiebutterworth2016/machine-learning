# Import dataset

## Public dataset
Public datasets are available at kaggle.com.\
Load the dataset into the dataframe.
```
import pandas as pd

df = pd.read_csv('~/Downloads/Melbourne_housing_FULL.csv')
```

## Scikit dataset

Scikit offers small built-in datasets which don't require downloading.

![scikit dataset](/images/practical/scikit-datasets.png)

```
from sklearn.datasets import load_breast_cancer

cancer = load_breast_cancer()
```

## Scikit blob

Scikit can be used to generate a random dataset called a blob.
```
from sklearn.datasets import make_blobs

data = make_blobs(n_samples=200, n_features=2, centers=4, cluster_std=1.8, random_state=101)
```

![blob parameters](/images/practical/blob-parameters.png)
