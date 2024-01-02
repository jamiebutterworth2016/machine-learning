# Linear regression

| Season (Input / X) | Viewers (Output / y) |
| ------------------ | -------------------- |
| 1                  | 19                   |
| 2                  | 18                   |
| ...                | ...                  |
| 9                  | 38                   |

<br/>

- The graph is a *scatterplot*. The line is a *hyperplane* we use to make **numeric predictions**.
- I can find an input (X) and follow the line to see where the output (y) will be. This is the *linear relationship* between input and output.
- The nearer the value is to the line (vertically), the more accurate the model's predictions are.
- The distance between the line and a value is the *error*.
- I can predict an output by choosing an input on the X axis, going up to the line and reading the output on the y axis.
- _It is difficult to use linear regression on tables with too few numeric columns._

![linear regression](/images/linear%20regression.png "linear regression")

## Multiple linear regression
- Multiple inputs, single output.
- The output must be a number.
- Inputs can be categorical variables (e.g. gender) but but must be expressed numerically (0 or 1), not as strings ("male", "female").
- Companies more likely to want to map many inputs to a predicted output.

![multiple linear regression](/images/multiple%20linear%20regression.PNG "multiple linear regression")
