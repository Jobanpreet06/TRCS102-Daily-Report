## DAY 10 OF TRAINING

**Data Visualization using Matplotlib & Seaborn**

Day 10 focused on **Data Visualization** using **Matplotlib** and **Seaborn**, two of the most widely used Python libraries for graphical data representation. The session covered different types of plots, chart customization, and visualization techniques used in Data Analysis, AI, and Machine Learning.

**Learning Objectives:-**

- Understand Data Visualization
- Learn Matplotlib Basics
- Create Line, Bar and Scatter Plots
- Customize Charts
- Understand Seaborn
- Visualize Data Effectively
- Solve Practical Visualization Exercises

## 1. Introduction to Data Visualization

**Data Visualization** is the graphical representation of data that helps identify patterns, trends, relationships, and insights easily.

**Why Data Visualization?**

- Easy to understand large datasets
- Detect trends and patterns
- Compare values visually
- Identify outliers
- Improve decision-making
- Essential in AI & Machine Learning

## 2. Introduction to Matplotlib

**Matplotlib** is a Python library used to create static, animated, and interactive graphs.

**Import Library**

```python
import matplotlib.pyplot as plt
```

**Features**

- Easy to use
- Highly customizable
- Supports multiple chart types
- Widely used in Data Science

## 3. Line Plot

A **Line Plot** is used to show trends over time or continuous data.

**Syntax**

```python
plt.plot(x, y)
plt.show()
```

**Example**

```python
import matplotlib.pyplot as plt

days = [1,2,3,4,5]

sales = [120,150,180,170,210]

plt.plot(days, sales)

plt.title("Daily Sales")

plt.xlabel("Days")

plt.ylabel("Sales")

plt.show()
```

**Output**

Displays a line graph representing daily sales.

**Customized Line Plot**

```python
plt.plot(days, sales,
         color="blue",
         marker="o",
         linestyle="--",
         linewidth=2)

plt.title("Daily Sales")

plt.grid(True)

plt.show()
```

**Common Parameters**

| Parameter | Purpose |
|-----------|---------|
| color | Changes line color |
| marker | Displays data points |
| linestyle | Changes line style |
| linewidth | Changes line thickness |
| label | Adds legend label |

## 4. Bar Plot

A **Bar Plot** compares values between different categories.

**Syntax**

```python
plt.bar(x, y)
plt.show()
```

**Example**

```python
subjects = ["Python","ML","AI","DBMS"]

marks = [92,85,88,80]

plt.bar(subjects, marks)

plt.title("Student Marks")

plt.xlabel("Subjects")

plt.ylabel("Marks")

plt.show()
```

**Output**

Displays a vertical bar chart.

**Horizontal Bar Chart**

```python
plt.barh(subjects, marks)

plt.title("Student Marks")

plt.show()
```

## 5. Scatter Plot

A **Scatter Plot** shows the relationship between two numerical variables.

**Syntax**

```python
plt.scatter(x, y)
plt.show()
```

**Example**

```python
study_hours = [1,2,3,4,5,6,7]

marks = [40,50,58,67,75,86,95]

plt.scatter(study_hours, marks)

plt.title("Study Hours vs Marks")

plt.xlabel("Study Hours")

plt.ylabel("Marks")

plt.show()
```

**Output**

Displays individual points showing the relationship between study hours and marks.

**Customized Scatter Plot**

```python
plt.scatter(study_hours,
            marks,
            color="red",
            marker="*",
            s=150)

plt.grid(True)

plt.show()
```

## 6. Multiple Plots

Different plots can be displayed in the same figure.

```python
plt.figure(figsize=(8,5))

plt.plot(days, sales)

plt.scatter(days, sales)

plt.show()
```

## 7. Adding Legend

```python
plt.plot(days, sales,
         label="Sales")

plt.legend()

plt.show()
```

## 8. Introduction to Seaborn

