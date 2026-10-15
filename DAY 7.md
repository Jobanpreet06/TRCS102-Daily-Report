## DAY 7 OF TRAINING

**Advanced NumPy – Views, Copies and Array Slicing**

Day 7 focused on advanced NumPy operations, including views, copies, shallow vs deep copying, and array slicing. These concepts help us understand how NumPy handles memory and how to modify arrays safely. They are useful for efficient data manipulation and preprocessing in AI and Machine Learning.

**Learning Objectives:-**

- Understand NumPy views and copies.
- Learn the difference between views and independent copies.
- Perform array slicing and step slicing.
- Understand how slicing affects the original array.
- Create safe copies of arrays and slices.
- Check whether arrays share memory.
- Solve practical NumPy exercises.

## 1. Introduction to NumPy

**NumPy** is a Python library used to work with numerical data and multidimensional arrays. It provides fast operations for mathematical calculations and data manipulation.

```python
import numpy as np

arr = np.array([10, 20, 30, 40])

print(arr)
```

**Output**

```text
[10 20 30 40]
```

## 2. Views and Copies

NumPy provides different ways to create another array from existing data.

| Feature | View | Copy |
|---|---|---|
| Memory | Shares data with original array | Has independent data |
| Changes to elements | Can affect the original | Do not affect the original |
| Memory usage | Usually lower | Usually higher |
| Use | Efficient data access | Safe, independent modification |

**Important:** In NumPy, `arr.view()` creates a view that shares the same underlying data. The `.copy()` method creates an independent copy.

## 3. View (Shallow Copy)

A **view** is another way to access the same underlying array data. Changes to the elements through the view can affect the original array.

**Example**

```python
import numpy as np

arr = np.array([10, 20, 30, 40])

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

Here, changing the first element through `view` also changes the original array.

**Checking Memory Sharing**

```python
print(np.shares_memory(arr, view))
```

**Output**

```text
True
```

`np.shares_memory()` checks whether two arrays share memory.

You can also check the `base` attribute:

```python
print(view.base)
```

For a view created directly from `arr`, this generally refers to the original array.

## 4. Deep Copy Using `.copy()`

A **copy** creates an independent array. Changes to the copied array do not affect the original array.

**Example**

```python
import numpy as np

arr = np.array([10, 20, 30, 40])

copy_arr = arr.copy()
copy_arr[1] = 500

print("Original:", arr)
print("Copy:", copy_arr)
```

**Output**

```text
Original: [10 20 30 40]
Copy: [ 10 500  30  40]
```

**Memory Check**

```python
print(np.shares_memory(arr, copy_arr))
```

**Output**

```text
False
```

The two arrays do not share their element data.

**Important point:** For ordinary NumPy arrays, `.copy()` makes a copy of the array data. For arrays containing Python objects, the contained objects themselves are not recursively copied.

## 5. Array Slicing

**Array slicing** is used to select a portion of an array.

**Syntax**

```python
array[start:stop:step]
```

- `start`: Index from which selection begins.
- `stop`: Index where selection ends, but that index is not included.
- `step`: Number of positions to skip between selected elements.

**Example**

```python
import numpy as np

arr = np.arange(1, 11)

print(arr[2:7])
print(arr[:5])
print(arr[5:])
```

**Output**

```text
[3 4 5 6 7]
[1 2 3 4 5]
[ 6  7  8  9 10]
```

## 6. Step Slicing

Step slicing selects elements at regular intervals.

**Example**

```python
import numpy as np

arr = np.arange(1, 11)

print(arr[::2])
print(arr[::-1])
```

**Output**

```text
[1 3 5 7 9]
[10  9  8  7  6  5  4  3  2  1]
```

- `arr[::2]` selects every second element.
- `arr[::-1]` reverses the array.

## 7. Views Created Through Slicing

Basic slicing in NumPy usually creates a view instead of a copy. Therefore, changing an element of a sliced array can change the original array.

**Example**

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])

slice_arr = arr[1:4]
slice_arr[0] = 999

print("Original:", arr)
print("Slice:", slice_arr)
```

**Output**

```text
Original: [ 10 999  30  40  50]
Slice: [999  30  40]
```

The original array changes because the slice shares its data.

## 8. Creating a Safe Copy of a Slice

If you want to modify a slice without changing the original array, use `.copy()`.

**Example**

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])

safe_slice = arr[1:4].copy()
safe_slice[0] = 111

print("Original:", arr)
print("Safe Copy:", safe_slice)
```

**Output**

```text
Original: [10 20 30 40 50]
Safe Copy: [111  30  40]
```

The original array remains unchanged.

**Coding Exercises**

**Exercise 1 – View Modification**

**Task:** Create a view of an array and change its first element.

```python
import numpy as np

arr = np.array([1, 2, 3, 4])

view = arr.view()
view[0] = 100

print("Original:", arr)
print("View:", view)
```

**Output**

```text
Original: [100   2   3   4]
View: [100   2   3   4]
```

**Exercise 2 – Verify a Copy**

**Task:** Change a copied array and check whether the original changes.

```python
import numpy as np

arr = np.array([1, 2, 3, 4])

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

**Exercise 3 – Array Slicing**

**Task:** Extract the elements from index 2 to index 6, excluding index 6.

```python
import numpy as np

arr = np.arange(1, 11)

print(arr[2:6])
```

**Output**

```text
[3 4 5 6]
```

**Exercise 4 – Reverse an Array**

**Task:** Reverse the given array using slicing.

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])

print(arr[::-1])
```

**Output**

```text
[50 40 30 20 10]
```

**Exercise 5 – Safe Slice Copy**

**Task:** Modify a slice without changing the original array.

```python
import numpy as np

arr = np.array([10, 20, 30, 40, 50])

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

- **Data Preprocessing:** Selecting portions of datasets.
- **Memory Optimization:** Using views to avoid unnecessary data duplication.
- **Feature Preparation:** Extracting selected columns or array sections.
- **Safe Data Manipulation:** Using copies to avoid accidental changes.
- **Model Training:** Preparing arrays for training and testing.
- **Numerical Computing:** Efficiently processing large arrays.
