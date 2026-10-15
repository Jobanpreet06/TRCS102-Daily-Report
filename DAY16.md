## DAY 17 OF TRAINING

**Lasso Regression – L1 Regularization and Feature Selection**

Day 17 focused on **Lasso Regression**, a regularization technique that can reduce overfitting and perform feature selection. We learned how Lasso differs from Ridge Regression, explored the alpha parameter, and evaluated house price predictions using MAE and R² Score.

**Learning Objectives:-**

- Understand Lasso Regression (L1)
- Learn how Lasso controls model complexity
- Understand feature selection
- Learn the role of alpha
- Train a Lasso Regression model
- Evaluate model performance
- Compare Ridge and Lasso Regression
- Practice changing alpha values

## 1. What is Lasso Regression?

Lasso Regression is a regularization technique that uses **L1 regularization**.

It reduces model coefficients and can make some coefficients exactly zero. This can remove less useful features or terms from the model.

**Advantages**

- Helps control overfitting.
- Can perform feature selection.
- Produces simpler models when some coefficients become zero.
- Can improve prediction on unseen data.

## 2. Ridge vs Lasso Regression

| Feature | Ridge Regression | Lasso Regression |
|---|---|---|
| Regularization | L2 | L1 |
| Coefficients | Shrinks coefficients | Shrinks coefficients |
| Exact zero coefficients | Usually not | Possible |
| Feature Selection | Does not usually remove features | Can remove less useful features |
| Main Benefit | Controls coefficient size | Controls coefficients and can simplify the model |

## 3. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import Ridge, Lasso
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score
```

## 4. Load and Prepare the Dataset

We use the same preprocessed house price dataset to make comparisons consistent.

```python
df = pd.read_csv("kc_house_preprocessed.csv")

df_sample = df.sample(
    n=80,
    random_state=42
)

X = df_sample[["Scaled_size"]]
y = df_sample["price"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)

print("Training Set:", len(X_train))
print("Testing Set:", len(X_test))
```

**Output**

```text
Training Set: 64
Testing Set: 16
```

## 5. Train the Lasso Regression Model

We use `alpha=100.0` and `max_iter=10000`, as in the original notebook.

```python
lasso_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(
        alpha=100.0,
        max_iter=10000
    )
)

lasso_model.fit(X_train, y_train)

y_pred_lasso = lasso_model.predict(X_test)
```

The polynomial feature transformation is included only to preserve the original experiment setup. The main topic here is Lasso regularization.

## 6. Evaluate the Model

```python
mae_lasso = mean_absolute_error(
    y_test,
    y_pred_lasso
)

r2_lasso = r2_score(
    y_test,
    y_pred_lasso
)

print("MAE:", mae_lasso)
print("R² Score:", r2_lasso)
```

**Reported Output**

```text
Average Miss (MAE): $178,785.42
R² Score: 41.45%
```

These results were reported in the original notebook. Run the code to verify them in your environment.

## 7. Understanding Alpha in Lasso

The alpha parameter controls how strongly Lasso penalizes coefficients.

- **Low alpha:** Weaker regularization.
- **High alpha:** Stronger regularization.
- **Very high alpha:** More coefficients may become zero, but the model may underfit.

The correct alpha should be selected by comparing model performance rather than assuming that a larger value is always better.

## 8. Visualize Lasso Regression

```python
plt.figure(figsize=(10, 6))

plt.scatter(
    X_train["Scaled_size"],
    y_train,
    alpha=0.6,
    label="Actual Houses"
)

x_range = np.linspace(
    X["Scaled_size"].min(),
    X["Scaled_size"].max(),
    500
).reshape(-1, 1)

plt.plot(
    x_range,
    lasso_model.predict(x_range),
    linewidth=2,
    label="Lasso Regression"
)

plt.title("Lasso Regression – House Price Prediction")
plt.xlabel("Scaled House Size")
plt.ylabel("House Price")
plt.legend()
plt.grid(True)
plt.show()
```

**Observation**

The graph compares actual house prices with Lasso predictions. Lasso controls model coefficients, and some coefficients may become zero depending on the data and alpha value.

**Exercise 1 – Change the Lasso Alpha**

**Task**

Change `alpha=100.0` to `alpha=10.0` and compare the results.

**Solution**

```python
lasso_model_1 = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(
        alpha=10.0,
        max_iter=10000
    )
)

lasso_model_1.fit(X_train, y_train)

y_pred = lasso_model_1.predict(X_test)

print("MAE:", mean_absolute_error(y_test, y_pred))
print("R² Score:", r2_score(y_test, y_pred))
```

**Observation**

A lower alpha applies a weaker penalty. This may retain more non-zero coefficients, but its effect on prediction accuracy depends on the dataset.

**Exercise 2 – Test Multiple Alpha Values**

**Task**

Compare Lasso models with alpha values of 1, 10, 100, and 500.

**Solution**

```python
alphas = [1.0, 10.0, 100.0, 500.0]

for alpha in alphas:
    model = make_pipeline(
        PolynomialFeatures(degree=6),
        Lasso(
            alpha=alpha,
            max_iter=10000
        )
    )

    model.fit(X_train, y_train)

    y_pred = model.predict(X_test)

    print("Alpha:", alpha)
    print("MAE:", mean_absolute_error(y_test, y_pred))
    print("R² Score:", r2_score(y_test, y_pred))
    print()
```

**Observation**

Compare MAE and R² Score for each alpha. A suitable value should balance model simplicity and prediction performance.

**Exercise 3 – Compare Ridge and Lasso**

**Task**

Train both models and compare their results.

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

print("Ridge MAE:", mean_absolute_error(y_test, ridge_pred))
print("Ridge R²:", r2_score(y_test, ridge_pred))

print("Lasso MAE:", mean_absolute_error(y_test, lasso_pred))
print("Lasso R²:", r2_score(y_test, lasso_pred))
```

**Reported Results**

| Model | MAE | R² Score |
|---|---:|---:|
| Ridge | $179,774.23 | 40.75% |
| Lasso | $178,785.42 | 41.45% |

**Observation**

In the original notebook, Lasso had a lower MAE and a higher R² Score than Ridge. This does not guarantee that Lasso will perform better on every dataset.

**AI/ML Applications**

- Feature Selection
- House Price Prediction
- Financial Forecasting
- Medical Data Analysis
- Business Analytics
- Predictive Modeling
- Reducing Model Complexity
