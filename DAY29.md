## DAY 29 OF TRAINING

**Customer Churn Prediction – Model Training & Performance Evaluation**

**Introduction**

Today, I learned how to train machine learning models to predict customer churn. After preparing the feature matrix `X` and target variable `y`, the next step is to divide the dataset into training and testing sets.

In this project, I used two classification algorithms: **Logistic Regression** and **Random Forest Classifier**. I also studied how to evaluate their performance using accuracy, a confusion matrix, and a classification report.

**Learning Objectives:-**

- Understand training and testing datasets.
- Learn the purpose of train-test splitting.
- Train Logistic Regression and Random Forest models.
- Predict churn for test data.
- Calculate model accuracy.
- Understand confusion matrices, precision, recall, and F1-score.

## 1. What Is Model Training?

Model training is the process in which a machine learning algorithm learns patterns from existing data.

In this project, the model learns from customer features such as tenure, monthly charges, support tickets, contract type, and feedback-derived features.

After training, the model can predict whether a customer is likely to leave or stay.

## 2. Splitting the Dataset

We divide the data into two parts:

- **Training data:** Used to teach the model.
- **Testing data:** Used to evaluate the model on data that was not used for training.

The PDF uses an 80:20 split, meaning 80% of the data is used for training and 20% for testing.

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42,
    stratify=y
)

print("Training set size:", X_train.shape[0])
print("Testing set size:", X_test.shape[0])
```

**Explanation:**

- `test_size=0.20` reserves 20% of the records for testing.
- `random_state=42` makes the split reproducible.
- `stratify=y` helps maintain a similar proportion of churn and retained customers in both sets.

**Output reported in the PDF:**

```text
Training set size: 400
Testing set size: 100
```

## 3. Model 1 – Logistic Regression

Logistic Regression is a supervised machine learning algorithm commonly used for classification.

It estimates the probability that an observation belongs to a class. Here, the two classes are retained customers (`0`) and churned customers (`1`).

**Python Code**

```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

model_lr = LogisticRegression(
    max_iter=1000,
    random_state=42
)

model_lr.fit(X_train, y_train)

y_pred_lr = model_lr.predict(X_test)

acc_lr = accuracy_score(y_test, y_pred_lr)

print("Logistic Regression Accuracy:",
      f"{acc_lr * 100:.2f}%")
```

**Explanation:**

- `fit()` trains the model.
- `predict()` predicts the churn class for test customers.
- `accuracy_score()` calculates the proportion of correct predictions.

## 4. Model 2 – Random Forest Classifier

Random Forest is a machine learning algorithm that combines the predictions of multiple decision trees.

It can learn more complex patterns in data and is widely used for classification tasks.

**Python Code**

```python
from sklearn.ensemble import RandomForestClassifier

model_rf = RandomForestClassifier(
    n_estimators=100,
    random_state=42
)

model_rf.fit(X_train, y_train)

y_pred_rf = model_rf.predict(X_test)

acc_rf = accuracy_score(y_test, y_pred_rf)

print("Random Forest Accuracy:",
      f"{acc_rf * 100:.2f}%")
```

**Explanation:**

- `n_estimators=100` creates a forest containing 100 decision trees.
- `fit()` trains the Random Forest model.
- `predict()` generates predictions for the test data.
- `accuracy_score()` measures the percentage of correct predictions.

## 5. Comparing the Models

```python
print("Logistic Regression:",
      f"{acc_lr * 100:.2f}%")

print("Random Forest:",
      f"{acc_rf * 100:.2f}%")
```

The PDF reports the following results:

```text
Logistic Regression Accuracy: 100.00%
Random Forest Accuracy: 100.00%
```

**Important:** These are the results printed in the supplied PDF, not independently verified results. An accuracy of 100% is unusually high for a real-world churn prediction problem and should be investigated. Possible causes include data leakage, overly simple or synthetic data, or features that reveal the target.

## 6. Understanding Accuracy

Accuracy measures the proportion of predictions that match the actual labels.

\[
\text{Accuracy} =
\frac{\text{Correct Predictions}}
{\text{Total Predictions}}
\]

For example, if a model correctly predicts 90 out of 100 customers, its accuracy is 90%.

Accuracy alone is not always enough. A model might correctly predict most customers who stay but fail to identify customers who actually leave.

## 7. Confusion Matrix

A confusion matrix compares the actual labels with the model's predicted labels.

```python
from sklearn.metrics import confusion_matrix
import seaborn as sns
import matplotlib.pyplot as plt

cm = confusion_matrix(y_test, y_pred_rf)

sns.heatmap(
    cm,
    annot=True,
    fmt="d",
    cmap="Blues",
    xticklabels=["Retained (0)", "Churned (1)"],
    yticklabels=["Retained (0)", "Churned (1)"]
)

plt.title("Random Forest Confusion Matrix")
plt.xlabel("Predicted Label")
plt.ylabel("Actual Label")
plt.show()
```

The four possible outcomes are:

- **True Positive (TP):** A churned customer is correctly predicted as churned.
- **True Negative (TN):** A retained customer is correctly predicted as retained.
- **False Positive (FP):** A retained customer is incorrectly predicted as churned.
- **False Negative (FN):** A churned customer is incorrectly predicted as retained.

False negatives are particularly important in churn prediction because the company may miss a customer who is about to leave.

## 8. Classification Report

A classification report provides precision, recall, F1-score, and support for each class.

```python
from sklearn.metrics import classification_report

print(
    classification_report(
        y_test,
        y_pred_rf,
        target_names=["Retained (0)", "Churned (1)"]
    )
)
```

**Important Metrics**

**Precision:** Out of all customers predicted as churned, how many actually churned?

\[
\text{Precision}=\frac{TP}{TP+FP}
\]

**Recall:** Out of all customers who actually churned, how many did the model identify?

\[
\text{Recall}=\frac{TP}{TP+FN}
\]

**F1-score:** A combined measure of precision and recall.

\[
F1=2\times\frac{\text{Precision}\times\text{Recall}}
{\text{Precision}+\text{Recall}}
\]

**Support:** The number of actual samples belonging to each class.

**Exercise 1: Split the Dataset into Training and Testing Sets**

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.20, random_state=42,
    stratify=y
)

print(X_train.shape)
print(X_test.shape)
```

**Exercise 2: Train a Logistic Regression Model**

```python
model_lr = LogisticRegression(max_iter=1000)
model_lr.fit(X_train, y_train)

print("Model trained successfully")
```

**Exercise 3: Train a Random Forest Model**

```python
model_rf = RandomForestClassifier(
    n_estimators=100,
    random_state=42
)

model_rf.fit(X_train, y_train)

print("Random Forest trained successfully")
```

**Exercise 4: Calculate Random Forest Accuracy**

```python
y_pred_rf = model_rf.predict(X_test)

accuracy = accuracy_score(y_test, y_pred_rf)

print("Accuracy:", accuracy * 100, "%")
```

**Exercise 5: Display the Classification Report**

```python
print(classification_report(y_test, y_pred_rf))
```

**AI/ML Applications**

Model training and evaluation are used in:

1. Customer churn prediction.
2. Email spam detection.
3. Fraud detection.
4. Loan default prediction.
5. Disease classification.
