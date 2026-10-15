## DAY 10 OF TRAINING

**Data Visualization Basics using Matplotlib**

Day 10 focused on **Data Visualization using Matplotlib**, a popular Python library used to represent data through graphs and charts. The session covered line plots, bar plots, scatter plots, multiple plots, and chart customization. These techniques help us understand data easily and identify patterns, trends, and relationships.

**Learning Objectives:-**

- Understand the meaning and importance of Data Visualization.
- Learn the basics of Matplotlib.
- Create line, bar, and scatter plots.
- Customize charts using titles, labels, colors, and markers.
- Display multiple plots in one figure.
- Add legends and grids to charts.
- Solve practical visualization exercises.

## 1. Introduction to Data Visualization

**Data Visualization** is the graphical representation of data using charts, graphs, and diagrams.

**Why is Data Visualization Important?**

- Makes large datasets easier to understand.
- Helps identify patterns and trends.
- Makes comparison between values easier.
- Helps identify unusual values.
- Supports better decision-making.
- Is useful in Data Analysis, AI, and Machine Learning.

## 2. Introduction to Matplotlib

**Matplotlib** is a Python library used to create static, animated, and interactive graphs.

**Importing Matplotlib**

```python
import matplotlib.pyplot as plt
```

**Features of Matplotlib**

- Easy to use.
- Supports different types of graphs.
- Allows chart customization.
- Works well with NumPy and Pandas.
- Is widely used in Data Science.

## 3. Line Plot

A **Line Plot** is used to show trends or changes in data over time.

**Example**

```python
import matplotlib.pyplot as plt

days = [1, 2, 3, 4, 5]
sales = [120, 150, 180, 170, 210]

plt.plot(days, sales)

plt.title("Daily Sales")
plt.xlabel("Days")
plt.ylabel("Sales")

plt.show()
```

**Output:** A line graph showing the changes in daily sales.

**Customized Line Plot**

```python
import matplotlib.pyplot as plt

days = [1, 2, 3, 4, 5]
sales = [120, 150, 180, 170, 210]

plt.plot(days, sales,
         color="blue",
         marker="o",
         linestyle="--",
         linewidth=2,
         label="Sales")

plt.title("Daily Sales")
plt.xlabel("Days")
plt.ylabel("Sales")
plt.grid(True)
plt.legend()

plt.show()
```

**Common Parameters**

| Parameter | Purpose |
|---|---|
| `color` | Changes the line color |
| `marker` | Displays markers at data points |
| `linestyle` | Changes the line style |
| `linewidth` | Changes line thickness |
| `label` | Gives a name to the plotted data |

## 4. Bar Plot

A **Bar Plot** is used to compare values among different categories.

**Example**

```python
import matplotlib.pyplot as plt

subjects = ["Python", "ML", "AI", "DBMS"]
marks = [92, 85, 88, 80]

plt.bar(subjects, marks)

plt.title("Student Marks")
plt.xlabel("Subjects")
plt.ylabel("Marks")

plt.show()
```

**Output:** A vertical bar chart comparing marks in different subjects.

**Horizontal Bar Chart**

A horizontal bar chart displays bars from left to right.

```python
import matplotlib.pyplot as plt

subjects = ["Python", "ML", "AI", "DBMS"]
marks = [92, 85, 88, 80]

plt.barh(subjects, marks)

plt.title("Student Marks")
plt.xlabel("Marks")
plt.ylabel("Subjects")

plt.show()
```

**Output:** A horizontal bar chart showing marks for each subject.

## 5. Scatter Plot

A **Scatter Plot** displays individual points to show the relationship between two numerical variables.

For example, it can help us understand the relationship between study hours and marks.

**Example**

```python
import matplotlib.pyplot as plt

study_hours = [1, 2, 3, 4, 5, 6, 7]
marks = [40, 50, 58, 67, 75, 86, 95]

plt.scatter(study_hours, marks)

plt.title("Study Hours vs Marks")
plt.xlabel("Study Hours")
plt.ylabel("Marks")

plt.show()
```

**Output:** A scatter plot showing the relationship between study hours and marks.

