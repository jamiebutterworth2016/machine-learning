# Helpful commands

## Reading a dataset
- Download the dataset from [kaggle.com](https://www.kaggle.com/anthonypino/melbourne-housing-market/) and extract the files.
- Add these three cells:
```
import pandas as pd

df = pd.read_csv('~/Downloads/Melbourne_housing_FULL.csv')

df.head(10)
```

- Run the cells with `Run > Run All Cells` to load the dataset and view the first 10 rows.

## Finding a specific row
- In ML, we often need to find a specific row.
- E.g. if the model finds that row 101 is the most suitable house to recommend to a buyer, we need to see that house.
- We're finding by index. The data is zero-indexed. Row 101 = index 100.
```
df.iloc[100]
```
Outputs
```
Suburb                         Airport West
Address                        180 Parer Rd
Rooms                                     3
Type                                      h
Price                              830000.0
...
Name: 100, dtype: object
```

## Printing columns
- Sometimes we need to configure which columns to select, modify or remove from the model.
- Print the column names with this command:
```
df.columns
```
Outputs
```
Index(['Suburb', 'Address', 'Rooms', 'Type', 'Price', 'Method', 'SellerG',
       'Date', 'Distance', 'Postcode', 'Bedroom2', 'Bathroom', 'Car',
       'Landsize', 'BuildingArea', 'YearBuilt', 'CouncilArea', 'Lattitude',
       'Longtitude', 'Regionname', 'Propertycount'],
      dtype='object')
```