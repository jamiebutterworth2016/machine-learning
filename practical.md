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