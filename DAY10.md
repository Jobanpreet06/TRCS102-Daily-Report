## DAY 10 OF TRAINING

**Pandas Boolean Indexing & Data Filtering**

**Introduction**

Day 10 focused on **Boolean Indexing and Data Filtering using Pandas**. Boolean Indexing helps us select rows from a dataset based on specific conditions. It is useful when we want to analyse only selected records instead of the complete dataset.

In this session, I learned how to filter data using single and multiple conditions, create Boolean masks, and select specific columns from a DataFrame.

**Learning Objectives:-**

- Understand Boolean Indexing in Pandas.
- Filter rows using a single condition.
- Apply multiple conditions using `&` and `|`.
- Create and use Boolean masks.
- Select specific columns from filtered data.
- Solve practical data-filtering exercises.

## 1. What Is Boolean Indexing?

Boolean Indexing is a technique used to select rows that satisfy a particular condition.

For example, if we want to display customers whose income is greater than 60000, we can use Boolean Indexing.

**Example: Filter Customers by Income**

```python
high_income = df[df["Income"] > 60000]

print(high_income)
```

**Explanation:**

- `df["Income"] > 60000` checks the income of each customer.
- It returns `True` for customers whose income is greater than 60000 and `False` for others.
- `df[...]` selects only the rows where the condition is `True`.

## 2. Filtering Using Multiple Conditions

We can combine multiple conditions to filter data more precisely.

**Example: Age and Gender**

```python
filtered = df[
    (df["Age"] >= 25) & (df["Gender"] == "F")
]

print(filtered)
```

This displays customers who are at least 25 years old and have gender `"F"`.

**Important operators:**

| Operator | Meaning |
|---|---|
| `&` | AND — both conditions must be true |
| `|` | OR — at least one condition must be true |
| `~` | NOT — reverses a Boolean condition |

Always place each condition inside parentheses when combining conditions in Pandas.

**Example: Using OR**

```python
filtered = df[
    (df["Age"] < 20) | (df["Income"] > 60000)
]

print(filtered)
```

This selects customers who are younger than 20 **or** have income greater than 60000.

## 3. Using a Boolean Mask

A Boolean mask stores the result of a condition as `True` or `False` values.

```python
mask = df["Income"] > 60000

print(mask)

high_income = df[mask]

print(high_income)
```

**Explanation:**

1. The condition checks each customer's income.
2. The variable `mask` stores the Boolean results.
3. `df[mask]` selects the rows where the mask is `True`.

Using a separate mask makes filtering easier to understand and reuse.

## 4. Selecting Specific Columns

Sometimes, we need only a few columns from the filtered data.

For example, to display only the hours studied and grade of students who passed:

```python
passed = eval_df[
    eval_df["Passed"] == "Yes"
][["HoursStudied", "Grade"]]

print(passed)
```

This first filters students who passed and then displays only the `HoursStudied` and `Grade` columns.

**Exercise 1: Display Customers with Income Greater Than 50000**

```python
result = df[df["Income"] > 50000]

print(result)
```

**Exercise 2: Display Customers Aged 25 or Above**

```python
result = df[df["Age"] >= 25]

print(result)
```

**Exercise 3: Display Female Customers with Income Above 40000**

```python
result = df[
    (df["Gender"] == "F") & (df["Income"] > 40000)
]

print(result)
```

**Exercise 4: Display Customers Who Are Younger Than 20 or Have Income Above 60000**

```python
result = df[
    (df["Age"] < 20) | (df["Income"] > 60000)
]

print(result)
```

**Exercise 5: Display Students Who Passed with Selected Columns**

```python
passed = eval_df[eval_df["Passed"] == "Yes"]

print(passed[["HoursStudied", "Grade"]])
```

**Note:** These exercises use the DataFrames `df` and `eval_df` introduced in the examples. Load the appropriate dataset before running them.

**AI/ML Applications**

Boolean Indexing and Data Filtering are useful in:

- Selecting relevant customer records.
- Filtering data during preprocessing.
- Analysing customer behaviour.
- Selecting records for Exploratory Data Analysis (EDA).
- Preparing datasets before training machine learning models.