**Customized Scatter Plot**

```python
import matplotlib.pyplot as plt

study_hours = [1, 2, 3, 4, 5, 6, 7]
marks = [40, 50, 58, 67, 75, 86, 95]

plt.scatter(study_hours, marks,
            color="red",
            marker="*",
            s=150)

plt.title("Study Hours vs Marks")
plt.xlabel("Study Hours")
plt.ylabel("Marks")
plt.grid(True)

plt.show()
```

Here, `color` changes the point color, `marker` changes the point shape, and `s` controls the marker size.

## 6. Multiple Plots in One Figure

We can display a line plot and a scatter plot together to compare the same data in different ways.

```python
import matplotlib.pyplot as plt

days = [1, 2, 3, 4, 5]
sales = [120, 150, 180, 170, 210]

plt.figure(figsize=(8, 5))

plt.plot(days, sales, label="Sales Trend")
plt.scatter(days, sales, label="Sales Points")

plt.title("Daily Sales Analysis")
plt.xlabel("Days")
plt.ylabel("Sales")
plt.legend()
plt.grid(True)

plt.show()
```

**Output:** A graph showing the sales trend with individual data points.

## 7. Chart Customization

Chart customization makes graphs easier to read and understand.

| Function | Purpose |
|---|---|
| `plt.title()` | Adds a chart title |
| `plt.xlabel()` | Adds a label to the X-axis |
| `plt.ylabel()` | Adds a label to the Y-axis |
| `plt.grid(True)` | Displays grid lines |
| `plt.legend()` | Displays labels for plotted data |
| `plt.figure(figsize=(8,5))` | Sets the figure size |
| `plt.show()` | Displays the graph |

**Coding Exercises**

**Exercise 1: Create a Line Plot**

**Task:** Display monthly sales using a line graph.

```python
import matplotlib.pyplot as plt

months = ["Jan", "Feb", "Mar", "Apr", "May"]
sales = [120, 135, 150, 170, 190]

plt.plot(months, sales, marker="o")

plt.title("Monthly Sales")
plt.xlabel("Month")
plt.ylabel("Sales")
plt.grid(True)

plt.show()
```

**Output:** A line graph showing the increase in monthly sales.

**Exercise 2: Create a Bar Chart**

**Task:** Compare marks in different subjects.

```python
import matplotlib.pyplot as plt

subjects = ["Python", "ML", "AI", "DBMS"]
marks = [92, 88, 95, 85]

plt.bar(subjects, marks)

plt.title("Subject Marks")
plt.xlabel("Subjects")
plt.ylabel("Marks")

plt.show()
```

**Output:** A bar chart comparing the marks obtained in four subjects.

**Exercise 3: Create a Scatter Plot**

**Task:** Show the relationship between study hours and marks.

```python
import matplotlib.pyplot as plt

hours = [1, 2, 3, 4, 5, 6]
marks = [35, 48, 59, 72, 85, 94]

plt.scatter(hours, marks, color="red")

plt.title("Study Hours vs Marks")
plt.xlabel("Study Hours")
plt.ylabel("Marks")
plt.grid(True)

plt.show()
```

**Output:** A scatter plot showing that marks generally increase as study hours increase in the given data.

**Exercise 4: Customize a Graph**

**Task:** Create a line graph with a title, markers, a legend, and grid lines.

```python
import matplotlib.pyplot as plt

days = [1, 2, 3, 4, 5]
temperature = [25, 27, 29, 28, 32]

plt.plot(days, temperature,
         color="green",
         marker="o",
         linestyle="--",
         label="Temperature")

plt.title("Daily Temperature")
plt.xlabel("Days")
plt.ylabel("Temperature")
plt.legend()
plt.grid(True)

plt.show()
```

**Output:** A customized line graph showing daily temperature changes.

**AI/ML Applications**

- **Exploratory Data Analysis (EDA):** Understanding data before training a model.
- **Model Performance Visualization:** Displaying model results using graphs.
- **Trend Analysis:** Understanding changes in data over time.
- **Feature Analysis:** Exploring relationships between variables.
- **Data Presentation:** Presenting findings in an understandable way.
