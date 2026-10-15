## DAY 19 OF TRAINING

**Random Forests – Ensemble Learning and Model Comparison**

Day 19 focused on **Random Forests**, an ensemble Machine Learning algorithm that combines multiple Decision Trees to improve prediction stability. We trained a Random Forest classifier, evaluated its performance, studied feature importance, and compared different classification models using the Titanic dataset.

**Learning Objectives:-**

- Understand Random Forests
- Learn Bootstrap Sampling and Bagging
- Train a Random Forest classifier
- Evaluate model performance
- Understand Feature Importance
- Compare classification models
- Use Cross-Validation
- Explore decision boundaries

## 1. What is a Random Forest?

Random Forest is a Machine Learning algorithm that combines multiple Decision Trees to make a final prediction.

**How It Works**

1. **Bootstrap Sampling:** Different training samples are created from the dataset.
2. **Random Feature Selection:** Different subsets of features are considered for splitting.
3. **Majority Voting:** The trees vote, and the most common class becomes the final prediction.

**Advantages**

- Reduces overfitting compared with many individual trees
- Provides stable predictions
- Captures non-linear relationships
- Measures feature importance

## 2. Import Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.ensemble import RandomForestClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.linear_model import LogisticRegression

from sklearn.model_selection import cross_val_score

from sklearn.metrics import (
    accuracy_score,
    classification_report,
    confusion_matrix
)

from sklearn.inspection import permutation_importance
```

Use the preprocessed Titanic dataset and the same train-test split as Day 18.

```python
# X_train, X_test, y_train, y_test
# are created using the preprocessing steps from Day 18.
```

## 3. Train Random Forest

```python
rf = RandomForestClassifier(
    n_estimators=100,
    max_depth=5,
    random_state=42
)

rf.fit(X_train, y_train)

y_pred_rf = rf.predict(X_test)

print("Training Accuracy:",
      accuracy_score(y_train, rf.predict(X_train)))

print("Testing Accuracy:",
      accuracy_score(y_test, y_pred_rf))
```

**Reported Output**

```text
Training Accuracy: 85.81%
Testing Accuracy: 78.77%
```

**Cross-Validation**

Cross-validation evaluates a model across different data splits.

```python
scores = cross_val_score(
    rf,
    X,
    y,
    cv=5,
    scoring="accuracy"
)

print("5-Fold CV Accuracy:", scores.mean())
```

**Reported Result**

```text
5-Fold CV Accuracy: 81.33%
```

## 4. Feature Importance

Feature Importance identifies which features contribute most to the Random Forest's predictions.

```python
importance_df = pd.DataFrame({
    "Feature": X.columns,
    "Importance": rf.feature_importances_
})

importance_df = importance_df.sort_values(
    by="Importance",
    ascending=False
)

print(importance_df)
```

**Plot Feature Importance**

```python
plt.figure(figsize=(8, 5))

plt.bar(
    importance_df["Feature"],
    importance_df["Importance"]
)

plt.xlabel("Features")
plt.ylabel("Importance")
plt.title("Random Forest Feature Importance")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

**Important Features**

The notebook identifies these among the important features:

- `IsFemale`
- `Pclass`
- `Age`

Feature importance helps us understand which information is useful for making predictions.

## 5. Compare Classification Models

We compare Logistic Regression, Decision Tree, and Random Forest.

| Model | Test Accuracy | Cross-Validation Accuracy |
|---|---:|---:|
| Logistic Regression | 80.45% | 78.66% |
| Tuned Decision Tree | 81.01% | 81.47% |
| Random Forest | 78.77% | 81.33% |

**Observation**

- The tuned Decision Tree achieved the highest reported test accuracy.
- Random Forest provided competitive cross-validation performance.
- Logistic Regression remained a useful baseline model.

The best model should be selected using appropriate validation rather than training accuracy alone.

**Exercise 1 – Change the Number of Trees**

**Task**

Test different values of `n_estimators`.

**Solution**

