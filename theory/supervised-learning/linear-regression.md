# Linear regression

| Season (Input / X) | Viewers (Output / y) |
| ------------------ | -------------------- |
| 1                  | 19                   |
| 2                  | 18                   |
| ...                | ...                  |
| 9                  | 38                   |

<br/>

![linear regression](/images/linear%20regression.png)

- The model requires a table with two numeric columns.
- The data points are plotted on a graph called a *scatterplot*.
    - The x axis is used for the first column.
    - The y axis is used for the second column.
- The model generates a line called a *hyperplane*.
- The line is positioned with minimal distance between the line and each data point.
- The model can then use this line to make **numeric predictions**.
- You can find a value on the x axis (input) and vertically trace upwards until you reach the line. When you reach the line, you go to the left until you reach the y axis. The value of the y axis is a prediction of the input value's corresponding output value.
- This is the *linear relationship* between input and output.
- The nearer the data point is to the line (vertically), the more accurate the predictions is.
- The distance between the line and the data point is the *error*.
- I can predict an output by choosing an input on the X axis, going up to the line and reading the output on the y axis.

## Multiple linear regression
- Multiple inputs, single output.
- The output must be a number.
- Inputs can be categorical variables (e.g. gender) but but must be expressed numerically (0 or 1), not as strings ("male", "female").
- Companies more likely to want to map many inputs to a predicted output.

![multiple linear regression](/images/multiple%20linear%20regression.PNG "multiple linear regression")
