## DAY 16 OF TRAINING

**Ridge Regression – L2 Regularization**

Day 16 focused on **Ridge Regression**, a regularization technique used to reduce overfitting in Machine Learning. We learned how Ridge Regression controls model coefficients, how the `alpha` parameter affects the model, and how to evaluate predictions using MAE and R² Score.

**Learning Objectives:-**

- Understand Regularization
- Learn Ridge Regression (L2)
- Understand how Ridge reduces overfitting
- Learn the role of the alpha parameter
- Train a Ridge Regression model
- Evaluate performance using MAE and R² Score
- Visualize model predictions
- Practice changing regularization strength

## 1. What is Regularization?

Regularization is a technique used to control the complexity of a Machine Learning model. It adds a penalty to the learning process to prevent the model from relying too heavily on large coefficients.

It helps reduce overfitting and may improve performance on unseen data.

## 2. What is Ridge Regression?

Ridge Regression is a regularization technique that uses **L2 regularization**.

It reduces the size of model coefficients but generally does not make them exactly zero.

**Advantages**

- Helps reduce overfitting.
- Controls large coefficients.
- Can improve prediction on unseen data.
- Keeps all input features in the model.

## 3. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import Ridge
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score
```

## 4. Load and Prepare the Dataset

We use the preprocessed house price dataset, `kc_house_preprocessed.csv`.

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

The dataset is divided into training and testing sets. The training data teaches the model, while the testing data evaluates its performance.

## 5. Train the Ridge Regression Model

We use Ridge Regression with `alpha=0.1`. The degree 6 feature transformation is retained from the original notebook so that regularization can be compared under the same setup. Polynomial Regression itself is not being introduced again here.

```python
ridge_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=0.1)
)

ridge_model.fit(X_train, y_train)

y_pred_ridge = ridge_model.predict(X_test)
```

## 6. Evaluate the Model

**Mean Absolute Error (MAE)**

MAE measures the average absolute difference between actual and predicted house prices. Lower MAE is generally better.

**R² Score**

R² Score measures how well the model explains variation in house prices. A higher score is generally better when comparing models on the same test data.

```python
mae_ridge = mean_absolute_error(
    y_test,
    y_pred_ridge
)

r2_ridge = r2_score(
    y_test,
    y_pred_ridge
)

print("MAE:", mae_ridge)
print("R² Score:", r2_ridge)
```

**Reported Output**

```text
Average Miss (MAE): $179,774.23
R² Score: 40.75%
```

These are the results recorded in the original notebook. Actual values should be verified by running the code with the same dataset and split.

## 7. Understanding the Alpha Parameter

The `alpha` parameter controls the strength of regularization.

- **Low alpha:** Applies a weaker penalty.
- **High alpha:** Applies a stronger penalty and shrinks coefficients more.
- **Very high alpha:** May make the model too simple and cause underfitting.

The best alpha depends on the dataset, so different values should be tested.

## 8. Visualize Ridge Regression

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
    ridge_model.predict(x_range),
    linewidth=2,
    label="Ridge Regression"
)

plt.title("Ridge Regression – House Price Prediction")
plt.xlabel("Scaled House Size")
plt.ylabel("House Price")
plt.legend()
plt.grid(True)
plt.show()
```

**Observation**

The graph compares actual house prices with Ridge predictions. Regularization controls the size of coefficients and can reduce overly complex predictions.

**Exercise 1 – Change the Alpha Value**

**Task**

Change `alpha=0.1` to `alpha=1.0` and compare MAE and R² Score.

**Solution**

```python
ridge_model_1 = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=1.0)
)

ridge_model_1.fit(X_train, y_train)

y_pred = ridge_model_1.predict(X_test)

print("MAE:", mean_absolute_error(y_test, y_pred))
print("R² Score:", r2_score(y_test, y_pred))
```

**Observation**

Increasing alpha applies stronger regularization. It may improve generalization, but excessive regularization can cause underfitting.

**Exercise 2 – Test Multiple Alpha Values**

**Task**

Compare Ridge Regression using alpha values of 0.01, 0.1, 1.0, and 10.0.

**Solution**

```python
alphas = [0.01, 0.1, 1.0, 10.0]

for alpha in alphas:
    model = make_pipeline(
        PolynomialFeatures(degree=6),
        Ridge(alpha=alpha)
    )

    model.fit(X_train, y_train)

    y_pred = model.predict(X_test)

    print("Alpha:", alpha)
    print("MAE:", mean_absolute_error(y_test, y_pred))
    print("R² Score:", r2_score(y_test, y_pred))
    print()
```

**Observation**

Compare the results to find an alpha value that gives lower MAE and higher R² Score on the test data.

**AI/ML Applications**

- House Price Prediction
- Financial Forecasting
- Sales Prediction
- Business Analytics
- Medical Data Analysis
- Preventing Overfitting
