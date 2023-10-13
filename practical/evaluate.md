# Evaluate

Evaluate the results.\
The evaluation method depends on your model type: regression model or classification model.

## Regression model
Two common measures:
- Mean absolute error (MAE)
- Root mean square error (RMSE)

### Mean absolute error
Measure the average of the errors in a set of predictions.\
I.e. how far the regression line is to the points.

### Root mean square error
Measures the standard deviation of prediction errors.\
Informs how spread out the prediction errors are in relation to an optimal fit.

## Classification model
Common evaluation methods:
- Accuracy score
- Confusion matrix
- Classification report

### Accuracy score
A starting point and simple metric which measures the number of cases the model classified correctly divided by the total number of cases.

If all the cases are correct, the accuracy score is 1.0.\
If none of the cases are correct, The score is 0.

Warning: normally reliable but can hide a lopsided number of false-positives or false-negatives.\
This isn't an issue if the number of both is balanced.

### Confusion matrix
Also known as error matrix.\
Simple table which summarises the model's performance.\

Top left - 134 points were predicted correctly as 0.\
Bottom right - 125 points were predicted corrently as 1.\
Top right - 12 points were predicted incorrectly as 1. Should've been 0. These are false positives.\
Bottom left - 29 were predicted incorrectly as 0. Should've been 1. These are false negatives.

![Confusion matrix](/images/practical/confusion-matrix.png)

(false positives + false negatives) / total data points

(12 + 29) / 300 = 0.1366

13.66% of points have been misclassified.

86.34% is the accuracy score of the model.

### Classification report
Generates three evaluation metrics:
- Precision
- Recall
- F1-score

#### Precision
Precision = number of true positives / number of predicted positive cases

A low precision score means a low number of false positives.

The ability of the model not to label a negative case as positive.

#### Recall
How many positive outcomes were correctly classified as positive?

Recall = number of true positives / number of actual positive cases.

The ability of the model to identify all positive cases.

#### F1-score
The weighted average of precision and recall.
Used as metric for model-to-model comparison instead of standalone model accuracy.

#### Support
Not an evaluation metric.
A tally of the number of positive and negative cases respectively.