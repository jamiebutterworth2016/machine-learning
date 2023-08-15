# 16. Development environment
- Python - language
- Jupyter Notebook - web app
- Install Jupyter with Anaconda Distribution or Python's package manager, pip.
- Install Anaconda - access to data science apps - Jupyter, rstudio, graphviz (for visuals).
- In the terminal, initiate Jupyter with `jupyter notebook` to generate a url, e.g. `http://localhost:8888/`.
- Click `New` to create a notebook project.
- Select `Python 3`.
- Import Pandas, a Python library for ML - `import pandas as pd`.
- Get dataset from [kaggle.com](https://www.kaggle.com/anthonypino/melbourne-housing-market/) and unzip.
- To run code in Jupyter, go to `Cell > Run All`.
- Use this code to load and view first 10 rows of the dataset:
```
df = pd.read_csv('~/Downloads/Melbourne_housing_FULL.csv')

df.head(10)
```

- In ML, you often need to locate a specific row by matching a row number with its row information.
- E.g. if the model finds that row 100 is the most suitable house to recommend to a buyer, we need to see which house that is, in the dataframe.
```
df.iloc[100]
```

- Sometimes, you'll need to configure which columns to select, modify or remove from the model.
- You can print the column names with this command:
```
df.columns
```

# 17. Building a model in Python
- 


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