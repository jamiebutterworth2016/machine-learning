# Linear regression

[Theory](/theory/supervised-learning/linear-regression.md)

## Preparation
1. Start with a table which has at least two numeric columns.
2. Remove or fill missing values.
3. Choose the independent variables which correlate most wth the dependent variable.

_If a strong linear correlation exists between two or more independent variables, this leads to a problem called collinearity where individual variables are not unique.\
You can still rely on the model's accuracy but you won't know which similar variables are influential and which are redundant._

## Libraries required
- pandas
- seaborn
- sklearn

## Import libraries
```
%matplotlib inline
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn import metrics
```

## Import dataset
If you don't already have a table, you can use the example dataset at `/practical/datasets/Melbourne_housing_FULL.csv`\
[Alternative download link](https://www.kaggle.com/anthonypino/melbourne-housing-market/#Melbourne_housing_FULL.csv)
```
import pandas as pd
df = pd.read_csv('~/Downloads/Melbourne_housing_FULL.csv')
```

## Data scrub and analysis
Remove non numeric columns.\
For the remaining numeric columns, keep a small number of numeric columns which explain a large proportion of variance. _Explain!_\
Remove the rest.
```
del df['Address']
del df['Method']
del df['SellerG']
del df['Date']
del df['Postcode']
del df['YearBuilt']
del df['Type']
del df['Lattitude']
del df['Longtitude']
del df['Regionname']
del df['Suburb']
del df['CouncilArea']
```

Check the shape of the dataset - the number of rows and columns (features).
```
df.shape
```

Check for missing values (NaN).
```
def.head()
```

Check the total number of missing values.
```
df.isnull().sum()
```

## Reduce numeric columns down to two
Use a heatmap to analyse the correlation between numeric columns.
```
df_heat = df.corr()
import seaborn as sns
sns.heatmap(df_heat, annot=True, cmap='coolwarm')
```

![heatmap](/images/practical/heatmap.png)

The dependent variable is **Price**. The others are independent variables.\
Use the methods below to remove independent variables until we only have two left.

### Independent variables should not be strongly correlated with each other
The high red numbers indicate those two independent variables are strongly correlated.\
The heatmap shows **Bedroom2** is highly correlated with **Rooms** - 0.95.\
One of these independent variables needs to be removed.\
Find a reason to remove one of these variables.\
Example: Remove **Bedroom2** as it is missing a lot of values.
```
del df['Bedroom2']
```

### Remove independent variables with a low correlation to the dependent variable
The dependent variable is **Price**.\
Independent variables **Landsize** and **Propertycount** can be removed because they have a very low correlation to **Price**.
```
del df['Bedroom2']
del df['Landsize']
del df['Propertycount']
```

### Remove independent variables with high number of missing rows
Remove **BuildingArea** as it has a high number of missing rows - 21,115.\
**BuildingArea** also has low correlation with dependent variable **Price** - another reason to remove **BuildingArea**.
```
del df['BuildingArea']
```

### Fill missing values with mean
Use the mean to fill variables with partial correlation to dependent variable **Price**.

Avoid filling values to variables with significant correlation to dependent variable **Price** and instead remove those missing values row-by-row.

```
df['Car'].fillna(df['Car'].mean(), inplace=True)
```

### Remove rows for variables with small number of missing values
This is a better option than removing an entire variable when it only has a small number of missing values.\
This is also a better option than artificially filling values with mean values.\
**It's important to remove rows only after removing variables and filling missing values to preserve more rows.**
```
df.dropna(axis=0, how='any', thresh=None, subset=None, inplace=True)
```

Check the remaining number of rows.\
20800 is enough rows to build the model.
```
df.shape
```

## Split validation
Assign X and y variables.
```
X = df[['Rooms','Distance','Bathroom','Car']]
y = df['Price']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=10)
```

## Set algorithm
```
model = LinearRegression()

model.fit(X_train, y_train)
```

Find y intercept.\
Result should be `282725.3156777688`
```
model.intercept_
```

Find X coefficients.\
Result should be `array([269450.10790036,-37787.76622417,207173.05927097,47417.17159475])`
```
model.coef_
```

Tidy X coefficients using two column table.
```
model_results = pd.DataFrame(model.coef_, X.columns, columns=['Coefficients'])

model_results
```

## Predict
Run the model to value an individual property by creating a new variable new_house.
```
new_house = [
    2,#Rooms
    2.5,#Distance
    1,#Bathroom
    1,#Car
]

new_house_predict = model.predict([new_house])

new_house_predict
```

Result should be `array([981746.34678378])`\
The predicted value of this house is $981,746.347.\
The actual value is $1,480,000.

## Evaluate
Use mean absolute error to compare the difference between the expected price prediction and the actual price.
```
prediction = model.predict(X_test)

metrics.mean_absolute_error(y_test, prediction)
```

The MAE should be `363782.9423236326`.\
This means on average, the model miscalculated the actual price by $363,782.\
This could be because we removed too many variables from the original dataset.\
We could rebuild the model by including variables like **Type** with one-hot encoding.\
Linear regression models are fast to build but not known for accuracy.\
There are better algorithms for accuracy.
