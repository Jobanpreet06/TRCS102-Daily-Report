## DAY 9 OF TRAINING

**Pandas Data Cleaning, Boolean Indexing & GroupBy**

Day 9 focused on **data preprocessing using Pandas**, including filtering datasets with Boolean Indexing, handling missing values, grouping data for analysis, and solving practical data-cleaning exercises commonly used in AI & Machine Learning.

**Learning Objectives:-**

- Understand Boolean Indexing
- Filter data using single and multiple conditions
- Detect Missing Values
- Handle missing data using `fillna()`
- Remove missing values using `dropna()`
- Perform GroupBy operations
- Calculate Aggregate Statistics
- Solve Data Cleaning Exercises

## 1. Boolean Indexing

Boolean Indexing is used to filter rows that satisfy a given condition.

**Example**

```python
high_income = df[df["Income"] > 60000]

print(high_income)
```

Returns all customers having income greater than **60000**.

**Multiple Conditions**

```python
filtered = df[(df["Age"] >= 25) & (df["Gender"] == "F")]

print(filtered)
```

**Using Boolean Mask**

```python
mask = df["Income"] > 60000

print(mask)

high_income = df[mask]

print(high_income)
```

## 2. Missing Values

Real-world datasets usually contain missing values that must be handled before training Machine Learning models.

**Detect Missing Values**

```python
df.isnull().sum()
```

**Example Output**

```text
CustomerID    0
Age           1
Gender        1
Income        1
Purchased     0
```

**Fill Missing Values**

Replace missing **Age** values with the column mean.

```python
mean_age = df["Age"].mean()

df["Age"] = df["Age"].fillna(mean_age)
```

Replace missing **Income** values.

```python
mean_income = df["Income"].mean()

df["Income"] = df["Income"].fillna(mean_income)
```

**Drop Missing Values**

Remove rows containing missing Gender values.

```python
df = df.dropna(subset=["Gender"])
```

**Verify Dataset**

```python
df.isnull().sum()
```

**Output**

```text
CustomerID    0
Age           0
Gender        0
Income        0
Purchased     0
```

## 3. GroupBy

`groupby()` groups similar records together for analysis.

**Average Income by Gender**

```python
df.groupby("Gender")["Income"].mean()
```

**Average Age by Gender**

```python
df.groupby("Gender")["Age"].mean()
```

**Multiple Columns**

```python
cols = ["Income","Age"]

df.groupby("Gender")[cols].mean()
```

**Output**

| Gender | Income | Age |
|---------|--------:|----:|
| F | 44666.67 | 26.27 |
| M | 69875.00 | 39.00 |

**Group by Purchased**

```python
df.groupby("Purchased")[cols].mean()
```

**Output**

| Purchased | Income | Age |
|------------|--------:|----:|
| No | 42250 | 25.0 |
| Yes | 73500 | 40.9 |

## 4. Aggregate Functions

Common aggregation functions used with GroupBy.

| Function | Purpose |
|----------|---------|
| `mean()` | Average value |
| `sum()` | Total |
| `count()` | Number of records |
| `max()` | Maximum value |
| `min()` | Minimum value |
| `std()` | Standard Deviation |

**Exercise 1 – Dataset Inspection**

```python
eval_df = pd.read_csv("student.csv")

print(eval_df.head())

print(eval_df.info())

print(eval_df.describe())
```

**Exercise 2 – Data Filtering**

Display students who passed.

```python
passed = eval_df[eval_df["Passed"]=="Yes"]

print(passed)
```

Display only selected columns.

```python
passed = eval_df[eval_df["Passed"]=="Yes"][["HoursStudied","Grade"]]

print(passed)
```

**Exercise 3 – Missing Value Handling**

```python
mean_hours = eval_df["HoursStudied"].mean()

clean_df = eval_df.copy()

clean_df["HoursStudied"] = clean_df["HoursStudied"].fillna(mean_hours)

clean_df = clean_df.dropna(subset=["Grade"])

print(clean_df)
```

**Exercise 4 – GroupBy Summary**

```python
summary = clean_df.groupby("Passed")[["HoursStudied","Grade","Attendance"]].mean()

print(summary)
```

**Output**

| Passed | HoursStudied | Grade | Attendance |
|---------|-------------:|------:|-----------:|
| No | 6.75 | 53.50 | 88.00 |
| Yes | 15.10 | 86.00 | 94.33 |

**AI/ML Applications**

- Data Cleaning
- Feature Selection
- Missing Value Treatment
- Customer Data Analysis
- Exploratory Data Analysis (EDA)
- Dataset Preprocessing
- Model Preparation

