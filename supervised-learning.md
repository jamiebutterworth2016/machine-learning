# Supervised learning
Both inputs and output are known.

1. I take the output.
2. I take the inputs which created the output.
3. I discover the relationship between the inputs and the output.
4. I use this relationship to predict the output of future inputs.

<br/>

# Supervised learning algorithms

## Linear regression

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

- The graph is a *scatterplot*. The line is a *hyperplane*.
- I can find an input (X) and follow the line to see where the output (y) will be. This is the *linear relationship* between input and output.
- The nearer the value is to the line (vertically), the more accurate the model's predictions are.
- The distance between the line and a value is called the *error*.
- I can predict an output by choosing an input on the X axis, going up to the line and reading the output on the y axis.

![linear regression](/linear%20regression.png "linear regression")

</br>

## Multiple linear regression
- Multiple inputs, single output.
- The output must be a number.
- Inputs can be categorical variables (e.g. gender) but but must be expressed numerically (0 or 1), not as strings ("male", "female").

![multiple linear regression](/multiple%20linear%20regression.png "multiple linear regression")


## Logistic regression
- A categorisation technique to split data into two classes.
- Produces a qualitative prediction (category) rather than a quantitative prediction.
- Uses the sigmoid function to find the probability of inputs producing discrete categorised outputs.

```
y = 1 / 1 + e^-x

e = Euler's constant, 2.718
```

- The sigmoid function produces a S-shaped curve which converts any number and maps it into a number between 0 and 1.

![sigmoid function](/sigmoid.png "sigmoid function")


## K-nearest neighbours