## DAY 28 OF TRAINING

**Customer Churn Prediction – NLP, Data Preprocessing & Feature Engineering**

**Introduction**

Today, I continued the Customer Churn Prediction project by studying customer feedback and preparing the dataset for machine learning.

Customer data contains different types of information. Some features are numerical, such as monthly charges, while others are categorical, such as contract type. Customer feedback is written in text form.

Machine learning algorithms generally require numerical input. Therefore, we use **Natural Language Processing (NLP)** and data preprocessing techniques to convert these different types of information into a common feature matrix.

**Learning Objectives:-**

- Understand Natural Language Processing (NLP).
- Learn the basic working of TF-IDF.
- Convert customer feedback into numerical features.
- Encode categorical data.
- Combine numerical, categorical, and text features.
- Create the feature matrix `X` and target variable `y`.

## 1. What Is Natural Language Processing (NLP)?

NLP is a field of AI that helps computers process and analyse human language.

In this project, NLP is used to analyse written customer feedback.

For example:

- Positive feedback: "Customer support was helpful."
- Negative feedback: "The internet is slow and expensive."

These comments may contain useful information about customer satisfaction and possible churn.

## 2. Understanding TF-IDF

**TF-IDF stands for Term Frequency–Inverse Document Frequency.**

It converts text into numerical values that represent the relative importance of words in a collection of documents.

In simple words, TF-IDF helps a machine learning model use words from customer reviews as numerical features.

For example, words such as `service`, `slow`, `expensive`, and `connection` may help describe customer experiences.

TF-IDF does not automatically understand the full meaning or sentiment of a sentence. It represents words and phrases numerically.

## 3. Displaying Customer Feedback

```python
print("--- Feedback from Retained Customers ---")

for text in df[df["Churn"] == 0]["CustomerFeedback"].head(3):
    print(text)

print("\n--- Feedback from Churned Customers ---")

for text in df[df["Churn"] == 1]["CustomerFeedback"].head(3):
    print(text)
```

The PDF provides these examples:

**Retained customers:**
- Customer support was very helpful and polite.
- Smooth connection and fair monthly prices.
- Excellent coverage and fast streaming experience.

**Churned customers:**
- Bad experience, moving to another provider soon.
- Cancel my subscription, worst customer care ever.
- Monthly charges are way too expensive for bad service.

These examples show how written feedback can provide additional information about customer experience.

## 4. Converting Text into TF-IDF Features

```python
from sklearn.feature_extraction.text import TfidfVectorizer

tfidf_vectorizer = TfidfVectorizer(
    max_features=15,
    stop_words="english",
    ngram_range=(1, 2)
)

text_features = tfidf_vectorizer.fit_transform(
    df["CustomerFeedback"]
).toarray()

print("Text Feature Shape:", text_features.shape)
print(tfidf_vectorizer.get_feature_names_out())
```

**Explanation:**

- `max_features=15` limits the vocabulary to 15 selected features.
- `stop_words="english"` removes common English stop words.
- `ngram_range=(1, 2)` allows single words and two-word phrases.
- `fit_transform()` learns the vocabulary and converts text into numerical features.
- `toarray()` converts the result into a dense NumPy array.

The number of columns in the text feature matrix is limited to at most 15.

**Important:** The PDF fits TF-IDF on the complete dataset before splitting the data. For a more reliable model evaluation, TF-IDF should instead be fitted on the training text only and then applied to the test text.

## 5. Converting Text Features into a DataFrame

```python
text_feature_names = [
    f"text_{word}"
    for word in tfidf_vectorizer.get_feature_names_out()
]

df_text_encoded = pd.DataFrame(
    text_features,
    columns=text_feature_names,
    index=df.index
)

print(df_text_encoded.head())
```

This code creates readable column names for the text features.

For example, a word such as `service` may become the feature `text_service`.

The `index=df.index` argument keeps the rows aligned with the original dataset.

## 6. Encoding Categorical Features

Machine learning models need numerical representations of categorical values.

The `Contract` column contains categories such as Month-to-month, One year, and Two year.

We can convert them into dummy variables using Pandas.

```python
df_contract_encoded = pd.get_dummies(
    df[["Contract"]],
    drop_first=True,
    dtype=int
)

print(df_contract_encoded.head())
print(df_contract_encoded.columns)
```

**Explanation:**

- `pd.get_dummies()` converts categories into numerical columns.
- `drop_first=True` removes one category to avoid redundant dummy columns.
- `dtype=int` creates integer values of 0 and 1.

In this encoding, Month-to-month acts as the reference category. The exact dummy columns depend on the categories present in the dataset.

## 7. Selecting Numerical Features

The project uses three numerical features:

```python
df_numeric = df[
    ["Tenure", "MonthlyCharges", "SupportTickets"]
]

print(df_numeric.head())
```

These features represent how long a customer has stayed, how much they pay, and how many support tickets they have raised.

## 8. Combining Features into One Matrix

This process is called **feature fusion**. It combines different types of information into one dataset for machine learning.

```python
X = pd.concat(
    [df_numeric, df_contract_encoded, df_text_encoded],
    axis=1
)

y = df["Churn"]

print("Feature Matrix Shape:", X.shape)
print("Target Shape:", y.shape)
print("\nFeature Columns:")
print(list(X.columns))
```

**Explanation:**

- `X` contains the input features used to predict churn.
- `y` contains the target values that the model must learn to predict.
- `pd.concat(..., axis=1)` combines the columns side by side.

**Output reported in the PDF:**

```text
Combined Feature Matrix X Shape: (500, 20)
Target Shape: (500,)
```

This reported shape means the feature matrix has 500 customer records and 20 features. The result depends on the dataset and the fitted TF-IDF vocabulary.

**Exercise 1: Display the First Five Customer Reviews**

```python
print(df["CustomerFeedback"].head())
```

**Exercise 2: Count the Number of Reviews**

```python
print("Total Reviews:", df["CustomerFeedback"].count())
```

**Exercise 3: Apply TF-IDF to Customer Feedback**

```python
from sklearn.feature_extraction.text import TfidfVectorizer

vectorizer = TfidfVectorizer(max_features=10)

features = vectorizer.fit_transform(
    df["CustomerFeedback"]
)

print("TF-IDF Shape:", features.shape)
```

**Exercise 4: Encode the Contract Column**

```python
encoded_contract = pd.get_dummies(
    df[["Contract"]],
    drop_first=True,
    dtype=int
)

print(encoded_contract.head())
```

**Exercise 5: Create Input and Target Variables**

```python
X = pd.concat(
    [df_numeric, df_contract_encoded, df_text_encoded],
    axis=1
)

y = df["Churn"]

print(X.shape)
print(y.shape)
```

**AI/ML Applications**

NLP and feature engineering are useful in:

1. Customer review analysis.
2. Email spam detection.
3. Sentiment analysis.
4. Product review classification.
5. Customer churn prediction.
