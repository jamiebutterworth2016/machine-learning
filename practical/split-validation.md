# Split validation
Split the data into 3 sets: training data, test data and validation data.

**Training data** is used to build the prediction model.

**Test data** is used to assess the model's prediction accuracy.

**Validation data** is fed into the model and the feedback is ued to optimise the model's parameters.\
This happens after the model is built with the training data and before the test data.

Training data - 60%\
Test data - 20%\
Validation data - 20%

When the model's prediction accuracy has been optimised and validated against the test data, it is ready to generate predictions using real data.

```
import pandas as pd
from sklearn.model_selection import train_test_split
```

```
df = pd.read_csv('~/Downloads/advertising.csv')

X = df[['Daily Time Spent on Site', 'Age', 'Area Income', 'Daily Internet Usage', 'Ad Topic Line', 'Country']]
y = df['Clicked on Ad']
```

Split the data into training data and test data.

![Data split](/images/practical/data-split.png)

```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4, random_state=10)
```

Split the test data into test data and validation data.
```
X_test, X_val, y_test, y_val = train_test_split(X_test, y_test, test_size=0.5)
```