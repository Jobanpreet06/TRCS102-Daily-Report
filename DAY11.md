## DAY 11 OF TRAINING

**Pandas Data Cleaning, Missing Values & GroupBy**

Day 11 focused on **data cleaning, handling missing values, and grouping data using Pandas**. Real-world datasets often contain missing information. If this data is not handled properly, it can affect data analysis and machine learning results.

In this session, I learned how to detect missing values, fill them using the mean, remove rows with missing values, group records, and calculate aggregate statistics.

**Learning Objectives:-**

- Detect missing values using `isnull()`.
- Fill missing numerical values using `fillna()`.
- Remove rows with missing values using `dropna()`.
- Understand the `groupby()` function.
- Calculate aggregate statistics.
- Clean and analyse a student dataset.

## 1. What Are Missing Values?

Missing values are entries where information is not available in a dataset.

For example, a customer's age or income may be missing because the information was not provided.

Pandas provides functions to identify and handle these values.

**Detect Missing Values**

```python
print(df.isnull().sum())
```

**Explanation:**

- `isnull()` checks whether each value is missing.
- `sum()` counts the missing values in each column.

**Example Output:**

```text
CustomerID    0
Age           1
Gender        1
Income        1
Purchased     0
```

This means that the `Age`, `Gender`, and `Income` columns each contain one missing value.

## 2. Filling Missing Values

The `fillna()` function replaces missing values with a specified value.

**Fill Missing Age Values**

```python
mean_age = df["Age"].mean()

df["Age"] = df["Age"].fillna(mean_age)
```

This calculates the average age and uses it to replace missing values in the `Age` column.

**Fill Missing Income Values**

```python
mean_income = df["Income"].mean()

df["Income"] = df["Income"].fillna(mean_income)
```

This replaces missing income values with the average income.

**Important:** The mean is generally suitable for numerical data when it makes sense for the distribution. It can be affected by extreme values.

## 3. Removing Missing Values

Sometimes, rows with missing information should be removed instead of filling them.

**Example: Remove Rows with Missing Gender**

```python
df = df.dropna(subset=["Gender"])
```

This removes rows where the `Gender` value is missing.

The `subset` argument specifies which column should be checked for missing values.

**Verify the Dataset**

```python
print(df.isnull().sum())
```

**Example Output after handling the missing values:**

```text
CustomerID    0
Age           0
Gender        0
Income        0
Purchased     0
```

This output is expected only if all missing values in the relevant columns have been handled.

## 4. What Is GroupBy?

The `groupby()` function groups rows that have the same value in a particular column. We can then calculate statistics for each group.

For example, we can calculate the average income of male and female customers separately.

**Average Income by Gender**

```python
print(df.groupby("Gender")["Income"].mean())
```

**Average Age by Gender**

```python
print(df.groupby("Gender")["Age"].mean())
```

**Average Income and Age by Gender**

```python
cols = ["Income", "Age"]

print(df.groupby("Gender")[cols].mean())
```

**Output reported in the original notes:**

| Gender | Income | Age |
|---|---:|---:|
| F | 44666.67 | 26.27 |
| M | 69875.00 | 39.00 |

These values depend on the dataset and should be verified by running the code.

## 5. Grouping by Purchased Status

We can also compare customers according to whether they purchased a product.

```python
cols = ["Income", "Age"]

print(df.groupby("Purchased")[cols].mean())
```

**Output reported in the original notes:**

| Purchased | Income | Age |
|---|---:|---:|
| No | 42250 | 25.0 |
| Yes | 73500 | 40.9 |

This summary helps compare the average income and age of customers who purchased and did not purchase.

## 6. Aggregate Functions

Aggregate functions calculate summary values from data.

| Function | Purpose |
|---|---|
| `mean()` | Calculates the average |
| `sum()` | Calculates the total |
| `count()` | Counts non-missing values |
| `max()` | Finds the maximum value |
| `min()` | Finds the minimum value |
| `std()` | Calculates standard deviation |

**Example: Multiple Aggregate Functions**

```python
summary = df.groupby("Gender")["Income"].agg(
    ["mean", "min", "max", "count"]
)

print(summary)
```

This displays the average, minimum, maximum, and count of income values for each gender group.

**Practical Exercise: Student Dataset**

Load the student dataset:

```python
import pandas as pd

eval_df = pd.read_csv("student.csv")

print(eval_df.head())
print(eval_df.info())
print(eval_df.describe())
```

**Explanation:**

- `head()` displays the first five rows.
- `info()` displays column names, data types, and non-null counts.
- `describe()` provides summary statistics for numerical columns.

**Handling Missing Values in Student Data**

```python
mean_hours = eval_df["HoursStudied"].mean()

clean_df = eval_df.copy()

clean_df["HoursStudied"] = (
    clean_df["HoursStudied"].fillna(mean_hours)
)

clean_df = clean_df.dropna(subset=["Grade"])

print(clean_df)
```

The original DataFrame is preserved by using `copy()`. Missing study hours are replaced with the mean, and rows with missing grades are removed.

**GroupBy Summary for Students**

```python
summary = clean_df.groupby("Passed")[
    ["HoursStudied", "Grade", "Attendance"]
].mean()

print(summary)
```

**Output reported in the original notes:**

| Passed | HoursStudied | Grade | Attendance |
|---|---:|---:|---:|
| No | 6.75 | 53.50 | 88.00 |
| Yes | 15.10 | 86.00 | 94.33 |

These figures are dataset-dependent and should be confirmed by running the code on `student.csv`.

**Exercise 1: Count Missing Values in Each Column**

```python
print(eval_df.isnull().sum())
```

**Exercise 2: Fill Missing Study Hours with the Mean**

```python
clean_df = eval_df.copy()

mean_hours = clean_df["HoursStudied"].mean()

clean_df["HoursStudied"] = (
    clean_df["HoursStudied"].fillna(mean_hours)
)

print(clean_df)
```

**Exercise 3: Remove Rows with Missing Grades**

```python
clean_df = clean_df.dropna(subset=["Grade"])

print(clean_df)
```

**Exercise 4: Calculate Average Study Hours by Pass Status**

```python
summary = clean_df.groupby("Passed")["HoursStudied"].mean()

print(summary)
```

**Exercise 5: Calculate Average Grade and Attendance by Pass Status**

```python
summary = clean_df.groupby("Passed")[
    ["Grade", "Attendance"]
].mean()

print(summary)
```

**Exercise 6: Find Minimum and Maximum Grades by Pass Status**

```python
summary = clean_df.groupby("Passed")["Grade"].agg(
    ["min", "max"]
)

print(summary)
```

**Note:** Run the exercises in order where one exercise uses `clean_df` created in an earlier exercise. The `student.csv` file must be available in the working directory.

**AI/ML Applications**

Data cleaning and GroupBy operations are useful in:

- Handling missing data before model training.
- Customer data analysis.
- Student performance analysis.
- Exploratory Data Analysis (EDA).
- Feature preparation for machine learning.
- Summarising data to identify patterns.
