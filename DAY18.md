## DAY 18 OF TRAINING

**Decision Trees & Random Forests**

Day 18 focused on **Decision Trees** and **Random Forests**, two popular tree-based Machine Learning algorithms used for classification problems. Using the **Titanic Dataset**, we learned how trees split data using **Gini Impurity**, how overfitting occurs, techniques to regularize trees, and how Random Forest combines multiple Decision Trees to improve prediction accuracy. We also compared these models with Logistic Regression.

**Learning Objectives:-**

- Understand Decision Tree Classification
- Learn Gini Impurity
- Train Decision Tree Models
- Visualize Decision Trees
- Learn Tree Regularization
- Understand Random Forests
- Learn Feature Importance
- Compare Classification Models
- Evaluate Model Performance

## 1. Why Tree-Based Models?

Decision Trees divide data into smaller groups using conditions.

Unlike Logistic Regression, they do **not** assume a linear relationship and naturally capture complex patterns.

**Comparison**

| Property | Logistic Regression | Decision Tree / Random Forest |
|-----------|---------------------|-------------------------------|
| Decision Boundary | Linear | Non-linear |
| Scaling | Required | Not Required |
| Feature Interaction | Manual | Automatic |
| Interpretation | Coefficients | Tree Structure |

**Advantages**

- Handles non-linear data
- No feature scaling required
- Easy to visualize
- Captures feature interaction automatically

## 2. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.ensemble import RandomForestClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
```

## 3. Load & Preprocess Dataset

**Steps**

- Load Titanic Dataset
- Fill missing Age values
- Fill missing Embarked values
- Convert Gender into numerical values
- Select Features

```python
df=pd.read_csv("train.csv")
```

## 4. Split Dataset

```python
X_train,X_test,y_train,y_test=train_test_split(
X,y,test_size=0.20,random_state=42,stratify=y)
```

**Output**

```
Training : 712 Rows

Testing : 179 Rows
```

## 5. Gini Impurity

**Formula**

```
Gini = 1 − Σ(pi²)
```

| Gini | Meaning |
|------|----------|
| 0 | Pure Node |
| 0.5 | Maximum Impurity |

## 6. Decision Tree Model

```python
model=DecisionTreeClassifier(random_state=42)
model.fit(X_train,y_train)
```

**Output**

```
Tree Depth : 23

Leaves : 161

Train Accuracy : 98.17%

Test Accuracy : 80.45%
```

**Observation**

Deep trees memorize training data and may overfit.

## 7. Visualizing Decision Trees

```python
plot_tree(dt_shallow,
feature_names=X.columns,
filled=True)
```

**How to Read**

- Left → True
- Right → False
- Colors represent predicted class
- Samples indicate number of records

## 8. Tree Regularization

| Hyperparameter | Purpose |
|---------------|---------|
| max_depth | Limits Tree Height |
| min_samples_split | Minimum samples before split |
| min_samples_leaf | Minimum samples in leaf |

**Best Result**

```
max_depth = 3

Accuracy = 81.01%
```

## 9. Random Forest

Random Forest combines many Decision Trees using **Bagging** and **Majority Voting**.

**Steps**

1. Bootstrap Sampling
2. Train Multiple Trees
3. Random Feature Selection
4. Majority Voting

**Advantages**

- Less Overfitting
- Better Accuracy
- Stable Predictions

## 10. Train Random Forest

```python
rf=RandomForestClassifier(
n_estimators=100,
max_depth=5
)
```

**Output**

```
Train Accuracy : 85.81%

Test Accuracy : 78.77%

