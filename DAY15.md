## DAY 15 OF TRAINING

**Polynomial Regression – Teaching Our Robot to Curve!**

Day 15 focused on **Polynomial Regression**, an advanced form of Linear Regression that can model **curved relationships** between input features and target values. We trained a Polynomial Regression model, evaluated its performance using **MAE** and **R² Score**, and learned how polynomial features improve prediction accuracy when data is non-linear. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Polynomial Regression
- Compare Linear vs Polynomial Regression
- Train a Polynomial Regression model
- Create Polynomial Features
- Evaluate model performance
- Interpret MAE and R² Score
- Visualize polynomial curves
- Understand non-linear prediction

## 1. What is Polynomial Regression?

Polynomial Regression is a Machine Learning algorithm that extends Linear Regression by fitting a **curved line** instead of a straight line.

**Why Polynomial Regression?**

Sometimes data does not follow a straight-line relationship.

Examples:

- House Price Prediction
- Population Growth
- Sales Forecasting
- Temperature Prediction

Polynomial Regression introduces higher-degree terms (like **x²**) to capture these curves. :contentReference[oaicite:1]{index=1}

## 2. Linear vs Polynomial Regression

| Linear Regression | Polynomial Regression |
|-------------------|----------------------|
| Fits a straight line | Fits a curved line |
| Works for linear data | Works for non-linear data |
| Simple model | More flexible model |
| Less complex | Better captures complex patterns |

## 3. Import Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
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

To make visualization simpler, a random sample of **80 houses** is selected.

```python
df_sample = df.sample(
    n=80,
    random_state=42
)
```

Split the dataset.

```python
X = df_sample.drop(columns="price")

y = df_sample["price"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)
```

**Output**

```
Training Set : 64 Houses

Testing Set : 16 Houses
```

The notebook loads the preprocessed dataset, samples 80 houses, and splits them into **64 training** and **16 testing** records. :contentReference[oaicite:2]{index=2}

## 5. Train Polynomial Regression Model

A Polynomial Regression model of **Degree 2** is created using a Scikit-learn pipeline.

```python
poly_model = make_pipeline(

    PolynomialFeatures(degree=2),

    LinearRegression()

)
```

Train the model.

```python
poly_model.fit(
    X_train,
    y_train
)

print("Polynomial Regression model trained successfully!")
```

**Output**

```
Polynomial Regression model trained successfully!
```

The model creates squared features internally, allowing it to learn curved relationships. :contentReference[oaicite:3]{index=3}

## 6. Predict House Prices

Predict prices for the testing dataset.

```python
y_pred = poly_model.predict(X_test)
```

Predict prices for the training dataset.

```python
y_train_pred = poly_model.predict(X_train)
```

## 7. Evaluate Model Performance

Calculate prediction accuracy.

```python
mae = mean_absolute_error(
    y_test,
    y_pred
)

accuracy = r2_score(
    y_test,
    y_pred
)

train_accuracy = r2_score(
    y_train,
    y_train_pred
)
```

**Output**

```
Average Miss (MAE) : $174,951.08

Testing Accuracy (R²) : 43.28%

Training Accuracy (R²) : 71.13%
```

These metrics summarize how well the polynomial model performs on both training and testing data. :contentReference[oaicite:4]{index=4}

## 8. Visualize Polynomial Curve

```python
plt.figure(figsize=(10,6))

plt.scatter(
    X,
    y,
    color="royalblue",
    alpha=0.7,
    label="Actual Houses"
)

x_range = np.linspace(
    X["sqft_living"].min(),
    X["sqft_living"].max(),
    500
).reshape(-1,1)

y_range_pred = poly_model.predict(x_range)

plt.plot(
    x_range,
    y_range_pred,
    color="crimson",
    linewidth=3,
    label="Polynomial Curve"
)

plt.title("Polynomial Regression - House Price Prediction")

plt.xlabel("House Size")

plt.ylabel("Price")

plt.legend()

plt.grid(True)

plt.show()
```

**Note**

The notebook reports a **ValueError (`x and y must be the same size`)** while plotting because the scatter plot uses feature and target arrays with incompatible dimensions. This needs to be corrected before the visualization can be displayed. :contentReference[oaicite:5]{index=5}

## 9. Performance Metrics

**Mean Absolute Error (MAE)**

Measures the average prediction error.

**Formula**

```text
MAE = Average(|Actual − Predicted|)
```

Lower MAE indicates better predictions.

**R² Score**

Measures how well the model explains the variation in the data.

| R² Score | Interpretation |
|-----------|----------------|
| 0 | Poor Model |
| 1 | Perfect Model |

Higher R² indicates better model performance. :contentReference[oaicite:6]{index=6}

## 10. Advantages of Polynomial Regression

- Captures curved relationships
- Better prediction for non-linear data
- Improves flexibility
- More accurate than linear regression for complex datasets
- Easy to implement using Scikit-learn

**Exercise 1 – Change Polynomial Degree**

**Task**

Change the polynomial degree from **2** to **3** and compare the model accuracy.

**Solution**

```python
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, r2_score

poly_model = make_pipeline(
    PolynomialFeatures(degree=3),
    LinearRegression()
)

poly_model.fit(X_train, y_train)

y_pred = poly_model.predict(X_test)

print("MAE :", mean_absolute_error(y_test, y_pred))
print("R² Score :", r2_score(y_test, y_pred))
```

**Observation**

- Increasing the polynomial degree makes the model more flexible.
- It may improve prediction accuracy for complex datasets.
- Very high degrees can lead to **overfitting**.

**Exercise 2 – Compare Linear and Polynomial Regression**

**Task**

Train both **Linear Regression** and **Polynomial Regression** models and compare their performance.

**Solution**

```python
from sklearn.linear_model import LinearRegression
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import PolynomialFeatures
from sklearn.metrics import mean_absolute_error, r2_score

# Linear Regression
linear_model = LinearRegression()

linear_model.fit(X_train, y_train)

linear_pred = linear_model.predict(X_test)

# Polynomial Regression
poly_model = make_pipeline(
    PolynomialFeatures(degree=2),
    LinearRegression()
)

poly_model.fit(X_train, y_train)

poly_pred = poly_model.predict(X_test)

print("Linear Regression")
print("MAE :", mean_absolute_error(y_test, linear_pred))
print("R² :", r2_score(y_test, linear_pred))

print("\nPolynomial Regression")
print("MAE :", mean_absolute_error(y_test, poly_pred))
print("R² :", r2_score(y_test, poly_pred))
```

**AI/ML Applications**

- House Price Prediction
- Stock Market Analysis
- Weather Forecasting
- Sales Prediction
- Medical Data Analysis
- Demand Forecasting
- Population Growth Prediction
