## DAY 27 OF TRAINING

**Customer Churn Prediction – Dataset Loading & Exploratory Data Analysis (EDA)**

**Introduction**

Today, I started working on an AI/ML project called **Customer Churn Prediction**. Customer churn means when a customer stops using a company's products or services.

Companies use customer data to understand why customers leave and to identify customers who may leave in the future.

In this project, we use Python, Pandas, NumPy, Matplotlib, and Seaborn to load, inspect, and visualize customer data.

**Learning Objectives:-**

- Understand customer churn and its importance.
- Load a customer dataset using Pandas.
- Inspect rows, columns, and dataset size.
- Understand numerical, categorical, and target features.
- Perform Exploratory Data Analysis (EDA).
- Visualize churn distribution and customer behaviour.

## 1. Understanding the Dataset

The project uses a dataset named `customer_churn_nlp.csv`.

The PDF reports that the dataset contains **500 rows and 7 columns**.

The dataset includes the following features:

| Feature | Meaning |
|---|---|
| Tenure | Number of months the customer has stayed with the company |
| MonthlyCharges | Amount charged to the customer each month |
| SupportTickets | Number of customer support complaints or requests |
| Contract | Type of customer contract |
| CustomerFeedback | Written feedback given by the customer |
| Churn | Target variable: 1 means the customer left; 0 means the customer stayed |

The complete column list should be checked using `df.columns`, because the PDF's description of the seven columns does not explicitly list every column name.

## 2. Importing Required Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_theme(style="whitegrid")
plt.rcParams["figure.figsize"] = (10, 5)
```

**Explanation:**

- Pandas is used to load and manage data.
- NumPy is used for numerical operations.
- Matplotlib creates charts.
- Seaborn creates statistical visualizations.

## 3. Loading and Inspecting the Dataset

```python
df = pd.read_csv("customer_churn_nlp.csv")

print("Dataset Shape:", df.shape)
print("\nFirst 5 Rows:")
print(df.head())

print("\nColumn Names:")
print(df.columns)

print("\nDataset Information:")
df.info()
```

**Explanation:**

- `pd.read_csv()` loads the CSV file.
- `df.shape` displays the number of rows and columns.
- `df.head()` displays the first five rows.
- `df.columns` displays all column names.
- `df.info()` shows column types and non-null values.

**Output reported in the PDF:**

```text
Dataset Shape: (500, 7)
```

The output means the dataset contains 500 customer records and 7 columns.

**Note:** The CSV file must be available in the working directory for this code to run.

## 4. What Is Exploratory Data Analysis (EDA)?

Exploratory Data Analysis means studying data before building a machine learning model.

It helps us understand the dataset, identify patterns, and discover relationships between customer information and churn.

In this project, we explore:

1. How many customers stayed or left.
2. Whether customer tenure is related to churn.
3. Whether monthly charges are related to churn.
4. How support tickets differ between retained and churned customers.
5. How churn varies across contract types.

## 5. Analysing Customer Churn Distribution

```python
churn_counts = df["Churn"].value_counts().sort_index()

print(churn_counts)

sns.countplot(data=df, x="Churn")
plt.title("Customer Retention vs Churn")
plt.xlabel("Churn (0 = Retained, 1 = Churned)")
plt.ylabel("Number of Customers")
plt.show()
```

**Explanation:**

A count plot displays the number of customers in each churn category.

- `0` represents retained customers.
- `1` represents customers who left the company.

This chart helps us understand the distribution of the target variable.

**Calculating the Churn Percentage**

```python
churn_percent = (df["Churn"].sum() / len(df)) * 100

print(f"Overall Churn Rate: {churn_percent:.2f}%")
```

**Output reported in the PDF:**

```text
Overall Churn Rate: 31.40%
```

This is the result reported by the PDF and has not been independently verified against the dataset.

## 6. Analysing Numerical Features

**A. Tenure vs Churn**

```python
sns.boxplot(data=df, x="Churn", y="Tenure")
plt.title("Tenure by Churn Status")
plt.xlabel("Churn (0 = Retained, 1 = Churned)")
plt.ylabel("Tenure in Months")
plt.show()
```

A box plot helps compare customer tenure between retained and churned customers.

The PDF identifies lower tenure as a feature associated with churn.

**B. Monthly Charges vs Churn**

```python
sns.boxplot(data=df, x="Churn", y="MonthlyCharges")
plt.title("Monthly Charges by Churn Status")
plt.xlabel("Churn (0 = Retained, 1 = Churned)")
plt.ylabel("Monthly Charges")
plt.show()
```

This chart compares monthly charges for customers who stayed and customers who left.

Higher charges may be associated with dissatisfaction, but the relationship must be checked using the actual data.

**C. Support Tickets vs Churn**

```python
sns.countplot(data=df, x="SupportTickets", hue="Churn")
plt.title("Support Tickets by Churn Status")
plt.xlabel("Number of Support Tickets")
plt.ylabel("Number of Customers")
plt.show()
```

This chart compares the number of support tickets across churn categories.

A higher number of complaints may indicate customer dissatisfaction.

## 7. Analysing Contract Type

```python
sns.countplot(data=df, x="Contract", hue="Churn")
plt.title("Churn Across Contract Types")
plt.xlabel("Contract Type")
plt.ylabel("Number of Customers")
plt.show()
```

The chart compares retained and churned customers across different contract types:

- Month-to-month
- One year
- Two year

This helps us investigate whether contract type is related to customer retention.

**Exercise 1: Display the First 10 Rows**

```python
print(df.head(10))
```

**Exercise 2: Find the Number of Rows and Columns**

```python
print(df.shape)
```

**Exercise 3: Count Retained and Churned Customers**

```python
print(df["Churn"].value_counts())
```

**Exercise 4: Calculate the Number of Churned Customers**

```python
churned = df[df["Churn"] == 1]
print("Churned Customers:", len(churned))
```

**Exercise 5: Display Customers with More Than 3 Support Tickets**

```python
result = df[df["SupportTickets"] > 3]
print(result)
```

**AI/ML Applications**

EDA is useful in:

1. Customer churn prediction.
2. Fraud detection.
3. Sales and business analysis.
4. Customer behaviour analysis.
5. Identifying patterns before training an ML model.