```python
estimators = [10, 50, 150]

for n in estimators:
    rf = RandomForestClassifier(
        n_estimators=n,
        max_depth=5,
        random_state=42
    )

    rf.fit(X_train, y_train)

    y_pred = rf.predict(X_test)

    print(
        "Trees:", n,
        "Accuracy:", accuracy_score(y_test, y_pred)
    )
```

**Reported Results**

| Number of Trees | Test Accuracy |
|---:|---:|
| 10 | 75.98% |
| 50 | 78.21% |
| 150 | 79.33% |

**Observation:** Increasing the number of trees can improve stability and accuracy, but it also increases computational time. Actual results may vary with the dataset and settings.

**Exercise 2 – Change `min_samples_leaf`**

**Task**

Compare different minimum leaf sample values.

**Solution**

```python
leaves = [1, 5, 10, 20, 50]

for leaf in leaves:
    dt = DecisionTreeClassifier(
        max_depth=10,
        min_samples_leaf=leaf,
        random_state=42
    )

    dt.fit(X_train, y_train)

    y_pred = dt.predict(X_test)

    print(
        "Leaf Samples:", leaf,
        "Accuracy:", accuracy_score(y_test, y_pred)
    )
```

**Observation**

- Increasing the minimum leaf size makes the tree simpler.
- A simpler tree may reduce overfitting.
- Very large leaf sizes can reduce accuracy.

**Exercise 3 – Permutation Feature Importance**

**Task**

Use permutation importance to identify important features.

**Solution**

```python
result = permutation_importance(
    rf,
    X_test,
    y_test,
    n_repeats=10,
    random_state=42
)

importance_df = pd.DataFrame({
    "Feature": X_test.columns,
    "Importance": result.importances_mean
}).sort_values(
    by="Importance",
    ascending=False
)

print(importance_df)
```

**Observation**

Permutation importance measures how much model performance decreases when a feature's values are shuffled.

The notebook identifies `IsFemale`, `Pclass`, and `Age` among the important features.

**Exercise 4 – Decision Surface**

**Task**

Compare the decision boundaries of a Decision Tree and Random Forest using `Age` and `Fare`.

**Solution**

```python
import numpy as np
import matplotlib.pyplot as plt

X_surface = df[["Age", "Fare"]]
y_surface = df["Survived"]

X_train_s, X_test_s, y_train_s, y_test_s = train_test_split(
    X_surface,
    y_surface,
    test_size=0.20,
    random_state=42,
    stratify=y_surface
)

dt = DecisionTreeClassifier(
    max_depth=5,
    random_state=42
)

rf = RandomForestClassifier(
    n_estimators=100,
    max_depth=5,
    random_state=42
)

dt.fit(X_train_s, y_train_s)
rf.fit(X_train_s, y_train_s)

age_min, age_max = X_surface["Age"].min(), X_surface["Age"].max()
fare_min, fare_max = X_surface["Fare"].min(), X_surface["Fare"].max()

age_grid, fare_grid = np.meshgrid(
    np.linspace(age_min, age_max, 100),
    np.linspace(fare_min, fare_max, 100)
)

grid = pd.DataFrame({
    "Age": age_grid.ravel(),
    "Fare": fare_grid.ravel()
})

fig, axes = plt.subplots(1, 2, figsize=(12, 5))

for ax, model, title in zip(
    axes,
    [dt, rf],
    ["Decision Tree", "Random Forest"]
):
    predictions = model.predict(grid).reshape(age_grid.shape)

    ax.contourf(
        age_grid,
        fare_grid,
        predictions,
        alpha=0.3
    )

    ax.scatter(
        X_test_s["Age"],
        X_test_s["Fare"],
        c=y_test_s,
        edgecolors="black"
    )

    ax.set_title(title)
    ax.set_xlabel("Age")
    ax.set_ylabel("Fare")

plt.tight_layout()
plt.show()
```

**Observation**

- A Decision Tree produces sharp, region-based decision boundaries.
- A Random Forest combines predictions from multiple trees, often producing more stable boundaries.

**AI/ML Applications**

- Fraud Detection
- Disease Prediction
- Credit Risk Analysis
- Loan Approval
- Customer Churn Prediction
- Feature Selection
- Titanic Survival Prediction
