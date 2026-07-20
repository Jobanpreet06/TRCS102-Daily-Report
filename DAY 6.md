## DAY 6 OF TRAINING

**NumPy Operations for AI & Machine Learning**

Day 6 focused on **NumPy (Numerical Python)**, one of the most important libraries in AI, Machine Learning, and Data Science. The session covered NumPy arrays, vectorized operations, indexing and slicing, data filtering, statistical analysis, reshaping, matrix multiplication, and practical exercises related to data preprocessing.

**Learning Objectives:-**

- Understand NumPy Arrays
- Learn Vectorized Operations
- Perform Indexing & Slicing
- Clean Data using Boolean Masking and `np.where()`
- Calculate Statistical Summaries
- Apply Broadcasting for Feature Scaling
- Reshape and Flatten Arrays
- Perform Matrix Multiplication
- Solve Data Preprocessing Exercises

## 1. Introduction to NumPy

**NumPy (Numerical Python)** is a powerful Python library used for numerical computations and handling multidimensional arrays efficiently.

**Why NumPy?**

- Faster than Python Lists
- Memory Efficient
- Supports Vectorized Operations
- Widely used in AI & Machine Learning
- Simplifies Mathematical Computations

```python
import numpy as np

arr = np.array([10, 20, 30, 40])

print(arr)
```

**Output**

```text
[10 20 30 40]
```

## 2. Vectorized Operations

Vectorization allows mathematical operations on entire arrays without using loops.

**Example**

```python
import numpy as np

numbers = np.array([1,2,3,4,5])

print(numbers + 10)
print(numbers * 2)
```

**Output**

```text
[11 12 13 14 15]

[ 2  4  6  8 10]
```

**Performance Comparison**

NumPy operations are significantly faster than traditional Python loops.

```text
Python Loop Time: 2.22 seconds

NumPy Vector Time: 0.045 seconds

**NumPy is approximately 49x faster**
```

NumPy performs operations internally using optimized C implementations, making it ideal for large datasets. :contentReference[oaicite:0]{index=0}

## 3. Indexing & Slicing

Datasets in Machine Learning are often represented as matrices.

- Rows → Data Samples
- Columns → Features

```python
import numpy as np

dataset = np.array([
    [25,50,710],
    [47,85,690],
    [31,62,780],
    [19,22,620]
])
```

**Access Single Element**

```python
print(dataset[1,1])
```

**Output**

```text
85
```

**Access Entire Row**

```python
print(dataset[2,:])
```

**Output**

```text
[31 62 780]
```

**Access Entire Column**

```python
print(dataset[:,2])
```

**Output**

```text
[710 690 780 620]
```

**Feature and Label Split**

```python
X = dataset[:,0:2]

y = dataset[:,2]

print(X)

print(y)
```

**Output**

```text
[[25 50]
 [47 85]
 [31 62]
 [19 22]]

[710 690 780 620]
```

This technique is commonly used when preparing data for machine learning models. :contentReference[oaicite:1]{index=1}

**Boolean Indexing**

```python
temp = np.array([20,30,10,25,15,28,3])

cold_days = temp[temp < 20]

hot_days = temp[temp > 25]

print(cold_days)

print(hot_days)
```

**Output**

```text
[10 15 3]

[30 28]
```

## 4. Data Filtering & Cleaning

Real-world datasets often contain missing or incorrect values.

**Using np.where()**

```python
salaries = np.array([45000,-999,52000,61000,-999,48000])

fixed = np.where(salaries < 0,10000,salaries)

print(fixed)
```

**Output**

```text
[45000 10000 52000 61000 10000 48000]
```

**Fixing Invalid Age Values**

```python
age = np.array([10,-25,67,120,-35,200])

fixed = np.where(age < 0,-age,age)

agefinal = np.where(fixed > 100,100,fixed)

print(agefinal)
```

**Output**

```text
[10 25 67 100 35 100]
```

