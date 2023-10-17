# Support vector machines (SVM)
Supervised learning.\
Classification technique.\
Predicts categorical outcomes.\
Similar to logistic regression.

In binary prediction, SVM mirrors logistic regression.\
Attempts to separate classes based on the mathematical relationship between variables.

SVM is superior to logistic regression because it attempts to separate data classes from a position of maximum distance between itself and partitioned points.

![SVM vs. logistic regression](/images/practical/svm-vs-logistic.png)

The key feature of SVM is the **margin**.\
The margin is the distance between the boundary line and the nearest data point, multiplied by two.\
The margin handles new points and outliers which would otherwise infringe on a logistic regression boundary line.

## Import libraries
```
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.svm import SVC
from sklearn.metrics import classification_report, confusion_matrix
from sklearn.model_selection import GridSearchCV
```

## Import dataset
Dataset is located at `~\practical\data\advertising.csv`.
```
df = pd.read_csv('~/Downloads/advertising.csv')
```

## Data scrubbing
Remove variables.
```
del df['Ad Topic Line']
del df['Timestamp']
```
Convert non-numeric variables.
```
df = pd.get_dummies(df, columns=['Country','City'])
```

## Split validation
**Clicked on Ad** is the dependent variable.
```
X = df.drop('Clicked on Ad', axis=1)
y = df['Clicked on Ad']

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=10)
```

## Set algorithm
```
model = SVC()

model.fit(X_train, y_train)
```

## Evaluate
```
model_predict = model.predict(X_test)
```

Generate a confusion matrix and classification report to evaluate the results of the model.
```
print(confusion_matrix(y_test, model_predict))
```
```
print(classification_report(y_test, model_predict))
```