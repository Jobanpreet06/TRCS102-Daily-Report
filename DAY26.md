## DAY 26 OF TRAINING

**Customer Segmentation & Elbow Method**

**Project:** Retail Customer Analysis using K-Means Clustering

Day 20 focuses on interpreting K-Means clusters and using customer groups for retail marketing. We also study the **Elbow Method**, which helps choose the number of clusters by comparing the inertia for different values of K.

**Learning Objectives:-**

- Interpret customer segments.
- Understand cluster centers.
- Learn inertia and WCSS.
- Apply the Elbow Method.
- Compare different values of K.
- Use clustering results for marketing decisions.

## 1. Understanding Customer Segments

After clustering the Mall Customers dataset, five customer segments can be identified using annual income and spending score.

| Segment | Customer Type | Marketing Strategy |
|---|---|---|
| High Income, High Spending | Premium Shoppers | Offer VIP rewards and premium products. |
| High Income, Low Spending | Conservative Spenders | Provide targeted offers and value deals. |
| Average Income, Average Spending | Moderate Spenders | Use regular loyalty programs. |
| Low Income, High Spending | High-Spending Budget Customers | Offer promotions and discounts. |
| Low Income, Low Spending | Budget Shoppers | Promote affordable products. |

**Observation**

Customer segmentation helps businesses understand purchasing behavior and design marketing strategies for different customer groups.

## 2. What Is the Elbow Method?

The **Elbow Method** helps find a suitable number of clusters, represented by K.

It uses **Inertia**, also called Within-Cluster Sum of Squares (WCSS), to measure how close data points are to their assigned cluster centers.

**Formula**

$$
WCSS = \\sum_{i=1}^{K}\\sum_{x\\in C_i}
\\|x-\\mu_i\\|^2
$$

Where:

- `K` = Number of clusters
- `Cᵢ` = Data points in cluster i
- `x` = A data point
- `μᵢ` = Centroid of cluster i

**How It Works**

1. Run K-Means for different values of K.
2. Calculate inertia for each value.
3. Plot K against inertia.
4. Find the elbow, where the decrease starts slowing down.
5. Select a suitable K based on the curve and the problem.

## 3. Apply the Elbow Method

```python
inertias = []
k_values = range(1, 11)

for k in k_values:
    km = KMeans(
        n_clusters=k,
        init="k-means++",
        n_init=10,
        random_state=42
    )

    km.fit(X_scaled)
    inertias.append(km.inertia_)

plt.figure(figsize=(8, 5))

plt.plot(
    k_values,
    inertias,
    marker="o"
)

plt.title("Elbow Method")
plt.xlabel("Number of Clusters (K)")
plt.ylabel("Inertia (WCSS)")
plt.xticks(k_values)
plt.show()
```

**Observation**

- Inertia decreases as K increases.
- The decrease is usually large for smaller K values.
- After the elbow, adding clusters gives smaller improvements.
- In the provided dataset analysis, **K = 5** is selected as a suitable choice.

> **Note:** The elbow is a practical estimate, not a guarantee of a mathematically unique optimum.

**Exercise 1 — Compare Different Values of K**

**Task:** Train K-Means with K = 3, 4, 5, and 6 and compare inertia.

**Solution**

```python
for k in [3, 4, 5, 6]:
    model = KMeans(
        n_clusters=k,
        init="k-means++",
        n_init=10,
        random_state=42
    )

    model.fit(X_scaled)

    print(
        "K =", k,
        "| Inertia =", round(model.inertia_, 2)
    )
```

**Observation**

Inertia generally decreases as K increases. Use the Elbow Method to balance compact clusters with model simplicity.

**Exercise 2 — Cluster Customers by Age and Income**

**Task:** Use Age and Annual Income instead of Annual Income and Spending Score.

**Solution**

```python
X_age_income = df[
    ["Age", "Annual Income (k$)"]
]

scaler2 = StandardScaler()

X_age_income_scaled = scaler2.fit_transform(
    X_age_income
)

model2 = KMeans(
    n_clusters=5,
    init="k-means++",
    n_init=10,
    random_state=42
)

model2.fit(X_age_income_scaled)

df["AgeIncomeCluster"] = model2.labels_

print(df[
    ["Age", "Annual Income (k$)", "AgeIncomeCluster"]
].head())
```

**Observation**

The customer groups may change because age and income represent different characteristics from income and spending score.

**Exercise 3 — Visualize Age and Income Clusters**

**Task:** Plot the clusters created using Age and Annual Income.

**Solution**

```python
plt.figure(figsize=(8, 6))

sns.scatterplot(
    data=df,
    x="Age",
    y="Annual Income (k$)",
    hue="AgeIncomeCluster",
    palette="Set1",
    s=70
)

plt.title("Customer Clusters: Age vs Annual Income")
plt.show()
```

**Observation**

The plot helps compare customers based on age and income. Different colors represent the clusters assigned by K-Means.

**Exercise 4 — Plot the Elbow Curve for Different K Values**

**Task:** Calculate inertia for K values from 2 to 7.

**Solution**

```python
inertias = []
k_values = range(2, 8)

for k in k_values:
    km = KMeans(
        n_clusters=k,
        init="k-means++",
        n_init=10,
        random_state=42
    )

    km.fit(X_scaled)
    inertias.append(km.inertia_)

plt.figure(figsize=(8, 5))

plt.plot(k_values, inertias, marker="o")

plt.xlabel("Number of Clusters (K)")
plt.ylabel("Inertia")
plt.title("Elbow Curve for K = 2 to 7")
plt.xticks(list(k_values))
plt.show()
```

**Observation**

The curve helps identify where adding more clusters gives diminishing improvements. Compare the curve with the full Elbow Method plot before selecting K.

**Real-World Applications**

- Customer segmentation in retail
- Targeted marketing campaigns
- Customer behavior analysis
- Product recommendation
- Image segmentation
- Grouping similar documents
- Exploratory analysis of medical data
