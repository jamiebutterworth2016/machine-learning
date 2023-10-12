## Build a decision model
1. Feed data into the model.
2. Choose an algorithm (there are hundreds to choose from!)
3. Tweak settings to reduce prediction error.

- The decision model improves its predictions based on experience.
- The more data, the more predictions the model can make.

<br/>

## Training and Test data
- Input data is split into training data and test data.
- Use the training data to build the model.
- The model makes predictions.
- When you're satisfied with the accuracy of the predictions, use the test data to test the model.

<br/><br/>

## Supervised learning
- Feed the model with the training data.
- Analyse the relationships between the input data (X) and the output data (y).
- Use a performance metric to measure how the model performed.
- Mean absolute error (MAE) is the metric we'll use here.
- Using Scikit-learn, MAE is found by inputting X values from the training data into the model and generating a prediction for each row in the dataset.
- Scikit-learn compares the predictions of the model to the correct output (y) and measures the model's accuracy.
- The model is accurate when the error rate is low.
- High accuracy means the model has learnt the data's patterns.