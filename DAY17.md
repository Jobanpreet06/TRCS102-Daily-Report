## DAY 17 OF TRAINING

**Classification & Logistic Regression**

Day 17 focused on **Classification** using **Logistic Regression**. Unlike Regression, which predicts continuous values, Classification predicts **categories or labels**. The session used the **Titanic Dataset** to perform both **Binary Classification (Survived/Not Survived)** and **Multiclass Classification (Passenger Class)** using Logistic Regression. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Classification in Machine Learning
- Learn Binary and Multiclass Classification
- Understand Logistic Regression
- Learn the Sigmoid Function
- Preprocess the Titanic Dataset
- Train Binary Classification Model
- Train Multiclass Classification Model
- Evaluate Models using Accuracy, Confusion Matrix & Classification Report

## 1. What is Classification?

Classification is a supervised Machine Learning technique used to predict **categories or labels** instead of continuous values.

**Types of Classification**

| Type | Description | Example |
|------|-------------|---------|
| Binary Classification | Predicts one of two classes | Survived / Not Survived |
| Multiclass Classification | Predicts one of three or more classes | Passenger Class (1,2,3) |

Examples:

- Spam Detection
- Disease Prediction
- Email Classification
- Titanic Survival Prediction

:contentReference[oaicite:1]{index=1}

## 2. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import (
    accuracy_score,
    confusion_matrix,
    classification_report
)
```

## 3. Load Titanic Dataset

```python
df = pd.read_csv("train.csv")

print(df.shape)

df.head()
```

**Output**

```
Dataset Shape

(891,12)
```

The Titanic dataset contains **891 passenger records** with **12 features** including age, fare, gender, passenger class, and survival status. :contentReference[oaicite:2]{index=2}

## 4. Data Preprocessing

Machine Learning models require numerical data.

**Steps Performed**

- Fill missing values in **Age** using Median
- Fill missing values in **Embarked** using Mode
- Convert **Sex** into numerical values

```python
df["Age"] = df["Age"].fillna(df["Age"].median())

df["Embarked"] = df["Embarked"].fillna(
    df["Embarked"].mode()[0]
)

df["IsFemale"] = df["Sex"].map({
    "female":1,
    "male":0
})
```

Selected Features

```python
features = [

"Age",

"Fare",

"SibSp",

"Parch",

"IsFemale"

]
```

:contentReference[oaicite:3]{index=3}

## 5. Binary Classification

**Target**

```
Survived
```

**Features**

- Age
- Fare
- SibSp
- Parch
- IsFemale

Binary Classification predicts whether a passenger **survived (1)** or **did not survive (0)**. :contentReference[oaicite:4]{index=4}

## 6. Logistic Regression & Sigmoid Function

Logistic Regression calculates a weighted sum of the input features and passes it through the **Sigmoid Function**, producing a probability between **0 and 1**.

**Sigmoid Equation**

```text
σ(z) = 1 / (1 + e⁻ᶻ)
```

**Code**

```python
def sigmoid(z):

    return 1 / (1 + np.exp(-z))
```

If Probability ≥ 0.5

```
Predict Survived
```

Else

```
Predict Not Survived
```

:contentReference[oaicite:5]{index=5}

## 7. Split Dataset

```python
X = df[features]

y = df["Survived"]

X_train, X_test, y_train, y_test = train_test_split(

    X,

    y,

    test_size=0.20,

    random_state=42

)
```

**Output**

```
Training Set : 712 Rows

Testing Set : 179 Rows
```

:contentReference[oaicite:6]{index=6}

## 8. Train Binary Logistic Regression Model

```python
binary_model = LogisticRegression(
    max_iter=1000
)

binary_model.fit(
    X_train,
    y_train
)

y_pred = binary_model.predict(X_test)
```

**Output**

```
Binary Classification Accuracy