**Boolean Masking**

```python
salaries = np.array([45000,-999,52000,61000,-999,48000])

is_invalid = salaries == -999

print(is_invalid)
```

**Output**

```text
[False True False False True False]
```

Boolean masking helps identify invalid entries efficiently. :contentReference[oaicite:2]{index=2}

## 5. Statistical Summaries & Broadcasting

NumPy provides statistical functions for data analysis.

**Mean**

```python
x = np.array([10,40,20,30,40])

print(np.mean(x))
```

**Output**

```text
28.0
```

**Median**

```python
print(np.median(x))
```

**Output**

```text
30.0
```

**Column-wise and Row-wise Mean**

```python
X = np.array([
    [10.0,200.0],
    [30.0,100.0],
    [20.0,300.0]
])

col_means = np.mean(X,axis=0)

row_means = np.mean(X,axis=1)

print(col_means)

print(row_means)
```

**Output**

```text
[20. 200.]

[105. 65. 160.]
```

**Broadcasting**

Broadcasting allows arithmetic operations between arrays of different shapes.

**Feature Standardization**

Formula:

```text
X_normalized = (X - Mean) / Standard Deviation
```

```python
mean = np.mean(X,axis=0)

std = np.std(X,axis=0)

normal = (X - mean)/std

print(normal)
```

**Output**

```text
[[-1.22474487 -1.22474487]
 [ 0.          0.        ]
 [ 1.22474487  1.22474487]]
```

Feature scaling is an important preprocessing step in Machine Learning. :contentReference[oaicite:3]{index=3}

## 6. Reshaping & Flattening

AI models often require specific data shapes.

```python
flat_arr = np.arange(6)

print(flat_arr)
```

**Output**

```text
[0 1 2 3 4 5]
```

**Reshape**

```python
matrix_2d = flat_arr.reshape(2,3)

print(matrix_2d)
```

**Output**

```text
[[0 1 2]
 [3 4 5]]
```

**Flatten**

```python
flattened = matrix_2d.flatten()

print(flattened)
```

**Output**

```text
[0 1 2 3 4 5]
```

## 7. Matrix Multiplication (Dot Product)

Matrix multiplication is heavily used in Neural Networks.

```python
inputs = np.array([1.0,2.0])

weights = np.array([
    [0.2,0.8,-0.5],
    [0.5,-0.1,0.4]
])

outputs = np.dot(inputs,weights)

print(outputs)
```

**Output**

```text
[1.2 0.6 0.3]
```

The dot product is used in neural layers to compute predictions. :contentReference[oaicite:4]{index=4}

## 8. Coding Exercises

**Exercise 1 – Celsius to Fahrenheit**

```python
celsius = np.array([0,10,25,36.6,40])

fahrenheit = (celsius * 9/5) + 32

print(fahrenheit)
```

**Output**

```text
[ 32.    50.    77.    97.88 104.  ]
```

**Exercise 2 – Feature & Label Split**

```python
X = student_data[:,0:3]

y = student_data[:,3]

print(X)

print(y)
```

**Output**

```text
[[90 18 25]
 [75 14 15]
 [95 19 30]
 [60 10 8]]

[85 62 92 45]
```

**Exercise 3 – Filter & Replace Outliers**

```python
age = np.array([25,-1,47,999,18,31,-5,62])

new = np.where((age<0) | (age>120),30,age)

print(new)
```

**Output**

```text
[25 30 47 30 18 31 30 62]
```

**Exercise 4 – Normalize Features**

```python
X = np.array([
    [10.0,100.0],
    [20.0,150.0],
    [30.0,200.0]
])

mean = np.mean(X,axis=0)

std = np.std(X,axis=0)

normalized = (X-mean)/std

print(normalized)
```

**Output**

```text
[[-1.22474487 -1.22474487]
 [ 0.          0.        ]
 [ 1.22474487  1.22474487]]
```

