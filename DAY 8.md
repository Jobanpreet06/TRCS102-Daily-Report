## DAY 8 OF TRAINING

**Pandas Basics – Series, DataFrames & Data Exploration**

Day 8 focused on the fundamentals of **Pandas**, a powerful Python library used for data manipulation and analysis. The session covered creating Series and DataFrames, loading datasets, exploring data, selecting rows and columns, and understanding dataset structure through various built-in functions.

**Learning Objectives:-**

- Understand Pandas and its importance
- Create Series and DataFrames
- Load datasets using `read_csv()`
- Explore datasets using built-in functions
- Select rows and columns
- Use `loc[]` and `iloc[]`
- Perform basic data analysis
- Solve practical exercises

## 1. Introduction to Pandas

**Pandas** is an open-source Python library used for data manipulation, analysis, and preprocessing. It provides fast, flexible, and easy-to-use data structures.

**Why Pandas?**

- Easy data handling
- Fast processing
- Supports CSV, Excel & SQL
- Handles missing values
- Used extensively in AI & Machine Learning

```python
import pandas as pd
```

## 2. Pandas Data Structures

Pandas mainly provides two data structures.

| Data Structure | Description |
|---------------|-------------|
| **Series** | One-dimensional labeled array |
| **DataFrame** | Two-dimensional table with rows and columns |

## 3. Pandas Series

A **Series** is a one-dimensional array capable of holding any data type.

**Example**

```python
import pandas as pd

marks = pd.Series([90,85,78,95])

print(marks)
```

**Output**

```text
0    90
1    85
2    78
3    95
dtype: int64
```

## 4. Pandas DataFrame

A **DataFrame** is a two-dimensional tabular data structure consisting of rows and columns.

**Example**

```python
student = {

    "Name":["Alice","Bob","John"],

    "Age":[20,21,19],

    "Marks":[90,80,95]

}

df = pd.DataFrame(student)

print(df)
```

## 5. Reading CSV Files

Datasets are commonly loaded using `read_csv()`.

```python
df = pd.read_csv("data.csv")

print(df.head())
```

## 6. Exploring the Dataset

**Display First Rows**

```python
df.head()
```

Displays the first **5 rows**.

**Display Last Rows**

```python
df.tail()
```

Displays the last **5 rows**.

**Dataset Information**

```python
df.info()
```

Shows:

- Number of rows
- Number of columns
- Data types
- Missing values
- Memory usage

**Statistical Summary**

```python
df.describe()
```

Displays:

- Count
- Mean
- Standard Deviation
- Minimum
- Maximum
- Quartiles

**Display Column Names**

```python
print(df.columns)
```

**Display Data Types**

```python
print(df.dtypes)
```

Example Output

```text
CustomerID      int64
Age           float64
Gender         object
Income        float64
Purchased      object
```

## 7. Selecting Data

**Selecting a Single Column**

```python
income = df["Income"]

print(income)
```

Returns a **Series**.

**Selecting Multiple Columns**

```python
features = df[["Age","Income"]]

print(features)
```

Returns a **DataFrame**.

## 8. Row Selection using `iloc[]`

`iloc[]` selects data using **index positions**.

**Example**

```python
df.iloc[1:4,1:4]
```

## 9. Row Selection using `loc[]`

`loc[]` selects data using **row labels and column names**.

**Example**

```python
df.loc[1,"Age"]
```

**Output**

```text
47
```

**Exercise 1 – Create a DataFrame**

```python
student = {

    "Name":["Rahul","Priya","Aman"],

    "Age":[20,21,19],

    "Marks":[88,92,85]

}

df = pd.DataFrame(student)

print(df)
```

**Exercise 2 – Dataset Exploration**

```python
df = pd.read_csv("students.csv")

print(df.head())

print(df.info())

print(df.describe())
```

**Exercise 3 – Column Selection**

```python
print(df["Marks"])

print(df[["Name","Marks"]])
```

**Exercise 4 – Row Selection**

```python
print(df.iloc[0:3])

print(df.loc[2])
```

