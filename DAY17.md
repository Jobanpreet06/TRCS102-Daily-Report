## DAY 18 OF TRAINING

**Multiclass Classification & Logistic Regression**

Day 18 focused on **Multiclass Classification** using Logistic Regression and the Titanic dataset. We learned how to predict one class from three or more possible classes and explored the differences between Binary and Multiclass Classification.

**Learning Objectives:-**

- Understand Multiclass Classification
- Train a Multiclass Logistic Regression model
- Predict passenger classes
- Evaluate model performance using accuracy and classification reports
- Understand Sigmoid and Softmax/One-vs-Rest approaches
- Compare Binary and Multiclass Classification

## 1. What is Multiclass Classification?

Multiclass Classification is a supervised Machine Learning technique used when the target variable has three or more possible classes.

For example, instead of predicting whether a Titanic passenger survived, we can predict the passenger's class.

**Target Variable**

```text
Pclass
```

The three possible classes are:

- Class 1
- Class 2
- Class 3

**Features Used**

- Survived
- Age
- Fare
- SibSp
- Parch
- IsFemale

## 2. Prepare the Dataset

This section uses the preprocessed Titanic dataset from Day 17. The missing values in `Age` and `Embarked` have already been handled, and `IsFemale` has been created.

```python
features_multi = [
    "Survived",
    "Age",
    "Fare",
    "SibSp",
    "Parch",
    "IsFemale"
]

X_multi = df[features_multi]

y_multi = df["Pclass"]
```

Split the dataset into training and testing sets:

```python
X_train_multi, X_test_multi, y_train_multi, y_test_multi = train_test_split(
    X_multi,
    y_multi,
    test_size=0.20,
    random_state=42
)
```

The training data is used to teach the model, and the testing data is used to check its predictions.

## 3. Train the Multiclass Logistic Regression Model

```python
multiclass_model = LogisticRegression(max_iter=1000)

multiclass_model.fit(
    X_train_multi,
    y_train_multi
)

print("Multiclass Logistic Regression Model Trained Successfully")
```

**Output**

```text
Multiclass Logistic Regression Model Trained Successfully
```

The model learns the relationship between the input features and the passenger class.

## 4. Evaluate the Multiclass Model

```python
y_pred_multi = multiclass_model.predict(X_test_multi)

print("Accuracy:", accuracy_score(y_test_multi, y_pred_multi))
```

**Reported Output**

```text
Accuracy: 82.68%
```

The notebook reported an accuracy of approximately 82.68%.

**Note:** The result can vary depending on the data split, preprocessing, and selected features.

## 5. Classification Report

```python
print(
    classification_report(
        y_test_multi,
        y_pred_multi
    )
)
```

**Reported Results**

| Class | Precision | Recall | F1-Score |
|---|---:|---:|---:|
| Class 1 | 0.94 | 0.89 | 0.91 |
| Class 2 | 0.62 | 0.30 | 0.41 |
| Class 3 | 0.81 | 0.98 | 0.88 |

**Explanation**

- **Precision:** Measures how many predictions for a class were correct.
- **Recall:** Measures how many actual passengers belonging to a class were correctly identified.
- **F1-Score:** Combines precision and recall into one score.

The reported results show that performance differs across passenger classes. The model identifies Class 3 passengers well by recall, while Class 2 has a lower recall.

## 6. Binary vs Multiclass Classification

| Feature | Binary Classification | Multiclass Classification |
|---|---|---|
| Number of Classes | Two | Three or more |
| Example | Survived / Not Survived | Passenger Class 1, 2, or 3 |
| Common Approach | Sigmoid for binary logistic regression | Softmax or One-vs-Rest |
| Output | One of two classes | One of multiple classes |
| Example Target | `Survived` | `Pclass` |

## 7. Important Points About Logistic Regression

- Logistic Regression is used for classification problems.
- It estimates the probability of a class.
- Binary Classification predicts one of two classes.
- Multiclass Classification predicts one class from three or more classes.
- The model's performance should be evaluated using testing data.
- Accuracy alone may not fully explain performance, so precision, recall, and F1-score are also useful.

**AI/ML Applications**

- Handwritten Digit Recognition
- Disease Classification
- Image Classification
- Customer Category Prediction
- News Classification
- Product Category Prediction
- Passenger Class Prediction
