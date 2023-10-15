# Logistic regression
Generally used for binary classification.\
Support vector machines are used to classify points into three or more classes.\
When predicting a qualitative outcome (class), the task is a classification problem.\
Part of the regression family.\
Analyses quantitative relationships between variables.\
Accepts both continuous and discrete variables.\
Outputs qualitative values - a discrete class, e.g. Yes/No or Customer/Non-customer.

## Sigmoid function
A sigmoid function is used to classify points.\
Assigns probabilties to discrete outcomes.\
Converts numerical results into a probability between 0 and 1.\
A value of 0 represents no chance of occuring.\
1 represents a chance of occuring.\
For binary predictions, we assign two discrete classes with a cut-off point of 0.5.\
Anything above 0.5 is classified as class A.\
Anything below 0.5 is classified as class B.

![Sigmoid function](/images/practical/sigmoid-function.png)

## Hyperplane

After assigning points to a class using the Sigmoid function, a hyperplane is used as a decision boundary to split the two classes.\
The boundary is then used to predict the class of future points.

![Hyperplane](/images/practical/hyperplane.png)

## Import libraries
```
import pandas
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import confusion_matrix, classification_report
```

## Import dataset
The dataset is at `/practical/datasets/18k_Projects.csv`\
[Alternative download link](https://www.kaggle.com/tayoaki/kickstarter-dataset)
```
df = pd.read_csv('~/Downloads/18k_Projects.csv')
```
![Kickstarter dataset](/images/practical/kickstarter-dataset.png)

## Data scrubbing and analysis

### Remove variables
Some of these variables are strings or timestamps which cannot be parsed as numbers.
```
del df['Id']
del df['Name']
del df['Url']
del df['Location']
del df['Pledged']
del df['Creator']
del df['Category']
del df['Updates']
del df['Start']
del df['End']
del df['Latitude']
del df['Longitude']
del df['Start Timestamp (UTC)']
del df['End Timestamp (UTC)']
del df['Creator Bio']
del df['Creator Website']
```

### One-hot encoding
Logistic regression can only read numbers.\
Convert categorical features (non-numbers) into numbers.\
```
df = pd.get_dummies(df, columns=['State','Currency','Top Category','Facebook Connected','Has Video'], drop_first = True)
```

Check the shape. Output (rows, columns) should be `(18142,36)`.
```
df.shape
```

### Remove and fill missing values
Check for independent variables with missing values.
```
df.isnull().sum()
```
**Facebook Friends** - 5852\
**Creator - # Projects Backed**  - 4244\
**# Videos** - 101\
**# Words (Risks and Challenges)** - 101

The dependent variable will be **State_successful**.

For each variable with missing values, check for the correlation between the variable and the dependent variable.
```
df['State_successful'].corr(df['Facebook Friends'])
df['State_successful'].corr(df['Creator - # Projects Backed'])
df['State_successful'].corr(df['# Videos'])
df['State_successful'].corr(df['# Words (Risks and Challenges)'])
```
**Facebook Friends** - 0.160\
**Creator - # Projects Backed**  - 0.106\
**# Videos** - 0.056\
**# Words (Risks and Challenges)** - 0.007

**Facebook Friends** and **Creator - # Projects Backed** have a high number of missing values but they are significant for analysis because they are strongly correlated to **State_successful**.

**# Videos** and **# Words (Risks and Challenges)** are weakly correlated to **State_successful** but they have very few missing values.\
Therefore we can simply remove the rows which are missing those values.\
It would be excessive to remove the entire variable.