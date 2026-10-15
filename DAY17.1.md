## DAY 17 OF TRAINING

**Binary Classification & Logistic Regression**

Day 17 focused on **Classification and Logistic Regression** using the Titanic dataset. We learned how classification predicts categories instead of continuous values. The main focus was Binary Classification, which predicts whether a passenger survived or did not survive the Titanic disaster.

**Learning Objectives:-**

- Understand Classification in Machine Learning
- Learn Binary Classification
- Understand Logistic Regression
- Learn the Sigmoid Function
- Preprocess the Titanic dataset
- Train a Binary Classification model
- Evaluate the model using accuracy, confusion matrix, and classification report

## 1. What is Classification?

Classification is a supervised Machine Learning technique used to predict categories or labels instead of continuous numerical values.

**Types of Classification**

| Type | Description | Example |
|---|---|---|
| Binary Classification | Predicts one of two classes | Survived / Not Survived |
| Multiclass Classification | Predicts three or more classes | Passenger Class (1, 2, 3) |

Examples of classification include spam detection, disease prediction, email classification, and Titanic survival prediction.

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

## 3. Load the Titanic Dataset

```python
df = pd.read_csv("train.csv")

print(df.shape)

df.head()
```

**Output**

```text
(891, 12)
```

The dataset contains 891 passenger records and 12 columns, including age, fare, gender, passenger class, and survival status.

## 4. Data Preprocessing

Data preprocessing prepares the dataset for Machine Learning.

**Steps Performed**

- Fill missing values in `Age` using the median.
- Fill missing values in `Embarked` using the mode.
- Convert `Sex` into numerical values.

```python
df["Age"] = df["Age"].fillna(df["Age"].median())

df["Embarked"] = df["Embarked"].fillna(
    df["Embarked"].mode()[0]
)

df["IsFemale"] = df["Sex"].map({
    "female": 1,
    "male": 0
})
```

**Select Features**

```python
features = [
    "Age",
    "Fare",
    "SibSp",
    "Parch",
    "IsFemale"
]
```

These features will be used to predict whether a passenger survived.

## 5. Binary Classification

**Target variable:** `Survived`

**Features:**
- Age
- Fare
- SibSp
- Parch
- IsFemale

Binary Classification predicts one of two possible outcomes:

- `1` – Passenger survived
- `0` – Passenger did not survive

## 6. Logistic Regression and Sigmoid Function

Logistic Regression is a Machine Learning algorithm used for classification. It calculates a weighted sum of input features and passes it through the Sigmoid Function to obtain a probability between 0 and 1.

**Sigmoid Function**

```text
σ(z) = 1 / (1 + e^(-z))
```

**Python Code**

```python
def sigmoid(z):
    return 1 / (1 + np.exp(-z))
```

**Prediction Rule**

- If probability ≥ 0.5, predict **Survived**.
- If probability < 0.5, predict **Not Survived**.

## 7. Split the Dataset

```python
X = df[features]

y = df["Survived"]

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
Training Set: 712
Testing Set: 179
```

The training set is used to train the model, while the testing set is used to evaluate its performance.

## 8. Train the Binary Logistic Regression Model

```python
binary_model = LogisticRegression(max_iter=1000)

binary_model.fit(X_train, y_train)

y_pred = binary_model.predict(X_test)
```

**Reported Output**

```text
Binary Classification Accuracy: 78.21%
```

The model predicts passenger survival with a reported accuracy of approximately 78.21%.

## 9. Model Evaluation

**Accuracy**

Accuracy measures the proportion of correct predictions made by the model.

```python
accuracy_score(y_test, y_pred)
```

**Reported accuracy:** 78.21%

**Confusion Matrix**

A confusion matrix compares the actual results with the predicted results.

```python
cm = confusion_matrix(y_test, y_pred)

print(cm)
```

**Reported Output**

```text
[[89 16]
 [23 51]]
```

- **89:** Correctly predicted passengers who did not survive.
- **16:** Passengers who did not survive but were predicted to survive.
- **23:** Passengers who survived but were predicted not to survive.
- **51:** Correctly predicted passengers who survived.

**Classification Report**

```python
print(classification_report(y_test, y_pred))
```

**Reported Summary**

| Metric | Value |
|---|---:|
| Precision | 0.78 |
| Recall | 0.77 |
| F1-Score | 0.77 |

- **Precision:** How many positive predictions were correct.
- **Recall:** How many actual positive cases were identified.
- **F1-Score:** A balance between precision and recall.

**Exercise 1 – Add Pclass Feature**

**Task**

Add `Pclass` to the Binary Classification model and compare the accuracy.

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

print("Accuracy:", accuracy_score(y_test, y_pred))
```

**Reported Results**

| Model | Accuracy |
|---|---:|
| Original Features | 78.21% |
| With Pclass | 81.01% |

**Observation**

Adding `Pclass` can improve prediction because passenger class is related to survival chances.

**Exercise 2 – Change the Prediction Threshold**

**Task**

Change the prediction threshold from 0.5 to 0.7.

**Solution**

```python
probabilities = binary_model.predict_proba(X_test)

prob_survival = probabilities[:, 1]

y_pred_custom = (prob_survival >= 0.7).astype(int)

print("Accuracy:", accuracy_score(y_test, y_pred_custom))
```

**Observation**

- A higher threshold makes the model more conservative when predicting survival.
- Fewer passengers are predicted to survive.
- False positives may decrease, while false negatives may increase.

**AI/ML Applications**

- Spam Detection
- Email Classification
- Disease Prediction
- Fraud Detection
- Customer Churn Prediction
- Sentiment Analysis
- Titanic Survival Prediction