CV Accuracy : 81.33%
```

## 11. Feature Importance

Feature Importance identifies which features contribute most to predictions.

```python
importance_df=pd.DataFrame(...)
```

**Important Features**

- IsFemale
- Pclass
- Age

## 12. Model Comparison

| Model | Test Accuracy | CV Accuracy |
|---------|--------------|-------------|
| Logistic Regression | 80.45% | 78.66% |
| Decision Tree | **81.01%** | **81.47%** |
| Random Forest | 78.77% | 81.33% |

## 13. Decision Tree vs Random Forest

| Decision Tree | Random Forest |
|--------------|---------------|
| Single Tree | Multiple Trees |
| Faster | Slightly Slower |
| High Variance | Low Variance |
| Can Overfit | Less Overfitting |

**Exercise 1 – Change `n_estimators`**

**Task**

Train the Random Forest model using **10, 50, and 150 trees**. Compare the test accuracy and training time.

**Solution**

```python
import time

estimators = [10, 50, 150]

for n in estimators:

    start = time.time()

    rf_test = RandomForestClassifier(
        n_estimators=n,
        max_depth=5,
        random_state=42
    )

    rf_test.fit(X_train, y_train)

    end = time.time()

    accuracy = accuracy_score(
        y_test,
        rf_test.predict(X_test)
    )

    print(
        f"Trees={n}, Accuracy={accuracy:.4f}, Time={end-start:.3f}s"
    )
```

**Output**

| n_estimators | Test Accuracy | Training Time |
|--------------|--------------|---------------|
| 10 | 75.98% | 0.078 s |
| 50 | 78.21% | 0.204 s |
| 150 | 79.33% | 0.400 s |

**Exercise 2 – Vary `min_samples_leaf`**

**Task**

Train a Decision Tree using:

```
max_depth = 10
```

and change **min_samples_leaf** from **1 to 50**.

**Solution**

```python
leaves = [1, 5, 10, 20, 50]

train_acc = []
test_acc = []

for leaf in leaves:

    dt = DecisionTreeClassifier(
        max_depth=10,
        min_samples_leaf=leaf,
        random_state=42
    )

    dt.fit(X_train, y_train)

    train_acc.append(
        accuracy_score(
            y_train,
            dt.predict(X_train)
        )
    )

    test_acc.append(
        accuracy_score(
            y_test,
            dt.predict(X_test)
        )
    )

print("Leaf | Train | Test")

for l, tr, te in zip(leaves, train_acc, test_acc):
    print(l, tr, te)
```

**Output**

| min_samples_leaf | Train Accuracy | Test Accuracy |
|------------------|---------------|--------------|
| 1 | 93.12% | 77.09% |
| 5 | 87.64% | 77.65% |
| 10 | 85.67% | 78.77% |
| 20 | 83.57% | 79.33% |
| 50 | 81.18% | 78.21% |

**Exercise 3 – Permutation Feature Importance**

**Task**

Find the most important features using **Permutation Importance**.

**Solution**

```python
from sklearn.inspection import permutation_importance

result = permutation_importance(
    rf,
    X_test,
    y_test,
    n_repeats=10,
    random_state=42
)

sorted_index = result.importances_mean.argsort()[::-1]

for i in sorted_index:
    print(
        X.columns[i],
        result.importances_mean[i]
    )
```

**Output**

```
Top Features

1. IsFemale
2. Pclass
3. Age
```

**Exercise 4 – Decision Surface Comparison**

**Task**

Plot the decision boundaries of a **Decision Tree** and a **Random Forest** using **Age** and **Fare**.

**Solution**

```python
from matplotlib.colors import ListedColormap

f1 = "Age"
f2 = "Fare"

X_2d = X_train[[f1, f2]].values
y_2d = y_train.values

dt = DecisionTreeClassifier(
    max_depth=4,
    random_state=42
)

rf = RandomForestClassifier(
    n_estimators=50,
    max_depth=4,
    random_state=42
)

dt.fit(X_2d, y_2d)
rf.fit(X_2d, y_2d)
```

**Output**

Decision boundary plots are generated for both models.
 
**AI/ML Applications**

- Titanic Survival Prediction
- Disease Prediction
- Fraud Detection
- Credit Risk Analysis
- Customer Churn Prediction
- Spam Detection
- Recommendation Systems
