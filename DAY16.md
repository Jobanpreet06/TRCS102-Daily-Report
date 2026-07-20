## DAY 16 OF TRAINING

**Ridge & Lasso Regularization – Preventing Overfitting in Machine Learning**

Day 16 focused on **Regularization**, a technique used to prevent **overfitting** in Machine Learning models. We learned how **Ridge Regression (L2)** and **Lasso Regression (L1)** improve Polynomial Regression by controlling model complexity, reducing unnecessary feature weights, and improving prediction performance. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Overfitting
- Learn the concept of Regularization
- Compare Ridge and Lasso Regression
- Train Polynomial Regression with Regularization
- Evaluate model performance
- Compare MAE and R² Score
- Visualize Regularized Models
- Prevent over-complex Machine Learning models

## 1. What is Overfitting?

Overfitting occurs when a Machine Learning model learns the **training data too perfectly**, including noise and unnecessary patterns. As a result, it performs well on training data but poorly on new or unseen data.

**Example**

- **Overfitted Model:** Memorizes every training example.
- **Good Model:** Learns the general pattern and predicts unseen data accurately.

Regularization helps reduce overfitting by limiting model complexity. :contentReference[oaicite:1]{index=1}

## 2. Types of Regularization

| Regularization | Description |
|---------------|-------------|
| **Ridge Regression (L2)** | Shrinks feature weights closer to zero but never makes them exactly zero. |
| **Lasso Regression (L1)** | Shrinks some feature weights to exactly zero, effectively removing less important features. |

## 3. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score
```

## 4. Load Dataset

Load the preprocessed house price dataset.

```python
df = pd.read_csv("kc_house_preprocessed.csv")

print("Successfully loaded!")

df.head()
```

Select a random sample of 80 houses.

```python
df_sample = df.sample(
    n=80,
    random_state=42
)
```

Choose the feature and target.

```python
X = df_sample[["Scaled_size"]]

y = df_sample["price"]
```

Split the dataset.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)
```

**Output**

```text
Successfully loaded 'kc_house_preprocessed.csv'

Training Set : 64 Houses

Testing Set : 16 Houses
```

The notebook loads the cleaned dataset, selects **80 random samples**, and divides them into **64 training** and **16 testing** records. :contentReference[oaicite:2]{index=2}

## 5. Train Polynomial Regression (Without Regularization)

Train a Degree 6 Polynomial Regression model without applying any regularization.

```python
wild_model = make_pipeline(
    PolynomialFeatures(degree=6),
    LinearRegression()
)

wild_model.fit(
    X_train,
    y_train
)
```

Predict house prices.

```python
y_pred_wild = wild_model.predict(X_test)
```

Calculate performance.

```python
mae_wild = mean_absolute_error(
    y_test,
    y_pred_wild
)

accuracy_wild = r2_score(
    y_test,
    y_pred_wild
)
```

**Output**

```text
Average Miss (MAE): $193,581.71

Accuracy Score (R²): 31.47%
```

This model overfits because it tries to fit the training data too closely. :contentReference[oaicite:3]{index=3}

## 6. Ridge Regression (L2 Regularization)

Ridge Regression reduces overfitting by shrinking model coefficients while keeping all features.

```python
ridge_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=0.1)
)

ridge_model.fit(
    X_train,
    y_train
)
```

Predict values.

```python
y_pred_ridge = ridge_model.predict(X_test)
```

Evaluate performance.

```python
mae_ridge = mean_absolute_error(
    y_test,
    y_pred_ridge
)

accuracy_ridge = r2_score(
    y_test,
    y_pred_ridge
)
```

**Output**

```text
Average Miss (MAE): $179,774.23

Accuracy Score (R²): 40.75%
```

Ridge Regression produces smoother predictions and improves model performance. :contentReference[oaicite:4]{index=4}

## 7. Lasso Regression (L1 Regularization)

Lasso Regression removes less important features by forcing some coefficients to become zero.

