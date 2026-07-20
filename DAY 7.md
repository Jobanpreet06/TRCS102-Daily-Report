## DAY 7 OF TRAINING

**Advanced NumPy – Copying, Views, Boolean Masking & Array Operations**

Day 7 focused on advanced **NumPy array operations**, including shallow vs deep copying, array views, boolean masking, advanced indexing, slicing, and conditional filtering. These concepts are essential for efficient data preprocessing and manipulation in AI & Machine Learning.

**Learning Objectives:-**

- Understand NumPy Views and Copies
- Learn Shallow Copy vs Deep Copy
- Perform Advanced Indexing & Slicing
- Apply Boolean Masking
- Filter Arrays Efficiently
- Modify Arrays Safely
- Solve Practical NumPy Exercises

## 1. Copying Arrays

NumPy provides two ways to copy arrays:

| Copy Type | Description |
|------------|-------------|
| Shallow Copy | Shares the same memory with the original array |
| Deep Copy | Creates a completely new array |

## 2. Shallow Copy (View)

A **Shallow Copy** creates another reference to the same data. Any modification in one array affects the other.

**Example**

```python
import numpy as np

arr = np.array([10,20,30,40])

view = arr.view()

view[0] = 100

print("Original:", arr)
print("View:", view)
```

**Output**

```text
Original: [100  20  30  40]
View: [100  20  30  40]
```

**Memory Check**

```python
print(arr.base)

print(view.base)
```

If `base` is not `None`, both arrays share the same memory.

## 3. Deep Copy

A **Deep Copy** creates a completely independent array.

Changes made to the copied array do not affect the original.

**Example**

```python
copy_arr = arr.copy()

copy_arr[1] = 500

print("Original:", arr)

print("Copy:", copy_arr)
```

**Output**

```text
Original: [100 20 30 40]

Copy: [100 500 30 40]
```

**Comparison**

| Feature | View | Copy |
|----------|------|------|
| Shares Memory | ✅ | ❌ |
| Original Changes | Yes | No |
| Faster | ✅ | ❌ |
| Safer | ❌ | ✅ |

## 4. Array Slicing

Slicing extracts a portion of an array.

**Example**

```python
arr = np.arange(1,11)

print(arr[2:7])

print(arr[:5])

print(arr[5:])
```

**Output**

```text
[3 4 5 6 7]

[1 2 3 4 5]

[6 7 8 9 10]
```

**Step Slicing**

```python
print(arr[::2])

print(arr[::-1])
```

**Output**

```text
[1 3 5 7 9]

[10 9 8 7 6 5 4 3 2 1]
```

## 5. Views from Slicing

Array slices are **views**, not copies.

```python
arr = np.array([10,20,30,40,50])

slice_arr = arr[1:4]

slice_arr[0] = 999

print(arr)

print(slice_arr)
```

**Output**

```text
[10 999 30 40 50]

[999 30 40]
```

## 6. Safe Copy of Slice

To prevent changes in the original array, use `.copy()`.

```python
safe_slice = arr[1:4].copy()

safe_slice[0] = 111

print(arr)

print(safe_slice)
```

**Output**

```text
Original: [10 999 30 40 50]

Copy: [111 30 40]
```

## 7. Boolean Masking

Boolean Masking filters data based on conditions.

**Example**

```python
arr1 = np.arange(0,21)

mask = arr1 % 2 == 0

print(mask)
```

**Output**

```text
[ True False True False True False True False True False
 True False True False True False True False True False True]
```

**Extract Even Numbers**

```python
even_numbers = arr1[arr1 % 2 == 0]

print(even_numbers)
```

**Output**

```text
[ 0  2  4  6  8 10 12 14 16 18 20]
```

**AI/ML Applications**

- Data Cleaning
- Feature Selection
- Removing Outliers
- Filtering Missing Values
- Dataset Preparation
- Memory Optimization using Views

## 8. Boolean Indexing with Conditions

Boolean indexing allows selecting elements that satisfy a specific condition.

**Example**

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

**Multiple Conditions**

Use logical operators (`&`, `|`) to apply multiple conditions.

```python
numbers = np.arange(1,21)

filtered = numbers[(numbers >= 5) & (numbers <= 15)]

print(filtered)
```

**Output**

```text
[ 5  6  7  8  9 10 11 12 13 14 15]
```

## 9. Fancy Indexing

Fancy indexing allows selecting multiple elements using index arrays.

**Example**

```python
arr = np.array([10,20,30,40,50,60])

print(arr[[0,2,5]])
```

**Output**

```text
[10 30 60]
```

**Reordering Elements**

```python
arr = np.array([100,200,300,400])

new_arr = arr[[3,2,1,0]]

print(new_arr)
```

**Output**

```text
[400 300 200 100]
```

## 10. Modifying Elements Using Boolean Masking

Boolean masks can also modify array values.

**Example**

```python
arr = np.array([5,12,18,25,7,30])

arr[arr < 10] = 0

print(arr)
```

**Output**

```text
[ 0 12 18 25  0 30]
```

**Practical Example – Student Marks**

```python
marks = np.array([55,42,88,76,34,91,67])

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

**Practical Example – Positive Numbers**

```python
numbers = np.array([-5,8,-2,14,0,-9,20])

positive = numbers[numbers > 0]

print(positive)
```

**Output**

```text
[ 8 14 20]
```

**Exercise 1 – Odd Number Filter**

```python
arr = np.arange(1,21)

odd = arr[arr % 2 != 0]

print(odd)
```

**Output**

```text
[ 1  3  5  7  9 11 13 15 17 19]
```

**Exercise 2 – Deep Copy Verification**

```python
arr = np.array([1,2,3,4])

copy_arr = arr.copy()

copy_arr[0] = 100

print("Original:", arr)

print("Copy:", copy_arr)
```

**Output**

```text
Original: [1 2 3 4]

Copy: [100   2   3   4]
```

**Exercise 3 – Boolean Mask**

```python
arr = np.arange(0,31)

mask = arr > 15

print(arr[mask])
```

**Output**

```text
[16 17 18 19 20 21 22 23 24 25 26 27 28 29 30]
```

**Exercise 4 – Safe Slice Copy**

```python
arr = np.array([10,20,30,40,50])

safe = arr[1:4].copy()

safe[1] = 999

print("Original:", arr)

print("Safe Copy:", safe)
```

**Output**

```text
Original: [10 20 30 40 50]

Safe Copy: [ 20 999  40]
```

**AI/ML Applications**

- Data preprocessing using Boolean Masking
- Feature selection from datasets
- Removing invalid records
- Creating training and testing subsets
- Memory-efficient processing using Views
- Safe dataset manipulation using Copies

