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
The dataset is at `/practical/datasets/18k_Projects.csv`.\
[Alternative download link](https://www.kaggle.com/tayoaki/kickstarter-dataset)
```
df = pd.read_csv('~/Downloads/18k_Projects.csv')
```
![Kickstarter dataset](/images/practical/kickstarter-dataset.png)


## Data scrubbing and analysis
Logistic regression models can only read numbers.

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
Convert categorical variables (non-numbers) into numbers.
```
df = pd.get_dummies(df, columns=['State','Currency','Top Category','Facebook Connected','Has Video'], drop_first = True)
```

Check the shape. Output (rows, columns) should be `(18142,36)`.
```
df.shape()
```

### Remove and fill missing values
Find variables with missing values.
```
df.isnull().sum()
```
**Facebook Friends** - 5852\
**Creator - # Projects Backed**  - 4244\
**# Videos** - 101\
**# Words (Risks and Challenges)** - 101

The dependent variable will be **State_successful**.

For each independent variable with missing values, check the correlation between the variable and the dependent variable.
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

**# Videos** and **# Words (Risks and Challenges)** are weakly correlated to **State_successful** (bad) but they have very few missing values (good).\
Therefore we can remove the rows which are missing those values.\
It would be excessive to remove the entire variable.

**Facebook Friends** and **Creator - # Projects Backed** have a high number of missing values but they are significant for analysis because they are strongly correlated to **State_successful**.

Check the deviation and range of these variables.
```
df.describe()
```
The standard deviation (std) and range (max - min) for **Facebook Friends** are high but much lower for **Creator - # Projects Backed**.

Check the variables using a distribution plot.
```
plt.figure(figsize=(12,6))
sns.distplot(df['Facebook Friends'], kde=True, hist=0)
```
```
plt.figure(figsize=(12,6))
sns.distplot(df['Creator - # Projects Backed'], kde=True, hist=0)
```

Ideally we'd fill missing values with the mean. However, the mean is less reliable when the values are more varied.

**Facebook Friends** values are too varied for us to use the mean.\
We'll remove the rows missing the **Facebook Friends** value instead.

**Creator - # Projects Backed** values are much less varied so we can use the mean to fill missing values.
```
df['Creator - # Projects Backed'].fillna(df['Creator - # Projects Backed'].mean(), inplace=True)
```

Drop rows containing missing values.
```
df.dropna(axis=0, how='any', thresh=None, subset=None, inplace=True)
```

Check the shape. Output (rows, columns) should be `(12215,36)`\
A third of the rows have been dropped since the last time we checked the shape.
```
df.shape()
```

## Split validation
```
X = df.drop('State_successful', axis=1)
y = df['State_successful']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=10)
```

## Set algorithm
Train the model.
```
model = LogisticRegression()

model.fit(X_train, y_train)
```

## Evaluate
TODO: add more info
```
model_predict = model.predict(X_test)

print(confusion_matrix(y_test, model_predict))

print(classification_report(y_test, model_predict))
```

## Predict
```
new_project = [
    ​0, #Comments
    ​9, #Rewards
    ​2500, #Goal
    ​157, #Backers 
    31, #Duration in Days
    ​319, #Facebook Friends
    ​110, #Facebook Shares
    ​1, #Creator - # Projects Created
    ​0, #Creator - # Projects Backed
    ​0, ## Videos
    ​12, ## Images
    ​872, ## Words (Description)
    ​65, ## Words (Risks and Challenges)
    ​0, ## FAQs
    ​0, #Currency_AUD
    ​1, #Currency_CAD
    ​0, #Currency_EUR
    ​0, #Currency_GBP
    0, #Currency_NZD
    ​0, #Currency_USD
    ​0, #Top Category_Art
    ​0, #Top Category_Comics
    ​0, #Top Category_Crafts
    ​0, #Top Category_Dance
    ​0, #Top Category_Design
    ​0, #Top Category_Fashion
    ​1, #Top Category_Film & Video
    ​0, #Top Category_Food
    ​0, #Top Category_Games
    ​0, #Top Category_Journalism
    ​0, #Top Category_Music
    ​0, #Top Category_Photography
    ​0, #Top Category_Publishing
    ​0, #Top Category_Technology
    ​0, #Top Category_Theater
    ​0, #Facebook Connected_No
    ​0, #Facebook Connected_Yes
    ​0, #Has Video_No
    ​1, #Has Video_Yes
]
```
```
new_pred = model.predict([new_project])
new_pred
```
Output should be `array([1], dtype=uint8)`\
The project has been classified as **State_successful**=1.\
This means the model has predicted the new project has will reach its funding target.