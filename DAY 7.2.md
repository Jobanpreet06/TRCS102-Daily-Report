## DAY 8 OF TRAINING

**Advanced NumPy – Boolean Masking, Conditional Filtering & Fancy Indexing**

Day 8 focused on selecting, filtering, and modifying NumPy array elements using conditions and index positions. The session covered Boolean masking, multiple conditions, fancy indexing, and conditional array modification. These techniques are important for cleaning data, selecting features, and preparing datasets for AI and Machine Learning.

**Learning Objectives:-**

- Understand Boolean masking.
- Filter arrays using conditions.
- Apply multiple conditions using logical operators.
- Learn fancy indexing.
- Modify array elements using Boolean masks.
- Separate values based on conditions.
- Solve practical NumPy exercises.

## 1. Introduction to Boolean Masking

**Boolean Masking** is a technique used to select array elements based on a condition.

It creates a Boolean array containing `True` and `False` values.

- `True`: The element satisfies the condition.
- `False`: The element does not satisfy the condition.

**Example**

```python
import numpy as np

arr = np.arange(0, 11)

mask = arr % 2 == 0

print(mask)
```

**Output**

```text
[ True False  True False  True False
  True False  True False  True]
```

The condition `arr % 2 == 0` checks which elements are even.

## 2. Extracting Even Numbers

A Boolean mask can be used directly inside an array to select the required elements.

**Example**

```python
import numpy as np

arr = np.arange(0, 21)

even_numbers = arr[arr % 2 == 0]

print(even_numbers)
```

**Output**

```text
[ 0  2  4  6  8 10 12 14 16 18 20]
```

Only the even numbers are selected.

## 3. Boolean Indexing with Conditions

Boolean indexing allows us to select values that satisfy a particular condition.

**Example – Student Marks**

```python
import numpy as np

marks = np.array([45, 82, 91, 33, 67, 58, 95])

passed = marks[marks >= 50]

print(passed)
```

**Output**

```text
[82 91 67 58 95]
```

The code selects marks greater than or equal to 50.

**Selecting Failed Students**

```python
import numpy as np

marks = np.array([55, 42, 88, 76, 34, 91, 67])

failed = marks[marks < 50]

print(failed)
```

**Output**

```text
[42 34]
```

## 4. Applying Multiple Conditions

We can combine two or more conditions using logical operators.

| Operator | Meaning |
|---|---|
| `&` | AND – both conditions must be true |
| `|` | OR – at least one condition must be true |
| `~` | NOT – reverses a Boolean condition |

**Important:** Put each condition inside parentheses when using `&` or `|` with NumPy arrays.

**Example – Select Numbers from 5 to 15**

```python
import numpy as np

numbers = np.arange(1, 21)

filtered = numbers[(numbers >= 5) & (numbers <= 15)]

print(filtered)
```

**Output**

```text
[ 5  6  7  8  9 10 11 12 13 14 15]
```

Both conditions must be true.

**Example – OR Condition**

```python
import numpy as np

numbers = np.arange(1, 11)

result = numbers[(numbers < 4) | (numbers > 8)]

print(result)
```

**Output**

```text
[ 1  2  3  9 10]
```

The result includes numbers less than 4 or greater than 8.

## 5. Fancy Indexing

**Fancy Indexing** is used to select multiple elements by specifying their index positions in a list or array.

**Example**

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50, 60])

print(arr[[0, 2, 5]])
```

**Output**

```text
[10 30 60]
```

The elements at indices 0, 2, and 5 are selected.

**Reordering Elements**

```python
import numpy as np

arr = np.array([100, 200, 300, 400])

new_arr = arr[[3, 2, 1, 0]]

print(new_arr)
```

**Output**

```text
[400 300 200 100]
```

The elements are selected in reverse index order.

**Important:** Fancy indexing returns a copy of the selected data, so modifying the resulting array does not change the original array's elements.

## 6. Modifying Elements Using Boolean Masking

Boolean masking can also be used to modify array values that satisfy a condition.

**Example – Replace Small Numbers**

```python
import numpy as np

arr = np.array([5, 12, 18, 25, 7, 30])

arr[arr < 10] = 0

print(arr)
```

**Output**

```text
[ 0 12 18 25  0 30]
```

All elements smaller than 10 are replaced with 0.

**Practical Example – Positive Numbers**

```python
import numpy as np

numbers = np.array([-5, 8, -2, 14, 0, -9, 20])

positive = numbers[numbers > 0]

print(positive)
```

**Output**

```text
[ 8 14 20]
```

Only positive numbers are selected. Zero is not included because the condition is strictly greater than zero.

**Practical Example – Student Marks**

Boolean masking can separate passed and failed students.

```python
import numpy as np

marks = np.array([55, 42, 88, 76, 34, 91, 67])

passed_students = marks[marks >= 50]
failed_students = marks[marks < 50]

print("Passed:", passed_students)
print("Failed:", failed_students)
```

**Output**

```text
Passed: [55 88 76 91 67]
Failed: [42 34]
```

This technique can help categorize records based on a condition.

**Coding Exercises**

**Exercise 1 – Odd Number Filter**

**Task:** Select all odd numbers from 1 to 20.

```python
import numpy as np

arr = np.arange(1, 21)

odd = arr[arr % 2 != 0]

print(odd)
```

**Output**

```text
[ 1  3  5  7  9 11 13 15 17 19]
```

**Exercise 2 – Boolean Mask**

**Task:** Select all numbers greater than 15 from an array containing numbers from 0 to 30.

```python
import numpy as np

arr = np.arange(0, 31)

mask = arr > 15

print(arr[mask])
```

**Output**

```text
[16 17 18 19 20 21 22 23 24 25 26 27 28 29 30]
```

**Exercise 3 – Multiple Conditions**

**Task:** Select numbers between 10 and 25, including both 10 and 25.

```python
import numpy as np

arr = np.arange(1, 31)

result = arr[(arr >= 10) & (arr <= 25)]

print(result)
```

**Output**

```text
[10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25]
```

**Exercise 4 – Fancy Indexing**

**Task:** Select the elements at indices 1, 3, and 5.

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50, 60])

result = arr[[1, 3, 5]]

print(result)
```

**Output**

```text
[20 40 60]
```

**Exercise 5 – Modify an Array Using a Condition**

**Task:** Replace all numbers below 10 with zero.

```python
import numpy as np

arr = np.array([5, 12, 8, 20, 3, 15])

arr[arr < 10] = 0

print(arr)
```

**Output**

```text
[ 0 12  0 20  0 15]
```

**Exercise 6 – Separate Passed and Failed Students**

**Task:** Separate marks into passed and failed groups, using 50 as the passing mark.

```python
import numpy as np

marks = np.array([35, 60, 48, 75, 90, 42])

passed = marks[marks >= 50]
failed = marks[marks < 50]

print("Passed:", passed)
print("Failed:", failed)
```

**Output**

```text
Passed: [60 75 90]
Failed: [35 48 42]
```

**AI/ML Applications**

- **Data Cleaning:** Filtering invalid or unwanted values.
- **Feature Selection:** Selecting data that meets specific conditions.
- **Outlier Detection:** Identifying unusually high or low values.
- **Dataset Preparation:** Separating records based on conditions.
- **Data Analysis:** Selecting passed students, positive values, or records in a range.
- **Preprocessing:** Replacing unwanted values before training a model.


## ⭐ Day 8 Completed – Boolean Masking, Conditional Filtering & Fancy Indexing
