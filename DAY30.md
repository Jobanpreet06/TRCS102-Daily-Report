## DAY 30 OF TRAINING

**Customer Churn Prediction – Feature Importance & Live Prediction**

**Introduction**

Today, I completed the main stages of the Customer Churn Prediction project by studying feature importance and building a function to predict churn for new customers.

A prediction system should not only produce a result but also help us understand which features may influence the prediction. In this project, Random Forest feature importance is used to inspect the contribution of different input features, and a prediction function accepts customer details and feedback to estimate churn risk.

**Learning Objectives:-**

- Understand feature importance.
- Identify influential customer features.
- Use a trained Random Forest model for prediction.
- Transform new customer feedback using the existing TF-IDF vectorizer.
- Estimate churn probability.
- Generate simple customer retention recommendations.

## 1. What Is Feature Importance?

Feature importance helps us understand which input features contribute most to the predictions made by a model.

In this project, the features include:

- Tenure
- Monthly charges
- Support tickets
- Contract type
- Numerical features extracted from customer feedback

Random Forest provides a feature importance score for each input feature.

A higher score indicates that a feature contributed more to the model's tree-based splits. It does not prove that the feature causes customer churn.

## 2. Finding Important Features

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

feature_importances = pd.Series(
    model_rf.feature_importances_,
    index=X.columns
)

top_features = feature_importances.sort_values(
    ascending=False
).head(10)

print(top_features)

sns.barplot(
    x=top_features.values,
    y=top_features.index
)

plt.title("Top 10 Important Features for Churn Prediction")
plt.xlabel("Feature Importance Score")
plt.ylabel("Feature")
plt.show()
```

**Explanation:**

- `model_rf.feature_importances_` returns the model's feature importance scores.
- `pd.Series()` connects each score to its feature name.
- `sort_values(ascending=False)` arranges the scores from highest to lowest.
- `head(10)` selects the ten highest-scoring features.
- The bar chart displays their relative importance.

The exact ranking must be obtained by running the code on the trained model. The PDF does not provide a complete readable list of the top ten scores.

## 3. Predicting Churn for a New Customer

A live prediction function accepts details about a customer and uses the trained model to estimate whether the customer may leave.

The function needs:

- Customer tenure
- Monthly charges
- Number of support tickets
- Contract type
- Written customer feedback

**Important:** Run the dataset preparation and model training steps from Days 24–26 in the same notebook or Python environment first. The function depends on `model_rf`, `tfidf_vectorizer`, `text_feature_names`, and the training columns in `X`.

## 4. Creating the Prediction Function

```python
def predict_customer_churn(
    tenure,
    monthly_charges,
    support_tickets,
    contract_type,
    feedback_text
):
    # Prepare numerical and contract features
    input_dict = {
        "Tenure": [tenure],
        "MonthlyCharges": [monthly_charges],
        "SupportTickets": [support_tickets],
        "Contract_One year": [
            1 if contract_type == "One year" else 0
        ],
        "Contract_Two year": [
            1 if contract_type == "Two year" else 0
        ]
    }

    # Convert feedback using the fitted TF-IDF vectorizer
    text_vectorized = tfidf_vectorizer.transform(
        [feedback_text]
    ).toarray()

    for i, col_name in enumerate(text_feature_names):
        input_dict[col_name] = [text_vectorized[0][i]]

    # Match the feature columns used during training
    df_input = pd.DataFrame(input_dict)
    df_input = df_input.reindex(columns=X.columns, fill_value=0)

    # Predict churn probability
    churn_prob = model_rf.predict_proba(df_input)[0][1]
    is_churn = churn_prob >= 0.5

    print("=" * 50)
    print("CUSTOMER CHURN RISK REPORT")
    print("=" * 50)

    print(f"Tenure: {tenure} months")
    print(f"Monthly Charges: ${monthly_charges:.2f}")
    print(f"Support Tickets: {support_tickets}")
    print(f"Contract Type: {contract_type}")
    print(f"Feedback: {feedback_text}")

    print(f"Churn Probability: {churn_prob * 100:.1f}%")

    if is_churn:
        print("Risk Status: HIGHER PREDICTED CHURN RISK")
        print("Suggested Action: Review customer concerns and")
        print("consider a suitable retention offer.")
    else:
        print("Risk Status: LOWER PREDICTED CHURN RISK")
        print("Suggested Action: Continue good customer service.")

    print("=" * 50)
