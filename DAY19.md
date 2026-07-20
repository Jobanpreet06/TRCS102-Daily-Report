## DAY 19 OF TRAINING

**Introduction to Clustering (Unsupervised Learning)**

Day 19 introduced **Unsupervised Learning**, where the model discovers hidden patterns without using target labels. We studied the **K-Means Clustering** algorithm using the **Mall Customers Dataset** to group customers based on their purchasing behavior. We also learned Feature Scaling, Cluster Visualization, Customer Segmentation, and the Elbow Method for selecting the optimal number of clusters. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Unsupervised Learning
- Learn Clustering
- Understand K-Means Algorithm
- Explore Mall Customers Dataset
- Perform Feature Scaling
- Build K-Means Model
- Visualize Clusters
- Interpret Customer Segments
- Learn the Elbow Method

## 1. Supervised vs Unsupervised Learning

| Supervised Learning | Unsupervised Learning |
|---------------------|----------------------|
| Uses target labels | No target labels |
| Predicts outputs | Finds hidden patterns |
| Examples: Regression, Classification | Example: Clustering |

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

## 3. Load Mall Customers Dataset

The dataset contains **200 customers** with the following attributes:

- CustomerID
- Gender
- Age
- Annual Income (k$)
- Spending Score (1–100)

```python
df = pd.read_csv("Mall_Customers.csv")

df.head()
```

**Output**

```
Dataset Shape

200 Rows × 5 Columns
```

## 4. Exploratory Data Analysis (EDA)

```python
print(df.shape)

df.info()

df.describe()
```

**Dataset Summary**

| Attribute | Value |
|-----------|-------|
| Rows | 200 |
| Columns | 5 |
| Missing Values | 0 |

**Summary Statistics**

| Feature | Mean |
|---------|------|
| Age | 38.85 |
| Annual Income | 60.56 |
| Spending Score | 50.20 |

Since there are **no missing values**, the dataset is ready for clustering. :contentReference[oaicite:2]{index=2}

## 5. Raw Data Visualization

```python
sns.scatterplot(
    data=df,
    x="Annual Income (k$)",
    y="Spending Score (1-100)"
)
```

**Observation**

The scatter plot naturally shows groups of customers:

- Low Income – Low Spending
- Low Income – High Spending
- Average Income – Average Spending
- High Income – Low Spending
- High Income – High Spending

This indicates that **5 clusters** may be suitable. :contentReference[oaicite:3]{index=3}

## 6. Feature Scaling

K-Means uses **Euclidean Distance**, so features must be on the same scale.

```python
X = df[
[
"Annual Income (k$)",
"Spending Score (1-100)"
]
]

scaler = StandardScaler()

X_scaled = scaler.fit_transform(X)
```

**Why Scaling?**

- Prevents one feature from dominating.
- Improves clustering accuracy.
- Gives equal importance to all features. :contentReference[oaicite:4]{index=4}

## 7. K-Means Clustering

**Steps**

1. Choose K
2. Initialize Centroids
3. Assign Data Points
4. Update Centroids
5. Repeat until convergence

```python
kmeans = KMeans(
    n_clusters=5,
    init="k-means++",
    n_init=10,
    random_state=42
)

kmeans.fit(X_scaled)

labels = kmeans.labels_
```

**Output**

```
Model Training Completed Successfully
```

## 8. Visualizing Clusters

```python
df["Cluster"] = labels

sns.scatterplot(
data=df,
x="Annual Income (k$)",
y="Spending Score (1-100)",
hue="Cluster"
)
```

**Cluster Centers**

| Cluster | Income | Spending Score |
|----------|---------|----------------|
| 1 | 55.30 | 49.52 |
| 2 | 86.54 | 82.13 |
| 3 | 25.73 | 79.36 |
| 4 | 88.20 | 17.11 |
| 5 | 26.30 | 20.91 |

## 9. Customer Segment Interpretation

| Cluster | Description |
|----------|-------------|
| High Income – High Spending | Premium Customers |
| High Income – Low Spending | Conservative Customers |
| Average Income – Average Spending | Regular Customers |
| Low Income – High Spending | Impulsive Buyers |
| Low Income – Low Spending | Budget Customers |

These customer groups help businesses design targeted marketing strategies. :contentReference[oaicite:5]{index=5}

## 10. Elbow Method

The Elbow Method helps determine the **optimal number of clusters (K)** by comparing inertia values.

```python
inertias=[]

for k in range(1,11):

    km=KMeans(
        n_clusters=k,
        random_state=42
    )

    km.fit(X_scaled)

    inertias.append(km.inertia_)
```

**Observation**

The elbow appears at **K = 5**, indicating that **5 clusters** are the optimal choice. :contentReference[oaicite:6]{index=6}

**Exercise 1 – Change Number of Clusters**

**Task**

Run K-Means for **K = 3, 4, 5, 6**.

**Solution**

```python
for k in [3,4,5,6]:

    model = KMeans(
        n_clusters=k,
        random_state=42
    )

    model.fit(X_scaled)

    print(
        "K =",k,
        "Inertia =",model.inertia_
    )
```

**Exercise 2 – Use Different Features**

**Task**

Cluster customers using **Age** and **Annual Income**.

**Solution**

```python
X2=df[
[
"Age",
"Annual Income (k$)"
]
]

X2=scaler.fit_transform(X2)

model=KMeans(
n_clusters=5,
random_state=42
)

model.fit(X2)
```

**Exercise 3 – Visualize New Clusters**

**Solution**

```python
plt.figure(figsize=(8,6))

sns.scatterplot(
x=df["Age"],
y=df["Annual Income (k$)"],
hue=model.labels_,
palette="Set1"
)

plt.show()
```

**Exercise 4 – Compare Different Values of K**

**Solution**

```python
scores=[]

for k in range(2,8):

    km=KMeans(
        n_clusters=k,
        random_state=42
    )

    km.fit(X_scaled)

    scores.append(km.inertia_)

print(scores)
```

**AI/ML Applications**

- Customer Segmentation
- Product Recommendation
- Market Basket Analysis
- Fraud Detection
- Image Segmentation
- Medical Data Analysis
- Social Network Analysis