78.21%
```

The Binary Logistic Regression model correctly predicts passenger survival with an accuracy of approximately **78.21%**. :contentReference[oaicite:7]{index=7}

## 9. Model Evaluation

**Accuracy**

```python
accuracy_score(y_test,y_pred)
```

Accuracy

```
78.21%
```

**Confusion Matrix**

```python
cm = confusion_matrix(
    y_test,
    y_pred
)
```

Output

```
[[89 16]

 [23 51]]
```

**Classification Report**

```python
print(
classification_report(
y_test,
y_pred
))
```

| Metric | Value |
|---------|-------|
| Precision | 0.78 |
| Recall | 0.77 |
| F1-Score | 0.77 |

:contentReference[oaicite:8]{index=8}

## 10. Multiclass Classification

Instead of predicting survival, the model predicts the **Passenger Class (Pclass)**.

**Target**

```
Pclass
```

**Features**

- Survived
- Age
- Fare
- SibSp
- Parch
- IsFemale

Multiclass Logistic Regression predicts one of **three passenger classes**. :contentReference[oaicite:9]{index=9}

## 11. Train Multiclass Model

```python
features_multi = [

"Survived",

"Age",

"Fare",

"SibSp",

"Parch",

"IsFemale"

]

X = df[features_multi]

y = df["Pclass"]

multiclass_model = LogisticRegression(
    max_iter=1000
)

multiclass_model.fit(
    X_train,
    y_train
)
```

**Output**

```
Multiclass Logistic Regression Model Trained Successfully
```

## 12. Evaluate Multiclass Model

```python
y_pred = multiclass_model.predict(
    X_test
)

accuracy_score(
    y_test,
    y_pred
)
```

**Output**

```
Accuracy

82.68%
```

Classification Report

| Class | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| Class 1 | 0.94 | 0.89 | 0.91 |
| Class 2 | 0.62 | 0.30 | 0.41 |
| Class 3 | 0.81 | 0.98 | 0.88 |

:contentReference[oaicite:10]{index=10}

## 13. Binary vs Multiclass Classification

| Feature | Binary | Multiclass |
|----------|---------|------------|
| Number of Classes | 2 | 3 or More |
| Example | Survived / Not Survived | Passenger Class |
| Function Used | Sigmoid | Softmax / One-vs-Rest |
| Output | Two Classes | Multiple Classes |

:contentReference[oaicite:11]{index=11}

**Exercise 1 – Add Pclass Feature**

**Task**

Add **Pclass** to the Binary Classification model and compare the accuracy.

**Solution**

```python
features_with_pclass = [
    "Age",
    "Fare",
    "SibSp",
    "Parch",
    "IsFemale",
    "Pclass"
]

X = df[features_with_pclass]
y = df["Survived"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)

model = LogisticRegression(max_iter=1000)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

print(
    accuracy_score(y_test, y_pred)
)
```

**Output**

```
Accuracy with Pclass

81.01%

Previous Accuracy

78.21%
```

**Observation**

Adding **Pclass** improves prediction accuracy because passenger class strongly influences survival chances. :contentReference[oaicite:12]{index=12}

**Exercise 2 – Change Threshold**

**Task**

Change the prediction threshold from **0.5** to **0.7**.

**Solution**

```python
probabilities = binary_model.predict_proba(X_test)

prob_survival = probabilities[:,1]

y_pred_custom = (
    prob_survival >= 0.7
).astype(int)

print(
accuracy_score(
    y_test,
    y_pred_custom
))
```

**Observation**

- Higher threshold makes the model more conservative.
- False Positives decrease.
- False Negatives increase.
- Fewer passengers are predicted to survive.

> **Note:** The notebook shows a `NameError` because it uses `X_test_bin`, which was not defined. Replacing it with `X_test` fixes the code. :contentReference[oaicite:13]{index=13}

**AI/ML Applications**

- Spam Detection
- Email Classification
- Disease Prediction
- Fraud Detection
- Customer Churn Prediction
- Sentiment Analysis
- Titanic Survival Prediction
