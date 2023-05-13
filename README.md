# machine-learning
Machine learning notes



# 6. Data scrubbing
- The clean-up prcess.
- Refine the dataset to make it more workable.
- Modify bad data.
- Remove incomplete, incorrectly formatted, irrelevant, duplicated data.
- Convert strings to numbers.

## Feature selection
- Idenfify which columns you want in your model.
- Reduce the number of columns as much as possible to make the model more simple and accurate.
- Remove irrelevant columns. They cause over-complication and inaccuracy.
- Remove duplicate columns.
- Merge columns.

- Before merge:

|   | Apples | Oranges | Carrots | Peas |
|---|--------|---------|---------|------|
| 1 | 1      | 0       | 0       | 0    |
| 2 | 1      | 1       | 0       | 0    |
| 3 | 0      | 1       | 1       | 1    |


- After merge:

|   | Fruit | Veg |
|---|-------|-----|
| 1 | 1     | 0   |
| 2 | 2     | 0   |
| 3 | 1     | 2   |

## Row compression
- Reduce the number of rows to simplify the dataset.
- "Tiger" and "Lion" can be merged and renamed as "Carnivore" because they have too similar vectors.

- Before merge:

|          | Meat Eater | Legs | Tail | Race Time  |
|----------|------------|------|------|------------|
| Tiger    | 1          | 4    | 1    | 2:01 mins  |
| Lion     | 1          | 4    | 1    | 2:05 mins  |
| Tortoise | 0          | 4    | 0    | 55:02 mins |

- After merge:

|           | Meat Eater | Legs | Tail | Race Time  |
|-----------|------------|------|------|------------|
| Carnivore | 1          | 4    | 1    | 2:03 mins  |
| Tortoise  | 0          | 4    | 0    | 55:02 mins |

## One-hot encoding
- 

# 7. Setting up the data
- Split the data into two segments. 70% into training data. 30% into test data.
- Randomise the rows to remove any ordering of the data. If any columns are ordered, this can cause bias. _Expand_
- Design the model and apply the model to the training data.
- Test data is put to the side and used later to test the accuracy of the model.
- Do not test the model with the same data used for training the model.

## Supervised learning
- Feed the model with the training data.
- Analyse the relationships between the input data (X) and the output data (y).
- Use a performance metric to measure how the model performed.
- Mean absolute error (MAE) is the metric we'll use here.
- Using Scikit-learn, MAE is found by inputting X values from the training data into the model and generating a prediction for each row in the dataset.
- Scikit-learn compares the predictions of the model to the correct output (y) and measures the model's accuracy.
- The model is accurate when the error rate is low.
- High accuracy means the model has learnt the data's patterns.