**Seaborn** is a Python data visualization library built on top of **Matplotlib**. It provides attractive and informative statistical graphics with minimal code.

**Import Seaborn**

```python
import seaborn as sns
import matplotlib.pyplot as plt
```

**Advantages of Seaborn**

- Beautiful default themes
- Better statistical plots
- Easy integration with Pandas
- Supports complex visualizations
- Ideal for Exploratory Data Analysis (EDA)

## 9. Histogram

A **Histogram** shows the frequency distribution of numerical data.

**Syntax**

```python
sns.histplot(data)
plt.show()
```

**Example**

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [45,52,67,72,81,90,55,61,77,84]

sns.histplot(marks, bins=5)

plt.title("Distribution of Marks")

plt.show()
```

**Output**

Displays the frequency distribution of student marks.

## 10. Box Plot

A **Box Plot** represents the spread of data and helps identify outliers.

**Example**

```python
sns.boxplot(y=marks)

plt.title("Box Plot of Marks")

plt.show()
```

**Applications**

- Detect Outliers
- Compare Distributions
- Analyze Data Spread

## 11. Heatmap

A **Heatmap** displays data values using different colors.

**Example**

```python
import numpy as np

data = np.array([
    [1,2,3],
    [4,5,6],
    [7,8,9]
])

sns.heatmap(data,
            annot=True,
            cmap="Blues")

plt.show()
```

**Output**

Displays a colored matrix with annotated values.

## 12. Plot Comparison

| Plot | Purpose |
|------|---------|
| Line Plot | Shows trends over time |
| Bar Plot | Compares categories |
| Scatter Plot | Shows relationship between variables |
| Histogram | Displays frequency distribution |
| Box Plot | Detects outliers and spread |
| Heatmap | Visualizes matrix values |

## 13. Chart Customization

Useful functions for improving visualizations.

```python
plt.title("Chart Title")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.grid(True)
plt.legend()
plt.show()
```

**Coding Exercise 1 – Line Plot**

```python
import matplotlib.pyplot as plt

months = ["Jan","Feb","Mar","Apr","May"]

sales = [120,135,150,170,190]

plt.plot(months, sales, marker="o")

plt.title("Monthly Sales")

plt.xlabel("Month")

plt.ylabel("Sales")

plt.grid(True)

plt.show()
```

**Coding Exercise 2 – Bar Chart**

```python
subjects = ["Python","ML","AI","DBMS"]

marks = [92,88,95,85]

plt.bar(subjects, marks)

plt.title("Subject Marks")

plt.xlabel("Subjects")

plt.ylabel("Marks")

plt.show()
```

**Coding Exercise 3 – Scatter Plot**

```python
hours = [1,2,3,4,5,6]

marks = [35,48,59,72,85,94]

plt.scatter(hours, marks,
            color="red")

plt.title("Study Hours vs Marks")

plt.xlabel("Study Hours")

plt.ylabel("Marks")

plt.grid(True)

plt.show()
```

**Coding Exercise 4 – Histogram**

```python
import seaborn as sns

ages = [18,19,20,20,21,22,22,23,24,25,25,26]

sns.histplot(ages, bins=5)

plt.title("Age Distribution")

plt.show()
```

**Coding Exercise 5 – Box Plot**

```python
salary = [25000,28000,30000,32000,34000,35000,90000]

sns.boxplot(y=salary)

plt.title("Employee Salary Distribution")

plt.show()
```

**Coding Exercise 6 – Heatmap**

```python
import numpy as np

matrix = np.array([
    [5,7,8],
    [6,9,4],
    [3,8,2]
])

sns.heatmap(matrix,
            annot=True,
            cmap="viridis")

plt.title("Sample Heatmap")

plt.show()
```

**AI/ML Applications**

- Exploratory Data Analysis (EDA)
- Model Performance Visualization
- Feature Relationship Analysis
- Outlier Detection
- Correlation Analysis
- Dataset Presentation
- Business Intelligence Dashboards
