# Data scrubbing
Some algorithms don't recognise some data types. \
Scrubbing is the process of refining the dataset.\
Fix spelling mistakes and simple errors in the CSV source file before importing the dataset.\
Perform major structural changes in the development environment.\
Remove personal identifiers which break privacy regulations.\
Data scrubbing does not affect the source file of the dataset.

## 1. Remove unwanted columns
Remove columns which aren't compatible with a chosen algorithm or are less relevant to the target output.\
Remove duplicate columns, e.g. country and country code.\
Remove columns from the dataframe with the `del` function.
```
del df['latitude']
del df['longitude']
```

## 2. One-hot encoding
The algorithm must be able to read the data types.\
Some algorithms like regression algorithms cannot read strings so strings like categories must be converted to numbers.\
E.g. "True" and "False" to 1 and 0.
```
import pandas as pd
df = pd.read_csv('~/Downloads/listings.csv')
df = pd.get_dummies(df, columns = ['neighbourhood_group', 'neighbourhood'])
df.head()
```
One-hot encoding expands the dataframe horizontally as it adds new columns.\
You can use the `drop_first` parameter to remove unwanted columns.
```
df = pd.get_dummies(df, columns = ['neighbourhood_group', 'neighbourhood'] , drop_first = True)
```
![one hot encoding](/images/practical/one-hot-encoding.png)

## 3. Remove missing values
Missing data can be split into three categories:
- Missing completely at random (MCAR) - The value is missing and is not related to any other value.
- Missing at random (MAR) - The value is missing because of a related value, e.g. in a questionnaire, the user inputs a lengthy mandatory answer and skips a secondary optional answer. The values are related as the second answer is missing because the first answer is sufficient.
- Nonignorable - The user has purposefully ignored inputting the value because they didn't want to, e.g. tax evasion.

### Inspecting missing values
Discover how many values are missing in each column.
```
df.isnull().sum()
```
![is null sum](/images/practical/isnull-sum.PNG)

### Managing missing values
There are a number of methods to manage missing values.

#### Fill missing values with the column's mean (average) value
Use this with numbers - not strings or booleans.
```
mean_reviews = df['reviews_per_month'].mean()
df['reviews_per_month'].fillna(mean_reviews, inplace = True)
```

#### Fill missing values with the column's mode value
The mode is the most common value in the column.
```
mode_reviews = df['reviews_per_month'].mode()
df['reviews_per_month'].fillna(mode_reviews, inplace = True)
```

#### Fill missing values with a customised value
```
df['reviews_per_month'].fillna(0)
```

#### Remove missing values entirely
- For when the mean, mode or a custom value aren't valid solutions.
- Or when the missing values are only a small percentage of the column.
- Or not relevant to the analysis.
- It's better to drop rows rather than columns to retain more of the original dataframe.
```
df.dropna(axis = 0, how = 'any', thresh = None, subset = None, inplace = True)
```
![dropna parameters](/images/practical/dropna-parameters.PNG)

## 4. Dimension reduction
Also known as descending dimension algorithms.\
Transform data to a lower dimension to lessen computational resources and visualise patterns in the data.\
Dimensions are the number of variables describing the data.\
Up to four variables can be plotted on a scatterplot.\
But 2D and 3D plots are easiest to visualise patterns.\
Dimension reduction isn't a case of removing columns but rather mathematically transforming information contained in columns in a way which captures the information using fewer columns.\
Merging columns.

![3d plot](/images/practical/3d-plot.PNG)
