# Machine learning libraries
A list of the most popular Python libraries used for ML.

## Pandas
Install pandas from command prompt: `pip install pandas`\
This command also installs library NumPy.
```
import pandas as pd
```
- Manage and present a mix of data types - numeric and non-numeric data.
- Pandas = panel data.
- Creates a series of panels similar to Excel sheets.
- Organise structured data as a dataframe.
- 2D data structure (tabular dataset).
- Labelled rows and columns.
- Import CSV and manipulate without affecting source file.
- Changes occur only inside the dev env.

![pandas](/images/practical/pandas.PNG)

## NumPy
```
import numpy as np
```
- Used with Pandas.
- NumPy = numeric Python.
- Manage multi-dimensional arrays and matrices.
- Merge and slice datasets.
- Offers math functions - min, max, mean, standard deviation, variance.

## Scikit-learn
`pip install scikit-learn`
```
from sklearn.model_selection import train_test_split
from sklearn import ensemble
from sklearn.metrics import mean_absolute_error
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA
from sklearn.datasets import make_blobs
from sklearn.cluster import KMeans
from sklearn.linear_model import LinearRegression
from sklearn import metrics
```
- Shallow learning algorithms
  - Logistic regression
  - Decision trees
  - Linear regression
  - Gradient boosting
- Evaluation metrics - mean absolute error
- Data partition methods
  - Split validation
  - Cross validation
- Trains the model.
- Uses the trained model to predict test data.

![scikit](/images/practical/scikit.PNG)

## Matplotlib
`pip install matplotlib`
```
import matplotlib.pyplot as plt
%matplotlib inline
```
- Visualisation of variables.
- Generate scatterplots, histograms, pie charts, bar charts, error charts.

## Seaborn
`pip install seaborn`
```
import seaborn as sns
```
- Visualisation of variables.
- Better looking than Matplotlib.
- Generate heatmaps, cluster maps, pairplots.

## TensorFlow
- Google.
- Deep learning algorithms.
- Neural networks.
