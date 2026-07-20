## DAY 13 OF TRAINING

**Data Preprocessing for Machine Learning**

Day 13 focused on **Data Preprocessing**, an essential step before training Machine Learning models. The session covered handling missing values, treating outliers, feature scaling, one-hot encoding, and preparing the final cleaned dataset for ML algorithms using Scikit-learn and Pandas. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Data Preprocessing
- Load and inspect datasets
- Handle Missing Values (Imputation)
- Detect & Treat Outliers
- Perform Feature Scaling
- Apply One-Hot Encoding
- Prepare final ML-ready dataset
- Save preprocessed data

## 1. Import Libraries & Load Dataset

Import required libraries and load the filtered house dataset.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.preprocessing import StandardScaler, MinMaxScaler

df = pd.read_csv("kc_house_filtered.csv")

df.head()
```

Check missing values.

```python
df.isnull().sum()
```

**Output**

```
price            0
bedrooms         0
bathrooms        0
sqft_living      0
floors           0
waterfront       0
yr_built         0
condition        0
```

The dataset is loaded successfully and contains no missing values initially. :contentReference[oaicite:1]{index=1}

## 2. Missing Value Imputation

To understand missing-value handling, random values are removed from the **Year Built** column and replaced using the **Median**.

**Why Median?**

- Less affected by extreme values
- Suitable for skewed numerical data
- Produces better estimates than mean in many cases

Median is preferred because it is robust against outliers. :contentReference[oaicite:2]{index=2}

**Exercise 1 – Missing Value Handling**

**Task**

- Identify missing values
- Replace missing values using Median

**Solution**

```python
median_year = df["yr_built"].median()

df["yr_built"] = df["yr_built"].fillna(median_year)
```

## 3. Outlier Capping using IQR

Extreme values can negatively affect Machine Learning models.

Instead of deleting them, **IQR (Interquartile Range) Capping** is used.

**Formula**

```
IQR = Q3 - Q1

Lower Limit = Q1 − 1.5 × IQR

Upper Limit = Q3 + 1.5 × IQR
```

**Function**

```python
def find_caps(column):

    Q1 = column.quantile(0.25)

    Q3 = column.quantile(0.75)

    IQR = Q3 - Q1

    lower = Q1 - 1.5 * IQR

    upper = Q3 + 1.5 * IQR

    return lower, upper
```

Apply capping.

```python
columns = ["price","sqft_living","bedrooms"]

for col in columns:

    lower, upper = find_caps(df[col])

    df[col] = df[col].clip(lower, upper)
```

**Output**

```
Price Outliers Capped

Sqft Living Outliers Capped

Bedroom Outliers Capped
```

IQR capping limits extreme values while preserving the dataset. :contentReference[oaicite:3]{index=3}

**Exercise 2 – Outlier Detection**

**Task**

- Detect outliers
- Cap them using IQR

**Solution**

```python
sns.boxplot(data=df,
            y="sqft_living")

plt.show()
```

## 4. Feature Scaling

Machine Learning algorithms perform better when numerical features are on similar scales.

Two scaling techniques are used.

| Scaler | Purpose |
|---------|----------|
| MinMaxScaler | Converts values between 0 and 1 |
| StandardScaler | Mean = 0, Standard Deviation = 1 |

:contentReference[oaicite:4]{index=4}

**Min-Max Scaling**

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()

df["Scaled_size"] = scaler.fit_transform(
    df[["sqft_living"]]
)
```

**Standard Scaling**

```python
from sklearn.preprocessing import StandardScaler

std = StandardScaler()

df["Year_Scaled"] = std.fit_transform(
    df[["yr_built"]]
)
```

**Output**

New columns created

```
Scaled_size

Year_Scaled
```

**Exercise 3 – Scaling Features**

**Task**

Normalize house size and standardize construction year.

**Solution**

```python
minmax = MinMaxScaler()

df["Scaled_size"] = minmax.fit_transform(
    df[["sqft_living"]]
)

standard = StandardScaler()

df["Year_Scaled"] = standard.fit_transform(
    df[["yr_built"]]
)
```

## 5. One-Hot Encoding

Machine Learning models cannot understand text values directly.

One-Hot Encoding converts categorical values into binary columns.

Example

| Neighborhood | Budget | Mid-Range | Premium |
|--------------|:------:|:---------:|:-------:|
| Budget | 1 | 0 | 0 |
| Premium | 0 | 0 | 1 |
| Mid-Range | 0 | 1 | 0 |

A random **Neighborhood** category is created and encoded using `pd.get_dummies()`. :contentReference[oaicite:5]{index=5}

**Code**

```python
neighborhoods = [

"Budget",

"Mid-Range",

"Premium"

]

df["Neighborhood"] = np.random.choice(
    neighborhoods,
    size=len(df)
)

df_encoded = pd.get_dummies(
    df,
    columns=["Neighborhood"],
    prefix="Loc",
    dtype=int
)
```

**New Columns**

```
Loc_Budget

Loc_Mid-Range

Loc_Premium
```

**Exercise 4 – One-Hot Encoding**

**Task**

Convert Neighborhood into numerical columns.

**Solution**

```python
df_encoded = pd.get_dummies(

    df,

    columns=["Neighborhood"],

    prefix="Loc"

)
```

## 6. Final Dataset Preparation

Select only important ML features.

```python
final_cols = [

"price",

"bedrooms",

"bathrooms",

"Scaled_size",

"floors",

"waterfront",

"sqft_living",

"condition",

"Loc_Budget",

"Loc_Mid-Range",

"Loc_Premium"

]

df_final = df_encoded[final_cols]
```

Save dataset.

```python
df_final.to_csv(

"kc_house_preprocessed.csv",

index=False

)
```

**Output**

```
Preprocessed data saved successfully as

kc_house_preprocessed.csv
```

The final dataset contains cleaned, scaled, and encoded features ready for Machine Learning. :contentReference[oaicite:6]{index=6}

**Summary**

The preprocessing pipeline includes:

- Loading dataset
- Handling missing values
- Outlier treatment
- Feature scaling
- One-Hot Encoding
- Saving final ML-ready dataset

**AI/ML Applications**

- Data Cleaning
- Missing Value Treatment
- Outlier Handling
- Feature Engineering
- Data Transformation
- Machine Learning Preprocessing
- Model Optimization



