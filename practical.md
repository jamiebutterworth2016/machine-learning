# Development environment
  
## Install Jupyter Notebook in Windows
- Install Python from [Link.](https://www.python.org/ftp/python/3.11.4/python-3.11.4-amd64.exe)
  - Also installs pip for you - the package manager required to install Jupyter Notebook.
- Open command prompt **as admin**.
- Install Jupyter Notebook (web app): `pip install notebook`
- Install pandas (Python library for ML): `pip install pandas`
- Launch Notebook with `jupyter notebook`
- This will open Notebook in a browser, address `http://localhost:8888/tree?token=569606a2396416d72985548e78f5138e84b655ccfd379fdd`

## Create a new notebook
- Click `New` and `Notebook` to create a notebook project.
- Select `Python 3` as the kernel.
- Each line is a cell.
- To run all cells, go to `Run > Run All Cells`.

![new notebook](/images/practical/new-notebook.PNG "new notebook")

## Read a dataset
- Download the dataset from [kaggle.com](https://www.kaggle.com/anthonypino/melbourne-housing-market/) and extract the files.
- Add these three cells:
```
import pandas as pd

df = pd.read_csv('~/Downloads/Melbourne_housing_FULL.csv')

df.head(10)
```

- Run the cells with `Run > Run All Cells` to load the dataset and view the first 10 rows.

## Find a specific row
- In ML, we often need to find a specific row.
- E.g. if the model finds that row 101 is the most suitable house to recommend to a buyer, we need to see that house.
- We're finding by index. The data is zero-indexed. Row 101 = index 100.
```
df.iloc[100]
```
Outputs
```
Suburb                         Airport West
Address                        180 Parer Rd
Rooms                                     3
Type                                      h
Price                              830000.0
Method                                    S
SellerG                               Barry
Date                             16/04/2016
Distance                               13.5
Postcode                             3042.0
Bedroom2                                3.0
Bathroom                                1.0
Car                                     2.0
Landsize                              971.0
BuildingArea                          113.0
YearBuilt                            1960.0
CouncilArea      Moonee Valley City Council
Lattitude                          -37.7186
Longtitude                          144.876
Regionname             Western Metropolitan
Propertycount                        3464.0
Name: 100, dtype: object
```

## Printing columns
- Sometimes we need to configure which columns to select, modify or remove from the model.
- Print the column names with this command:
```
df.columns
```
Outputs
```
Index(['Suburb', 'Address', 'Rooms', 'Type', 'Price', 'Method', 'SellerG',
       'Date', 'Distance', 'Postcode', 'Bedroom2', 'Bathroom', 'Car',
       'Landsize', 'BuildingArea', 'YearBuilt', 'CouncilArea', 'Lattitude',
       'Longtitude', 'Regionname', 'Propertycount'],
      dtype='object')
```

# Building a model in Python

## 1. Import libraries and dataset
- Import Pandas.
- Import functions from Scikit-learn.
  - Gradient boosting (ensemble).
  - Absolute error to evaluate performance.
- Load the dataset into the dataframe.
```
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn import ensemble
from sklearn.metrics import mean_absolute_error

df = pd.read_csv('~/Downloads/Melbourne_housing_FULL.csv')
```

## 2. Scrub dataset
Scrubbing is the process of refining the dataset.\
Fix spelling mistakes and simple errors in the CSV source file before importing the dataset.\
Perform major structural changes in the development environment.

### 2a. Remove unwanted columns
```
del df['Address']
del df['Method']
del df['SellerG']
del df['Date']
del df['Postcode']
del df['Lattitude']
del df['Longtitude']
del df['Regionname']
del df['Propertycount']
```

### 2b. Remove missing values
There are a number of methods to manage missing values.
- Populate empty cells with the dataset's mean value.
- Median value.
- Delete the rows with missing values entirely.
```
df.dropna(axis = 0, how = 'any', thresh = None, subset = None, inplace = True)
```
![dropna parameters](/images/practical/dropna-parameters.PNG "dropna parameters")

### 2c. Convert text to number columns (one-hot encoding)
```
df = pd.get_dummies(df, columns = ['Suburb', 'CouncilArea', 'Type'])
```

### 2d. Assign dependent and independent variables to columns
```
X = df.drop('Price',axis=1)
y = df['Price']
```

## 3. Split dataset
Split the data into training and test data.\
Standard 70/30 split.\
Use the Scikit-learn command.
```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.3, shuffle = True)
```

## 4. Create model with algorithm and parameters
The algorithm is ensemble's gradient boosting regressor.

TODO: explain each parameter
```
model = ensemble.GradientBoostingRegressor( n_estimators = 150, learning_rate = 0.1, max_depth = 30, min_samples_split = 4, min_samples_leaf = 6, max_features = 0.6, loss = 'huber' )

model.fit(X_train, y_train)
```

## 5. Evaluate results


# Algorithm parameters
Gradient boosting parameters

## n_estimators
- The number of trees.
- More trees improves prediction accuracy (up to a certain point) at the cost of increased processing time.
- Use 150 trees as an initial starting point.

## learning_rate
- The rate which additional trees influence the prediction.
- Use a low rate of 0.1 to improve accuracy.

## max_depth
- The maximum number of layers of each tree.
- "None" = nodes expand until all leaves are pure or all leaves contain less than min_samples_leaf.
- Use high number of 30.
- More layers = higher accuracy?

## min_samples_split
- The minimum number of samples required to execute a new binary split (create a new branch).

## min_samples_leaf
- Helps mitigate outliers. Outliers result in a low number of samples foudnd in one leaf as a result of a binary split.
- Low number of samples results in a branch not being created. Therefore, outliers are disposed of and don't affect the prediction.
- If set to 4, a sample size of 3 or lower (found in a leaf) will be disposed of.

## max_features
- Total number of features presented to the model to determine the best split.
- Random forests and gradient boosting restrict the number of features fed to each tree to create multiple results that can be voted on later.
- If the value is an integer (whole number), the model considers max_features at each split (branch).
- If the value is a float (e.g. 0.6), max_features is the percentage of total features randomly selected.
- Etc. More to write here.

## loss
- huber protects against outliers.

Train the prediction model by feeding the training data into the model.
```
model.fit(X_train,y_train)
```

# Evaluate the results
- `X_train` is training data used to train the model.
- `y_train` is the correct training data.
- We're using mean absolute error to evaluate the model's accuracy.
- Pass the `X_train` training data to the model for it to output predictions.
```
predictions = model.predict(X_train)
```
- Compare the `predictions` with the correct data `y_train`.
```
mae_train = mean_absolute_error(y_train,predictions)
print ("Training Set Mean Absolute Error: %.2f" % mae_train)
```