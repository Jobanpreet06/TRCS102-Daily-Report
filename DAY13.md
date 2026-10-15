## DAY 13 OF TRAINING

**Statistical Data Visualization using Seaborn**

Day 11 focused on **Statistical Data Visualization using Seaborn**, a Python library built on top of Matplotlib. Seaborn makes it easier to create attractive and informative statistical graphs. The session covered histograms, box plots, and heatmaps, along with their practical applications in Data Analysis and Machine Learning.

**Learning Objectives:-**

- Understand Seaborn and its advantages.
- Learn to create histograms.
- Understand box plots and outlier detection.
- Create heatmaps using numerical data.
- Compare different visualization techniques.
- Apply Seaborn to practical datasets.
- Solve coding exercises related to data visualization.

## 1. Introduction to Seaborn

**Seaborn** is a Python data visualization library built on top of Matplotlib. It is mainly used to create attractive statistical graphs with less code.

**Importing Seaborn**

```python
import seaborn as sns
import matplotlib.pyplot as plt
```

**Advantages of Seaborn**

- Provides attractive default themes.
- Makes statistical visualization easier.
- Works well with Pandas DataFrames.
- Supports different types of statistical plots.
- Helps in Exploratory Data Analysis (EDA).

## 2. Histogram

A **Histogram** shows the frequency distribution of numerical data. It groups values into intervals called bins and displays how many values fall into each interval.

**Example**

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [45, 52, 67, 72, 81, 90, 55, 61, 77, 84]

sns.histplot(marks, bins=5)

plt.title("Distribution of Marks")
plt.xlabel("Marks")
plt.ylabel("Frequency")

plt.show()
```

**Output:** A histogram showing the distribution of student marks across five bins.

**Important Parameters**

- `bins`: Specifies the number of intervals.
- `color`: Changes the color of the histogram.
- `kde=True`: Adds a smooth estimated distribution curve.

**Customized Histogram**

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [45, 52, 67, 72, 81, 90, 55, 61, 77, 84]

sns.histplot(marks, bins=5, kde=True, color="skyblue")

plt.title("Student Marks Distribution")
plt.xlabel("Marks")
plt.ylabel("Frequency")

plt.show()
```

## 3. Box Plot

A **Box Plot** shows the spread and distribution of numerical data. It helps identify possible outliers.

A box plot displays:

- **Median:** The middle value of the data.
- **Quartiles:** Values that divide ordered data into four parts.
- **Whiskers:** Lines showing the spread of data within the plot's whisker limits.
- **Outliers:** Values that fall unusually far from the rest of the data.

**Example**

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [45, 52, 67, 72, 81, 90, 55, 61, 77, 84]

sns.boxplot(y=marks)

plt.title("Box Plot of Marks")
plt.ylabel("Marks")

plt.show()
```

**Output:** A box plot showing the distribution and spread of student marks.

**Example for Outlier Detection**

```python
import seaborn as sns
import matplotlib.pyplot as plt

salary = [25000, 28000, 30000, 32000, 34000, 35000, 90000]

sns.boxplot(y=salary)

plt.title("Employee Salary Distribution")
plt.ylabel("Salary")

plt.show()
```

**Output:** The box plot helps identify the unusually high salary value of `90000` as a potential outlier.

## 4. Heatmap

A **Heatmap** represents numerical values using different colors. It is commonly used to visualize matrices and correlation between numerical variables.

**Example**

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np

data = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
])

sns.heatmap(data, annot=True, cmap="Blues")

plt.title("Sample Heatmap")
plt.show()
```

**Output:** A colored matrix displaying the values from 1 to 9.

**Important Parameters**

| Parameter | Purpose |
|---|---|
| `annot=True` | Displays numerical values inside the cells |
| `cmap` | Sets the color scheme |
| `linewidths` | Adds space between cells |
| `fmt` | Controls the display format of annotations |

**Customized Heatmap**

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np

matrix = np.array([
    [5, 7, 8],
    [6, 9, 4],
    [3, 8, 2]
])

sns.heatmap(matrix,
            annot=True,
            cmap="viridis",
            linewidths=0.5)

