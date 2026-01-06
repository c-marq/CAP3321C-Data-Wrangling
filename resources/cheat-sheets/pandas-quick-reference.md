# Pandas Quick Reference

A quick reference guide for common Pandas operations.

---

## Importing Pandas

```python
import pandas as pd
```

---

## Creating DataFrames

```python
# From a dictionary
data = {'col1': [1, 2, 3], 'col2': ['a', 'b', 'c']}
df = pd.DataFrame(data)

# From a CSV file
df = pd.read_csv('filename.csv')

# From a URL
df = pd.read_csv('https://example.com/data.csv')
```

---

## Viewing Data

```python
df.head()           # First 5 rows
df.head(10)         # First 10 rows
df.tail()           # Last 5 rows
df.sample(5)        # Random 5 rows
df.shape            # (rows, columns)
df.columns          # Column names
df.dtypes           # Data types
df.info()           # Summary info
df.describe()       # Statistical summary
```

---

## Selecting Data

```python
# Single column (returns Series)
df['column_name']

# Multiple columns (returns DataFrame)
df[['col1', 'col2']]

# Rows by index position
df.iloc[0]          # First row
df.iloc[0:5]        # First 5 rows
df.iloc[0, 2]       # Row 0, Column 2

# Rows by label
df.loc[0]           # Row with index 0
df.loc[0:5]         # Rows with index 0 through 5
df.loc[0, 'col1']   # Row 0, column 'col1'
```

---

## Filtering Data

```python
# Single condition
df[df['age'] > 30]

# Multiple conditions (AND)
df[(df['age'] > 30) & (df['city'] == 'Miami')]

# Multiple conditions (OR)
df[(df['age'] > 30) | (df['city'] == 'Miami')]

# Using query method
df.query('age > 30')
df.query('age > 30 and city == "Miami"')
```

---

## Sorting Data

```python
# Sort by one column
df.sort_values('column_name')

# Sort descending
df.sort_values('column_name', ascending=False)

# Sort by multiple columns
df.sort_values(['col1', 'col2'])
```

---

## Adding/Modifying Columns

```python
# Add new column
df['new_col'] = df['col1'] + df['col2']

# Rename columns
df.rename(columns={'old_name': 'new_name'}, inplace=True)

# Drop columns
df.drop(columns=['col1', 'col2'], inplace=True)
```

---

## Handling Missing Values

```python
# Check for missing values
df.isnull().sum()

# Drop rows with missing values
df.dropna()

# Fill missing values
df.fillna(0)
df.fillna(df['column'].mean())
```

---

## Grouping and Aggregating

```python
# Group by one column
df.groupby('category').sum()

# Group by multiple columns
df.groupby(['cat1', 'cat2']).mean()

# Multiple aggregations
df.groupby('category').agg({'col1': 'sum', 'col2': 'mean'})
```

---

## Common Aggregation Functions

| Function | Description |
|----------|-------------|
| `sum()` | Sum of values |
| `mean()` | Average |
| `median()` | Median value |
| `min()` | Minimum |
| `max()` | Maximum |
| `count()` | Count non-null values |
| `nunique()` | Count unique values |
| `std()` | Standard deviation |

---

## Saving Data

```python
# To CSV
df.to_csv('output.csv', index=False)

# To Excel
df.to_excel('output.xlsx', index=False)
```

---

## Useful Tips

```python
# Reset index
df.reset_index(drop=True, inplace=True)

# Set a column as index
df.set_index('column_name', inplace=True)

# Get unique values
df['column'].unique()

# Value counts
df['column'].value_counts()

# Apply function to column
df['col'].apply(lambda x: x * 2)
```

---

[← Back to Resources](../README.md)
