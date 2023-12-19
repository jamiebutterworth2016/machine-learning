# Exploratory data analysis (EDA)
- Manage data with Pandas.
- Visualise data with Seaborn.
- Common EDA techniques.
- Summarise the important characteristics of the dataset to preare for further processing and analysis.
- Become familiar with the data, e.g. distribution and the state of missing values.

## Requirements
- [Create new project](create-jupyter-notebook-project.md)
- Get the dataset.
  - [Download Airbnb dataset from Kaggle.](https://www.kaggle.com/datasets/lennarthaupts/airbnb-berlin-july-2021)
  - Unzip and move `listings_berlin.csv` to `Downloads` folder.
- Install Seaborn.
  - Open command prompt as admin.
  - Run `pip install seaborn`

## Steps
- Import Pandas, Seaborn and Matplotlib inline.
- Matplotlib inline is used to display a plot directly below a cell in Jupyter Notebook.
```
import pandas as pd
import seaborn as sns
%matplotlib inline
```

- Show the first 10 rows of the dataframe.
```
df = pd.read_csv('~/Downloads/listings_berlin.csv')
df.head(10)
```

### Useful commands
- `df.tail(5)` shows the last 5 rows.
- `df.iloc[99]` shows the 100th row (dataframes are zero-indexed).
- `df.shape` shows the number of rows and columns.
- `df.columns` shows the columns.
- `df.describe()` shows a summary of the dataframe's count, mean etc.

### Visualisation - Pairplot
- Use Seaborn to display a pairplot.
- These are 2D plots. Each plot shows the relationship between two of the columns.
- What does this mean though? What am I looking for?
```
sns.pairplot(df,vars=['price','number_of_reviews','availability_365'])
```
![pairplot](/images/practical/pairplot.PNG)

### Visualisation - Heatmap
- Use Seaborn to display a heatmap.

```
df_corr = df.corr()
sns.heatmap(df_corr,annot=True,cmap='coolwarm')
```