plt.title("Sample Heatmap")
plt.show()
```

## 5. Plot Comparison

Different plots are useful for different purposes.

| Plot | Purpose |
|---|---|
| Line Plot | Shows trends over time |
| Bar Plot | Compares values between categories |
| Scatter Plot | Shows the relationship between two numerical variables |
| Histogram | Displays frequency distribution |
| Box Plot | Shows data spread and helps identify outliers |
| Heatmap | Displays matrix values using colors |

## 6. Practical Applications of Seaborn

Seaborn is useful in many Data Analysis and Machine Learning tasks.

- **Exploratory Data Analysis (EDA):** Understanding the structure of a dataset.
- **Outlier Detection:** Finding unusual values using box plots.
- **Distribution Analysis:** Understanding how numerical values are distributed.
- **Correlation Analysis:** Studying relationships between numerical features using correlation heatmaps.
- **Feature Analysis:** Exploring patterns between variables.
- **Data Presentation:** Creating clear and attractive statistical graphs.

**Example: Correlation Heatmap**

A correlation heatmap helps us understand how numerical variables are related.

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd

data = pd.DataFrame({
    "Hours": [1, 2, 3, 4, 5],
    "Marks": [35, 45, 60, 75, 90],
    "Sleep": [8, 7, 8, 6, 7]
})

correlation = data.corr()

sns.heatmap(correlation,
            annot=True,
            cmap="coolwarm")

plt.title("Correlation Heatmap")
plt.show()
```

**Output:** A heatmap showing the correlation coefficients between Hours, Marks, and Sleep.

Correlation values range from `-1` to `+1`:

- `+1` indicates a perfect positive linear relationship.
- `-1` indicates a perfect negative linear relationship.
- `0` indicates no linear correlation.

**Coding Exercises**

**Exercise 1: Create a Histogram**

**Task:** Display the distribution of student ages.

```python
import seaborn as sns
import matplotlib.pyplot as plt

ages = [18, 19, 20, 20, 21, 22, 22, 23, 24, 25, 25, 26]

sns.histplot(ages, bins=5)

plt.title("Age Distribution")
plt.xlabel("Age")
plt.ylabel("Frequency")

plt.show()
```

**Output:** A histogram showing the frequency distribution of student ages.

**Exercise 2: Create a Box Plot**

**Task:** Visualize employee salaries and identify potential outliers.

```python
import seaborn as sns
import matplotlib.pyplot as plt

salary = [25000, 28000, 30000, 32000, 34000, 35000, 90000]

sns.boxplot(y=salary)

plt.title("Employee Salary Distribution")
plt.ylabel("Salary")

plt.show()
```

**Output:** A box plot displaying the salary distribution and highlighting `90000` as a potential outlier.

**Exercise 3: Create a Heatmap**

**Task:** Visualize the values of a numerical matrix.

```python
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

matrix = np.array([
    [5, 7, 8],
    [6, 9, 4],
    [3, 8, 2]
])

sns.heatmap(matrix,
            annot=True,
            cmap="viridis")

plt.title("Sample Heatmap")
plt.show()
```

**Output:** A colored matrix displaying each numerical value.

**Exercise 4: Create a Correlation Heatmap**

**Task:** Find and visualize the correlation between study hours, marks, and sleep hours.

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

data = pd.DataFrame({
    "Hours": [1, 2, 3, 4, 5],
    "Marks": [35, 45, 60, 75, 90],
    "Sleep": [8, 7, 8, 6, 7]
})

sns.heatmap(data.corr(),
            annot=True,
            cmap="coolwarm")

plt.title("Feature Correlation")
plt.show()
```

**Output:** A correlation heatmap showing the relationships between the three numerical variables.

**Exercise 5: Compare a Histogram and Box Plot**

**Task:** Display the same marks data using a histogram and a box plot.

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [45, 52, 67, 72, 81, 90, 55, 61, 77, 84]

plt.figure(figsize=(8, 4))

sns.histplot(marks, bins=5)
plt.title("Distribution of Marks")
plt.xlabel("Marks")
plt.ylabel("Frequency")

plt.show()

sns.boxplot(x=marks)
plt.title("Spread of Marks")
plt.xlabel("Marks")

plt.show()
```

**Output:** The histogram shows the frequency distribution, while the box plot summarizes the spread of the same data.