```python
lasso_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(
        alpha=100.0,
        max_iter=10000
    )
)

lasso_model.fit(
    X_train,
    y_train
)
```

Predict values.

```python
y_pred_lasso = lasso_model.predict(X_test)
```

Evaluate performance.

```python
mae_lasso = mean_absolute_error(
    y_test,
    y_pred_lasso
)

accuracy_lasso = r2_score(
    y_test,
    y_pred_lasso
)
```

**Output**

```text
Average Miss (MAE): $178,785.42

Accuracy Score (R²): 41.45%
```

Lasso improves prediction accuracy while simplifying the model by removing unnecessary polynomial terms. :contentReference[oaicite:5]{index=5}

## 8. Compare All Models

| Model | MAE | R² Score |
|--------|---------|----------|
| Polynomial Regression | $193,581.71 | 31.47% |
| Ridge Regression | $179,774.23 | 40.75% |
| Lasso Regression | $178,785.42 | 41.45% |

**Observation**

- Polynomial Regression overfits the data.
- Ridge reduces coefficient values and improves accuracy.
- Lasso removes less useful features and gives the best performance among the three models. :contentReference[oaicite:6]{index=6}

## 9. Visualize Regularized Models

Plot all models on the same graph for comparison.

```python
plt.figure(figsize=(12,7))

plt.scatter(
    X_train,
    y_train,
    color="royalblue",
    alpha=0.6,
    label="Actual Houses"
)

x_range = np.linspace(
    X["Scaled_size"].min(),
    X["Scaled_size"].max(),
    500
).reshape(-1,1)

plt.plot(
    x_range,
    wild_model.predict(x_range),
    '--',
    color="orange",
    label="Polynomial"
)

plt.plot(
    x_range,
    ridge_model.predict(x_range),
    color="crimson",
    linewidth=3,
    label="Ridge"
)

plt.plot(
    x_range,
    lasso_model.predict(x_range),
    color="forestgreen",
    linewidth=3,
    label="Lasso"
)

plt.title("Regularization Comparison")

plt.xlabel("Scaled House Size")

plt.ylabel("House Price")

plt.legend()

plt.grid(True)

plt.show()
```

**Observation**

The graph shows that Ridge and Lasso produce smoother prediction curves compared to the highly flexible polynomial model, helping reduce overfitting. :contentReference[oaicite:7]{index=7}

**Exercise 1 – Change Ridge Alpha**

**Task**

Change:

```python
Ridge(alpha=0.1)
```

to

```python
Ridge(alpha=1.0)
```

Compare MAE and R² Score.

**Solution**

```python
ridge_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=1.0)
)

ridge_model.fit(X_train, y_train)

y_pred = ridge_model.predict(X_test)

print("MAE :", mean_absolute_error(y_test, y_pred))
print("R² Score :", r2_score(y_test, y_pred))
```

**Observation**

Increasing **alpha** applies stronger regularization, producing a simpler model. Very high values may reduce overfitting but can also cause underfitting.

**Exercise 2 – Compare Ridge and Lasso**

**Task**

Train both Ridge and Lasso Regression models and compare their performance.

**Solution**

```python
ridge = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=0.1)
)

lasso = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(alpha=100.0, max_iter=10000)
)

ridge.fit(X_train, y_train)
lasso.fit(X_train, y_train)

ridge_pred = ridge.predict(X_test)
lasso_pred = lasso.predict(X_test)

print("Ridge R² :", r2_score(y_test, ridge_pred))
print("Lasso R² :", r2_score(y_test, lasso_pred))
```

**Result**

- Ridge keeps all features while reducing their impact.
- Lasso removes less important features by assigning zero coefficients.
- In this notebook, **Lasso achieved the best R² Score (41.45%)**. :contentReference[oaicite:8]{index=8}

**AI/ML Applications**

- Preventing Overfitting
- Feature Selection
- House Price Prediction
- Stock Market Analysis
- Medical Data Prediction
- Financial Forecasting
- Business Analytics
