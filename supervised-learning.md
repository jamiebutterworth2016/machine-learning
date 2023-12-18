# Semi-supervised learning
Tables don't usually start with a classification column.\
Use unsupervised learning first to generate a classification column.\
Then use supervised learning to then make predictions.

# Supervised learning
Supports both numeric predictions and classification.\
Classification appears to be the most useful.

Both inputs and output are known.

1. I take the output.
2. I take the inputs which created the output.
3. I discover the relationship between the inputs and the output.
4. I use this relationship to predict the output of future inputs.

| Algorithm                     | Used for                 |
| ----------------------------- | ------------------------ |
| Linear regression             | Numeric predictions      |
| Logistic regression           | Classification           |
| k-nearest neighbours (k-NN)   | Classification           |
| Support vector machines (SVM) | Classification           |


</br>

## 1. Linear regression

| Season (Input / X) | Viewers (Output / y) |
| ------------------ | -------------------- |
| 1                  | 19                   |
| 2                  | 18                   |
| 3                  | 17                   |
| 4                  | 20                   |
| 5                  | 29                   |
| 6                  | 31                   |
| 7                  | 33                   |
| 8                  | 32                   |
| 9                  | 38                   |

<br/>

- The graph is a *scatterplot*. The line is a *hyperplane* we use to make **numeric predictions**.
- I can find an input (X) and follow the line to see where the output (y) will be. This is the *linear relationship* between input and output.
- The nearer the value is to the line (vertically), the more accurate the model's predictions are.
- The distance between the line and a value is the *error*.
- I can predict an output by choosing an input on the X axis, going up to the line and reading the output on the y axis.
- _It is difficult to use linear regression on tables with too few numeric columns._

![linear regression](/images/linear%20regression.png "linear regression")

</br>

### Multiple linear regression
- Multiple inputs, single output.
- The output must be a number.
- Inputs can be categorical variables (e.g. gender) but but must be expressed numerically (0 or 1), not as strings ("male", "female").
- Companies more likely to want to map many inputs to a predicted output.

![multiple linear regression](/images/multiple%20linear%20regression.PNG "multiple linear regression")

<br/>

## 2. Logistic regression
- Classification technique.
- The logistic hyperplane is a classification boundary which **splits data into two classes**.
- Uses the sigmoid function to find the probability of inputs producing classified outputs.

```
y = 1 / 1 + e^-x

e = 2.718 (Euler's constant) 
```

- The sigmoid function produces an S-shaped curve.
- Converts an input into to a number between 0 and 1, in relation to the output.
- 0 to 1 is an expression of probability.
- 0 = no chance of occurring.
- 1 = chance of occurring.
- Data points 0.5 to 1 are assigned to class A.
- Data points 0 to 0.5 are assigned to class B.
- The sigmoid function rarely produces exactly 0.5 (unclassifiable).
- The output is not placed along the y-axis.
- The output is the position of the point in relation to the hyperplane, which determines the classification of the inputs.

*Sigmoid function splitting points into two classes.*

![sigmoid function](/images/sigmoid.PNG "sigmoid function")

![classified](/images/logistic%20regression%20classified%202.png "classified")

### Multinomial logistic regression
- For when the output can be more than two classes.
- Logistic regression's strength is binary prediction, other  
classification algorithms like descition trees or support vector machines may be a better option for solving multiclassification.
- Data should be free of missing values.
- Inputs should not be strongly correlated with each other.
- At least 30 points for each output to ensure high accuracy.

![multinomial logistic regression](/images/multinomial%20logistic%20regression.PNG "multinomial logistic regression")

<br/>

## 3. k-nearest neighbours (k-NN)
- Classification technique.
- Classifies new points relative to how near they are to existing points.
- k is the number of existing points we use to determine which class a new point belongs to.
- k must be an uneven number.
  
1. I set k to 3.
2. A new point is placed on the graph.
3. I find the new point's 3 nearest neighbouring points.
4. I note the class of each neighbouring point.
5. The new point belongs to the class with the most neighbouring points. E.g. 1 neighbouring point belongs to class A. 2 neighbouring points belong to class B. The new point belongs to class B.

![k-nearest neighbours](/images/k-nearest%20neighbours.PNG "k-nearest neighbours")

- Test different k combinations to find the best fit.
- Setting k too low, results in misclassification.
- Setting k is too high is computationally expensive. Calculating the distance between a new point and all existing points is expensive.
- Setting k to an uneven number eliminates the possibility of a stalemate.
- 5 is the default when using Scikit-learn.
- k-NN is not recommended for large datasets.

<br/>

## 4. Support Vector Machines (SVM)
- Classification technique used to categorise outputs.
- Similar to logistic regression but more emphasis on the line's location.
- Both techniques use a line to separate the points but positions the line differently.
- Logistic regression **minimises** the distance between all points and the line.
- SVM **maximises** the distance (margin) between all points and the line.

![svm-vs-logistic](/images/svm.PNG "svm vs logistic")
