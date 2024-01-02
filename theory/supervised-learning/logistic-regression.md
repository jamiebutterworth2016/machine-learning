# Logistic regression
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

## Multinomial logistic regression
- For when the output can be more than two classes.
- Logistic regression's strength is binary classification. Decision trees or support vector machines may be better algorithms for multiclassification.
- Inputs should not have missing values.
- Inputs should not be strongly correlated with each other.
- There should be at least 30 inputs for each output to ensure high accuracy. _To confirm._

![multinomial logistic regression](/images/multinomial%20logistic%20regression.PNG "multinomial logistic regression")
