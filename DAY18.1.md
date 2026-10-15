## DAY 18 OF TRAINING

**Decision Trees – Classification and Overfitting**

Day 18 focused on **Decision Trees**, a supervised Machine Learning algorithm used for classification. We learned about Gini Impurity, trained Decision Tree models, visualized tree structures, and used regularization to reduce overfitting on the Titanic dataset.

**Learning Objectives:-**

- Understand Decision Trees
- Learn Gini Impurity
- Train a Decision Tree classifier
- Visualize tree structures
- Understand overfitting
- Apply regularization
- Evaluate model performance

## 1. What are Decision Trees?

A Decision Tree is a Machine Learning algorithm that makes predictions by dividing data into smaller groups using conditions.

For example, it can predict whether a Titanic passenger survived based on age, gender, passenger class, and fare.

**Advantages**

- Handles non-linear relationships
- Does not require feature scaling
- Easy to understand and visualize
- Automatically captures feature interactions

## 2. Decision Tree vs Logistic Regression

| Feature | Logistic Regression | Decision Tree |
|---|---|---|
| Decision Boundary | Linear | Non-linear |
| Feature Scaling | Usually not required | Not required |
| Interpretability | Coefficients | Tree structure |
| Feature Interaction | May require feature engineering | Captures automatically |

## 3. Import Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
```

## 4. Load and Preprocess Dataset

```python
df = pd.read_csv("train.csv")

df["Age"] = df["Age"].fillna(df["Age"].median())

df["Embarked"] = df["Embarked"].fillna(
    df["Embarked"].mode()[0]
)

df["IsFemale"] = df["Sex"].map({
    "female": 1,
    "male": 0
})
```

Select the features and target.

```python
features = [
    "Pclass",
    "Age",
    "Fare",
    "SibSp",
    "Parch",
    "IsFemale"
]

X = df[features]
y = df["Survived"]
```

Split the dataset.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42,
    stratify=y
)

print("Training Set:", len(X_train))
print("Testing Set:", len(X_test))
```

**Output**

```text
Training Set: 712
Testing Set: 179
```

## 5. Gini Impurity

Gini Impurity measures how mixed the classes are in a Decision Tree node.

**Formula**

```text
Gini = 1 - Σ(pi²)
```

Here, `pi` represents the proportion of each class.

| Gini Value | Meaning |
|---|---|
| 0 | Pure node |
| Higher value | More mixed classes |
| 0.5 | Maximum impurity for two equally represented classes |

The Decision Tree selects splits that reduce impurity.

## 6. Train a Decision Tree

```python
model = DecisionTreeClassifier(
    random_state=42
)

model.fit(X_train, y_train)

y_train_pred = model.predict(X_train)
y_test_pred = model.predict(X_test)

print("Tree Depth:", model.get_depth())
print("Leaves:", model.get_n_leaves())

print("Training Accuracy:",
      accuracy_score(y_train, y_train_pred))

print("Testing Accuracy:",
      accuracy_score(y_test, y_test_pred))
```

**Reported Output**

```text
Tree Depth: 23
Leaves: 161
Training Accuracy: 98.17%
Testing Accuracy: 80.45%
```

**Observation**

The training accuracy is much higher than the testing accuracy. This indicates that the model may be **overfitting**.

## 7. Visualize the Decision Tree

```python
dt_shallow = DecisionTreeClassifier(
    max_depth=3,
    random_state=42
)

dt_shallow.fit(X_train, y_train)

plt.figure(figsize=(16, 8))

plot_tree(
    dt_shallow,
    feature_names=X.columns,
    class_names=["Died", "Survived"],
    filled=True
)

plt.show()
```

**How to Read the Tree**

- Root node: The first decision.
- Left branch: The condition is true.
- Right branch: The condition is false.
- Leaf node: The final prediction.
- Colors: Show the dominant class.

## 8. Regularization in Decision Trees

Overfitting can be reduced by controlling the size of a Decision Tree.

**Important Parameters**

| Parameter | Purpose |
|---|---|
| `max_depth` | Limits tree depth |
| `min_samples_split` | Minimum samples needed to split a node |
| `min_samples_leaf` | Minimum samples required in a leaf |

**Example**

```python
dt = DecisionTreeClassifier(
    max_depth=3,
    random_state=42
)

dt.fit(X_train, y_train)

y_pred = dt.predict(X_test)

print("Testing Accuracy:",
      accuracy_score(y_test, y_pred))
```

**Reported Result**

```text
Optimal Depth: 3
Accuracy: 81.01%
```

A shallower tree can generalize better by learning the main patterns instead of memorizing training data.

**Exercise 1 – Change Tree Depth**

**Task**

Change `max_depth` and compare the testing accuracy.

**Solution**

```python
depths = [2, 3, 5, 10, None]

for depth in depths:
    dt = DecisionTreeClassifier(
        max_depth=depth,
        random_state=42
    )

    dt.fit(X_train, y_train)
    y_pred = dt.predict(X_test)

    print(
        "Depth:", depth,
        "Accuracy:", accuracy_score(y_test, y_pred)
    )
```

**Observation**

- A shallow tree may underfit.
- A very deep tree may overfit.
- The best depth depends on the dataset.

**Exercise 2 – Change Minimum Leaf Samples**

**Task**

Test different values of `min_samples_leaf`.

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
        "Minimum Leaf Samples:", leaf,
        "Accuracy:", accuracy_score(y_test, y_pred)
    )
```

**Observation**

Increasing `min_samples_leaf` makes the tree simpler and can reduce overfitting. If the value becomes too large, the model may underfit.

**AI/ML Applications**

- Fraud Detection
- Disease Prediction
- Loan Approval
- Customer Churn Prediction
- Spam Detection
- Titanic Survival Prediction
