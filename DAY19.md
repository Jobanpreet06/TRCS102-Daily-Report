## DAY 19 OF TRAINING

**Introduction to Clustering & K-Means**

**Project:** Customer Segmentation for Retail — Mall Customers Dataset

Day 19 introduced **Unsupervised Learning**, where a model discovers patterns and groups in data without predefined labels. We explored **K-Means Clustering** using the Mall Customers dataset to group customers according to annual income and spending score.

**Learning Objectives:-**

- Understand supervised and unsupervised learning.
- Learn the concept of clustering.
- Explore the Mall Customers dataset.
- Perform exploratory data analysis (EDA).
- Understand feature scaling.
- Implement K-Means clustering.
- Visualize customer clusters.

## 1. Supervised vs Unsupervised Learning

| Supervised Learning | Unsupervised Learning |
|---|---|
| Uses labelled data | Uses unlabelled data |
| Predicts known target values | Finds hidden patterns |
| Examples: Regression, Classification | Example: Clustering |

**Example:** Just as coins can be grouped by size, color, and weight without knowing their country, clustering groups similar data points together.

## 2. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

import warnings
warnings.filterwarnings("ignore")
```

## 3. Load the Mall Customers Dataset

The dataset contains 200 customer records and five columns:

- `CustomerID`
- `Gender`
- `Age`
- `Annual Income (k$)`
- `Spending Score (1-100)`

```python
df = pd.read_csv("Mall_Customers.csv")

print(df.shape)
print(df.head())
```

**Expected Output**

```text
(200, 5)
```

## 4. Exploratory Data Analysis (EDA)

EDA helps us understand the dataset before applying a Machine Learning algorithm.

```python
print("Dataset Shape:", df.shape)

df.info()

print(df.describe())

print(df.isnull().sum())
```

**Dataset Summary**

| Feature | Mean |
|---|---:|
| Age | 38.85 |
| Annual Income | 60.56 |
| Spending Score | 50.20 |

- Total customers: 200
- Total columns: 5
- Missing values: 0 in every column

## 5. Visualize the Raw Data

```python
plt.figure(figsize=(8, 5))

sns.scatterplot(
    data=df,
    x="Annual Income (k$)",
    y="Spending Score (1-100)"
)

plt.title("Annual Income vs Spending Score")
plt.show()
```

**Observation**

The scatter plot suggests several customer groups:

- Low income, low spending
- Low income, high spending
- Average income, average spending
- High income, low spending
- High income, high spending

These patterns suggest that five clusters may be useful.

## 6. Feature Scaling

K-Means uses Euclidean distance to group similar points. If features have different scales, a feature with a larger range can dominate the distance calculation.

**StandardScaler**

StandardScaler transforms features to have approximately a mean of 0 and a standard deviation of 1.

```python
X = df[
    ["Annual Income (k$)", "Spending Score (1-100)"]
]

scaler = StandardScaler()

X_scaled = scaler.fit_transform(X)

print(X_scaled[:5])
```

**Why Is Scaling Important?**

- Prevents one feature from dominating.
- Makes distance calculations fairer.
- Helps K-Means create meaningful clusters.

## 7. How K-Means Works

K-Means follows these steps:

1. **Choose K:** Select the number of clusters.
2. **Initialize Centroids:** Select starting cluster centers.
3. **Assign Points:** Assign each point to its nearest centroid.
4. **Update Centroids:** Calculate new cluster centers.
5. **Repeat:** Continue until the centroids stop changing significantly.

## 8. Train the K-Means Model

We use `K = 5` to create five customer groups.

```python
kmeans = KMeans(
    n_clusters=5,
    init="k-means++",
    n_init=10,
    random_state=42
)

kmeans.fit(X_scaled)

labels = kmeans.labels_

print("Model training completed!")
print("First 10 cluster labels:", labels[:10])
```

**Expected Output**

```text
Model training completed!
First 10 cluster labels: [4 2 4 2 4 2 4 2 4 2]
```

*Note: Cluster labels are identifiers; their numerical order has no special meaning.*

## 9. Visualize the Clusters

```python
df["Cluster"] = labels

centroids = scaler.inverse_transform(
    kmeans.cluster_centers_
)

plt.figure(figsize=(10, 6))

sns.scatterplot(
    data=df,
    x="Annual Income (k$)",
    y="Spending Score (1-100)",
    hue="Cluster",
    palette="Set1",
    s=70
)

plt.scatter(
    centroids[:, 0],
    centroids[:, 1],
    color="black",
    marker="*",
    s=300,
    label="Centroids"
)

plt.title("Mall Customer Segmentation (K=5)")
plt.legend()
plt.show()
```

**Cluster Centers**

| Cluster | Annual Income (k$) | Spending Score |
|---|---:|---:|
| 1 | 55.30 | 49.52 |
| 2 | 86.54 | 82.13 |
| 3 | 25.73 | 79.36 |
| 4 | 88.20 | 17.11 |
| 5 | 26.30 | 20.91 |
