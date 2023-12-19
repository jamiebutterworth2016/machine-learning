# Setting up the development environment
[Create Jupyter Notebook project](create-jupyter-notebook-project.md)\
[Helpful commands](helpful-commands.md)
[Helpful libraries](import-libraries.md)

# Model design flow
1. [Import dataset](import-dataset.md)
2. [Exploratory data analysis](exploratory-data-analysis.md) (optional)
3. [Data scrubbing](data-scrubbing.md)
4. [Pre-model algorithm - unsupervised learning](pre-model-algorithms.md) (optional)
5. [Split validation](split-validation.md)
6. [Set algorithm - supervised learning](algorithms.md)
7. Predict
8. [Evaluate](evaluate.md)
9. Optimise


## Optimise
For a clustering analysis technique, this could mean going back and modifying the number of clusters.\
For a tree-based learning technique, this could mean tweaking the parameters.\
Can be performed manually with trial error.\
Or automatically using a method like grid search.








## Assign dependent and independent variables to columns
```
X = df.drop('Price',axis=1)
y = df['Price']
```


## 4. Create model with algorithm and parameters
The algorithm is ensemble's gradient boosting regressor.

TODO: explain each parameter
```
model = ensemble.GradientBoostingRegressor( n_estimators = 150, learning_rate = 0.1, max_depth = 30, min_samples_split = 4, min_samples_leaf = 6, max_features = 0.6, loss = 'huber' )

model.fit(X_train, y_train)
```

## 5. Evaluate results


# Algorithm parameters
Gradient boosting parameters

## n_estimators
- The number of trees.
- More trees improves prediction accuracy (up to a certain point) at the cost of increased processing time.
- Use 150 trees as an initial starting point.

## learning_rate
- The rate which additional trees influence the prediction.
- Use a low rate of 0.1 to improve accuracy.

## max_depth
- The maximum number of layers of each tree.
- "None" = nodes expand until all leaves are pure or all leaves contain less than min_samples_leaf.
- Use high number of 30.
- More layers = higher accuracy?

## min_samples_split
- The minimum number of samples required to execute a new binary split (create a new branch).

## min_samples_leaf
- Helps mitigate outliers. Outliers result in a low number of samples foudnd in one leaf as a result of a binary split.
- Low number of samples results in a branch not being created. Therefore, outliers are disposed of and don't affect the prediction.
- If set to 4, a sample size of 3 or lower (found in a leaf) will be disposed of.

## max_features
- Total number of features presented to the model to determine the best split.
- Random forests and gradient boosting restrict the number of features fed to each tree to create multiple results that can be voted on later.
- If the value is an integer (whole number), the model considers max_features at each split (branch).
- If the value is a float (e.g. 0.6), max_features is the percentage of total features randomly selected.
- Etc. More to write here.

## loss
- huber protects against outliers.

Train the prediction model by feeding the training data into the model.
```
model.fit(X_train,y_train)
```

# Evaluate the results
- `X_train` is training data used to train the model.
- `y_train` is the correct training data.
- We're using mean absolute error to evaluate the model's accuracy.
- Pass the `X_train` training data to the model for it to output predictions.
```
predictions = model.predict(X_train)
```
- Compare the `predictions` with the correct data `y_train`.
```
mae_train = mean_absolute_error(y_train,predictions)
print ("Training Set Mean Absolute Error: %.2f" % mae_train)
```