```

**Understanding the Code**

- `tfidf_vectorizer.transform()` converts new feedback into the same text feature representation used during training.
- `pd.DataFrame()` creates a row of customer features.
- `reindex(columns=X.columns, fill_value=0)` aligns the new data with the training feature columns.
- `predict_proba()` returns the estimated probabilities for the two classes.
- `[0][1]` selects the estimated probability of churn, class `1`.
- The `0.5` threshold is used here to classify the customer as higher or lower predicted risk.

The risk labels and suggested actions are illustrative. A real business should choose an appropriate threshold and retention policy based on validation results and business requirements.

## 5. Testing the Prediction Function

**Test Case 1: Customer with Possible Warning Signs**

```python
predict_customer_churn(
    tenure=2,
    monthly_charges=95.50,
    support_tickets=5,
    contract_type="Month-to-month",
    feedback_text=(
        "Terrible internet speed, disconnects constantly! "
        "Overpriced charges."
    )
)
```

This test provides a short tenure, high monthly charges, multiple support tickets, and negative feedback.

The model will calculate a probability using the trained data. The actual probability and predicted class must be obtained by running the code.

**Test Case 2: Customer with Positive Feedback**

```python
predict_customer_churn(
    tenure=36,
    monthly_charges=45.00,
    support_tickets=0,
    contract_type="Two year",
    feedback_text=(
        "Love the service, smooth connection and "
        "very helpful customer care!"
    )
)
```

This test provides a longer tenure, fewer support tickets, and positive feedback.

Again, the result depends on the trained model and should not be assumed in advance.

## 6. Understanding Churn Probability

The churn probability is an estimate produced by the model.

For example, if a model returns a probability of `0.75`, it corresponds to an estimated churn probability of 75%.

The example function uses a threshold of 0.5:

- Probability at or above 50%: classified as churn.
- Probability below 50%: classified as retained.

This threshold is only a simple default. It does not guarantee that the model is well calibrated or that a customer will actually leave.

## 7. Customer Retention Recommendations

If the model identifies a customer with higher predicted churn risk, a company could:

1. Review complaints and resolve service problems.
2. Offer a suitable plan based on the customer's needs.
3. Provide better customer support.
4. Review whether charges are appropriate.
5. Follow up to understand the customer's concerns.

These are possible business actions, not guaranteed solutions.

**Exercise 1: Display the Top Five Important Features**

```python
print(
    feature_importances.sort_values(
        ascending=False
    ).head(5)
)
```

**Exercise 2: Display Feature Importance for All Features**

```python
print(feature_importances)
```

**Exercise 3: Predict Churn Probability for a New Customer**

```python
# Assumes df_input has been prepared with the
# same columns used during model training.

probability = model_rf.predict_proba(df_input)[0][1]

print("Churn Probability:", probability)
```

**Exercise 4: Convert Probability into a Class Label**

```python
prediction = 1 if probability >= 0.5 else 0

print("Predicted Churn:", prediction)
```

**Exercise 5: Display a Simple Risk Message**

```python
if probability >= 0.5:
    print("Higher predicted churn risk")
else:
    print("Lower predicted churn risk")
```

**AI/ML Applications**

Feature importance and prediction systems are used in:

1. Customer retention platforms.
2. Telecom customer analysis.
3. Subscription services.
4. E-commerce customer behaviour analysis.
5. Predictive analytics dashboards.
