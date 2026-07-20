## DAY 11 OF TRAINING

**Data Visualization Hands-on Practice – Titanic Dataset**

Day 11 focused on applying **Matplotlib** and **Seaborn** to a real-world dataset (Titanic Dataset). The session involved exploring passenger information, visualizing trends, identifying outliers, and understanding relationships between different features using various graphs. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Load and inspect a real-world dataset
- Perform Exploratory Data Analysis (EDA)
- Visualize Age Distribution
- Analyze Passenger Survival
- Detect Outliers using Box Plot
- Study Relationship between Age & Fare
- Create Correlation Heatmaps
- Interpret visualization results

## 1. Load the Dataset

Import the required libraries and load the Titanic dataset.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("train.csv")

df.head(3)
```

**Check Missing Values**

```python
df.isnull().sum()
```

**Output**

```text
PassengerId      0
Survived         0
Pclass           0
Name             0
Sex              0
Age              0
SibSp            0
Parch            0
Ticket           0
Fare             0
Cabin          687
Embarked         2
```

The notebook begins by loading the Titanic dataset, displaying the first three rows, and checking missing values in each column. :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2}

**Exercise 1 – Load & Inspect Dataset**

**Task**

- Import NumPy, Pandas, Matplotlib and Seaborn.
- Load **train.csv**.
- Display first three rows.
- Check missing values.

**Solution**

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("train.csv")

print(df.head(3))

print(df.isnull().sum())
```

## 2. Age Distribution Histogram

A histogram helps visualize the distribution of passenger ages.

**Code**

```python
plt.figure(figsize=(8,5))

sns.histplot(
    data=df,
    x="Age",
    color="teal",
    kde=True,
    edgecolor="darkgreen"
)

plt.title("Titanic Passenger Age Distribution")

plt.xlabel("Age")

plt.ylabel("Passenger Count")

plt.show()
```

**Observation**

- Most passengers were **young adults (20–35 years)**.

:contentReference[oaicite:3]{index=3}

**Exercise 2 – Age Distribution**

**Task**

- Create histogram
- Enable KDE
- Add title
- Label axes
- Identify most common age group

**Solution**

```python
plt.figure(figsize=(8,5))

sns.histplot(
    data=df,
    x="Age",
    kde=True,
    bins=20,
    color="purple"
)

plt.title("Titanic Passenger Age Distribution")

plt.xlabel("Age (Years)")

plt.ylabel("Passenger Count")

plt.show()
```

**Insight**

Most passengers were between **20–35 years**. :contentReference[oaicite:4]{index=4}

## 3. Survival Count Plot

Count plots compare categorical values.

**Code**

```python
plt.figure(figsize=(8,5))

sns.countplot(
    data=df,
    x="Survived",
    palette="Set2"
)

plt.title("Passenger Survival Count")

plt.xlabel("Survival")

plt.ylabel("Passengers")

plt.show()
```

**Exercise 3 – Passenger Survival**

**Task**

Visualize the number of passengers who survived and those who did not.

**Solution**

```python
plt.figure(figsize=(6,4))

sns.countplot(
    data=df,
    x="Survived",
    palette="Set2"
)

plt.title("Passenger Survival Counts (0 = Died, 1 = Survived)")

plt.xlabel("Survival Status")

plt.ylabel("Number of Passengers")

plt.show()
```

**Insight**

More passengers **died** than survived. :contentReference[oaicite:5]{index=5}

## 4. Box Plot – Fare Distribution

A box plot helps identify outliers.

**Code**

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    data=df,
    x="Fare",
    color="teal"
)

plt.title("Titanic Passenger Fare")

plt.show()
```

**Exercise 4 – Fare Outliers**

**Task**

- Draw a Box Plot
- Identify outliers
- Estimate highest fare

**Solution**

```python
plt.figure(figsize=(8,4))

sns.boxplot(
    data=df,
    x="Fare",
    color="pink"
)

plt.title("Ticket Fare Distribution & Outliers")

plt.xlabel("Ticket Fare")

plt.show()
```

**Insight**

- Many outliers are present.
- Highest fare is **above \$500**.
- Most passengers paid **less than \$50**. :contentReference[oaicite:6]{index=6}

## 5. Scatter Plot – Age vs Fare

Scatter plots show relationships between numerical variables.

**Handle Missing Values**

```python
median_age = df["Age"].median()

df["Age"] = df["Age"].fillna(median_age)
```

**Code**

```python
plt.figure(figsize=(8,5))

sns.scatterplot(
    data=df,
    x="Age",
    y="Fare",
    hue="Survived"
)

plt.title("Passenger Age vs Ticket Fare")

plt.grid(True)

plt.show()
```

**Exercise 5 – Age vs Fare**

**Task**

- Fill missing Age values
- Draw Scatter Plot
- Color passengers using Survival

**Solution**

```python
median_age = df["Age"].median()

df["Age"] = df["Age"].fillna(median_age)

plt.figure(figsize=(8,5))

sns.scatterplot(
    data=df,
    x="Age",
    y="Fare",
    hue="Survived",
    palette="coolwarm"
)

plt.title("Passenger Age vs Ticket Fare")

plt.xlabel("Age (Years)")

plt.ylabel("Ticket Fare")

plt.grid(True)

plt.show()
```

**Insight**

Passengers who paid **higher fares** had a greater chance of survival. :contentReference[oaicite:7]{index=7}

## 6. Correlation Heatmap

Heatmaps display correlation among numerical features.

**Code**

```python
columns = ["Survived","Pclass","Age","Fare"]

corr = df[columns].corr()

sns.heatmap(
    corr,
    annot=True,
    cmap="coolwarm",
    vmax=1,
    vmin=-1
)

plt.show()
```

**Exercise 6 – Correlation Matrix**

**Task**

- Calculate correlation matrix
- Plot Heatmap
- Analyze relationships

**Solution**

```python
numeric_df = df[
    ["Survived","Pclass","Age","Fare"]
]

corr_matrix = numeric_df.corr()

plt.figure(figsize=(6,4.5))

sns.heatmap(
    corr_matrix,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1
)

plt.title("Titanic Features Correlation Grid")

plt.show()
```

**Insights**

- **Pclass** has a **negative correlation** with survival.
- **Fare** has a **positive correlation** with survival.
- First-class passengers had better survival chances. :contentReference[oaicite:8]{index=8}

**AI/ML Applications**

- Exploratory Data Analysis (EDA)
- Outlier Detection
- Data Cleaning
- Feature Relationship Analysis
- Customer Behaviour Analysis
- Data Preprocessing
- Pattern Recognition
