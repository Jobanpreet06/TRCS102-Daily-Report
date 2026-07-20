## DAY 12 OF TRAINING

**Exploratory Data Analysis (EDA) on House Price Dataset**

Day 12 focused on **Exploratory Data Analysis (EDA)** using a real-world **King County House Price Dataset**. The session covered loading and cleaning data, understanding dataset statistics, performing univariate and bivariate analysis, visualizing data using Seaborn & Matplotlib, identifying outliers, analyzing feature relationships, and preparing the dataset for Machine Learning. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Exploratory Data Analysis (EDA)
- Load and inspect datasets
- Select important features
- Perform statistical analysis
- Create visualizations using Seaborn
- Detect outliers
- Study feature relationships
- Generate correlation heatmaps
- Prepare data for Machine Learning

## 1. Import Libraries

Import the required Python libraries.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## 2. Load Dataset

Load the King County House Price dataset.

```python
df = pd.read_csv("kc_house_data.csv")

print(df.head())
```

Display dataset size.

```python
print(df.shape)
```

**Output**

```
21613 Rows
21 Columns
```

The dataset contains **21,613 houses** with **21 features**. :contentReference[oaicite:1]{index=1}

## 3. Select Important Features

Choose only useful columns for analysis.

```python
friendly_cols = [

"price",

"bedrooms",

"bathrooms",

"sqft_living",

"floors",

"waterfront",

"yr_built",

"condition"

]

df = df[friendly_cols]

df.head()
```

Selected Features

| Feature | Description |
|----------|-------------|
| price | House Price |
| bedrooms | Number of Bedrooms |
| bathrooms | Number of Bathrooms |
| sqft_living | Living Area |
| floors | Number of Floors |
| waterfront | Waterfront View |
| yr_built | Year Built |
| condition | House Condition |

This simplifies the dataset by keeping only the most understandable and relevant features. :contentReference[oaicite:2]{index=2}

## 4. Dataset Statistics

Display summary statistics.

```python
df.describe()
```

Displays

- Count
- Mean
- Standard Deviation
- Minimum
- Maximum
- Quartiles

**Dataset Information**

```python
df.info()
```

Shows

- Data types
- Memory usage
- Non-null values

The selected dataset has **8 columns**, all without missing values. :contentReference[oaicite:3]{index=3}

## 5. Univariate Analysis – Price Distribution

Visualize house prices using Histogram.

```python
plt.figure(figsize=(10,5))

sns.histplot(
    data=df,
    x="price",
    bins=50,
    kde=True,
    color="red"
)

plt.title("House Price Distribution")

plt.xlabel("Price")

plt.ylabel("Number of Houses")

plt.show()
```

**Observation**

- Most houses have moderate prices.
- Very expensive houses appear as outliers.

:contentReference[oaicite:4]{index=4}

## 6. Bedroom Count Analysis

Display the frequency of bedroom counts.

```python
plt.figure(figsize=(10,5))

sns.countplot(
    data=df,
    x="bedrooms",
    hue="bedrooms",
    palette="Set2",
    legend=False
)

plt.title("Bedroom Counts")

plt.show()
```

**Detect Outliers**

```python
giant_outlier = df[df["bedrooms"] > 10]

print(giant_outlier)
```

**Observation**

- Most houses contain **3–4 bedrooms**.
- Two extreme houses have more than **10 bedrooms**, including one with **33 bedrooms**.

:contentReference[oaicite:5]{index=5}

## 7. Bivariate Analysis – Size vs Price

Study the relationship between living area and price.

```python
plt.figure(figsize=(10,6))

sns.scatterplot(
    data=df,
    x="sqft_living",
    y="price",
    hue="waterfront"
)

plt.title("House Size vs Price")

plt.show()
```

**Observation**

- Larger houses generally cost more.
- Waterfront houses tend to have higher prices.

:contentReference[oaicite:6]{index=6}

## 8. Waterfront vs Price

Compare prices of waterfront and non-waterfront houses.

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    x="waterfront",
    y="price",
    data=df,
    hue="waterfront",
    palette="pastel"
)

plt.title("Waterfront vs House Price")

plt.show()
```

**Observation**

- Waterfront houses are significantly more expensive.

:contentReference[oaicite:7]{index=7}

## 9. House Condition vs Price

Analyze the effect of house condition on price.

```python
plt.figure(figsize=(8,5))

sns.barplot(
    x="condition",
    y="price",
    data=df,
    hue="condition",
    palette="coolwarm"
)

plt.title("House Condition vs Price")

plt.show()
```

**Observation**

Better-maintained houses usually have higher average prices.

:contentReference[oaicite:8]{index=8}

## 10. Correlation Heatmap

Display correlation between numerical features.

```python
plt.figure(figsize=(10,8))

correlation = df.corr()

sns.heatmap(
    correlation,
    annot=True,
    cmap="coolwarm",
    linewidths=0.5,
    vmin=-1,
    vmax=1
)

plt.title("Correlation Heatmap")

plt.show()
```

**Observation**

- Living area has the strongest positive correlation with price.
- Waterfront also positively affects price.

:contentReference[oaicite:9]{index=9}

## 11. Save Processed Dataset

```python
df.to_csv(
    "kc_house_filtered.csv",
    index=False
)
```

The filtered dataset is saved for further Machine Learning tasks. :contentReference[oaicite:10]{index=10}

**Summary of Findings**

- House size has the strongest impact on price.
- Waterfront houses are generally more expensive.
- Outliers such as houses with unusually high bedroom counts were identified.
- Correlation analysis helps understand relationships between variables.
- The cleaned dataset is ready for further Machine Learning analysis.

**AI/ML Applications**

- Exploratory Data Analysis (EDA)
- Feature Selection
- Outlier Detection
- Data Cleaning
- Correlation Analysis
- Data Visualization
- Dataset Preparation for Machine Learning
