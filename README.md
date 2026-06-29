# TRCS102-Daily-Report
DAY1 Of TRAINING 
🐍 Day 1: Python Basics – Variables & Data Types

📖 Overview

This repository contains the concepts and practice programs covered on Day 1 of Industrial Training for AI & Machine Learning. It introduces Python fundamentals such as variables, data types, memory references, mutability, type casting, and coding exercises.

⸻

🎯 Learning Objectives

By the end of this session, you will learn:

* Variables and Python’s memory reference model
* Built-in data types
* Mutable vs Immutable objects
* Type casting (Implicit & Explicit)
* Variable naming conventions (PEP 8)
* Basic Python programming through assignments and exercises

⸻

📚 Topics Covered

1. Variables

A variable is a reference (name) that points to an object stored in memory.

Example

x = 42
print(x)
print(type(x))
print(id(x))

Key Points

* Variables store references, not values.
* type() returns the object’s data type.
* id() returns the memory address.

⸻

2. Sharing References

Assigning one variable to another creates another reference to the same object.

x = 42
y = x
print(id(x))
print(id(y))
print(x is y)

Output

True

⸻

3. Dynamic Typing

Python automatically determines the data type.

value = 100
print(type(value))
value = "Hello"
print(type(value))

⸻

4. Built-in Data Types

Numeric Types

* int
* float
* complex

a = 10
b = 3.14
c = 2 + 3j

⸻

String

text = "Hello World"

Strings are enclosed in single, double, or triple quotes.

⸻

Boolean

True
False

⸻

None

value = None

Represents the absence of a value.

⸻

5. Collection Data Types

List

* Ordered
* Mutable
* Allows duplicates

fruits = ["Apple", "Banana", "Apple"]

⸻

Tuple

* Ordered
* Immutable
* Allows duplicates

fruits = ("Apple", "Banana")

⸻

Dictionary

Stores data in key-value pairs.

student = {
    "name": "Alice",
    "age": 20
}

⸻

Set

* Unordered
* Mutable
* No duplicate elements

numbers = {1,2,2,3}
print(numbers)

Output

{1,2,3}

⸻

6. Mutable vs Immutable

Immutable Objects

Cannot be changed after creation.

Examples

* int
* float
* str
* tuple
* bool

Example

a = 5
a = a + 1

A new object is created.

⸻

Mutable Objects

Can be modified without creating a new object.

Examples

* list
* dict
* set

Example

numbers = [1,2,3]
numbers.append(4)

Memory address remains the same.

⸻

Copying Lists

Instead of

list_b = list_a

Use

list_b = list_a.copy()

to avoid changing the original list.

⸻

7. Type Casting

Implicit Type Casting

Python converts automatically.

10 + 5.5

Output

15.5

⸻

Explicit Type Casting

int("123")
float("10")
str(100)
list(tuple_data)
tuple(list_data)
set(list_data)

⸻

8. Variable Naming Rules

Rules

* Start with a letter or _
* Cannot start with numbers
* Only letters, numbers and _
* Case-sensitive
* Cannot use keywords

⸻

Best Practices (PEP 8)

Variables

student_name
learning_rate

Classes

Student
NeuralNetwork

Constants

PI
MAX_EPOCHS

Always use meaningful names.

⸻

📝 Assignment

Student Result Card

name = input("Enter Student Name: ")
marks = float(input("Enter Marks: "))
if marks >= 33:
    status = "Pass"
else:
    status = "Fail"
print("="*30)
print("RESULT CARD")
print("="*30)
print("Student Name :", name)
print("Marks :", marks)
print("Status :", status)
print("="*30)

⸻

💻 Coding Exercises

Exercise 1 – Identity vs Equality

a = [1,2,3]
b = a
c = [1,2,3]
print(a is b)
print(a == c)
print(a is c)

Output

True
True
False

Explanation

* is compares memory addresses.
* == compares values.

⸻

Exercise 2 – Modify Tuple

fruits = ("apple","pear","cherry")
temp = list(fruits)
temp[1] = "banana"
fruits = tuple(temp)
print(fruits)

Output

('apple', 'banana', 'cherry')

⸻

Exercise 3 – AI Hyperparameters Dictionary

hyperparameters = {
    "learning_rate":0.001,
    "batch_size":32,
    "optimizer":"Adam",
    "epochs":10,
    "early_stopping":True
}
print(hyperparameters["learning_rate"])
print(hyperparameters["batch_size"])
print(hyperparameters["optimizer"])
print(hyperparameters["epochs"])
print(hyperparameters["early_stopping"])
hyperparameters["learning_rate"] = 0.005
print(hyperparameters)

⸻

Exercise 4 – Set Magic

roles = [
    "admin",
    "user",
    "user",
    "editor",
    "admin",
    "user",
    "viewer"
]
print("Total Accounts:", len(roles))
unique_roles = set(roles)
print("Unique Roles:", unique_roles)
print("Unique Role Count:", len(unique_roles))

⸻

📌 Key Concepts Learned

* Variables and Memory References
* Sharing References
* Dynamic Typing
* Numeric Data Types
* Strings
* Boolean
* None
* Lists
* Tuples
* Dictionaries
* Sets
* Mutable vs Immutable Objects
* Copying Mutable Objects
* Type Casting
* Variable Naming Rules
* Result Card Program
* Identity vs Equality
* Dictionary Operations
* Removing Duplicates Using Sets

⸻

🛠 Technologies Used

* Python 3

⸻

📂 Repository Structure

Day1-Python-Basics/
│── README.md
│── assignment.py
│── exercise1.py
│── exercise2.py
│── exercise3.py
│── exercise4.py

⸻

✅ Conclusion

This project covers the complete fundamentals of Python required before moving to advanced topics like NumPy, Pandas, Machine Learning, and Deep Learning. It provides a strong understanding of variables, memory management, data types, mutability, type conversion, and Python coding practices.

⭐ Day 1 Completed – Python Basics: Variables & Data Types