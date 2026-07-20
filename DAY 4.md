## DAY 4 OF TRAINING

**Python Data Structures – Lists, Tuples, Dictionaries & Sets**

Day 4 focused on Python Data Structures, which are essential for storing, organizing, and manipulating data efficiently. The session covered Lists, Tuples, Dictionaries, and Sets along with their operations, built-in methods, and practical AI/ML applications.

**Learning Objectives:-**

- Understand Python Data Structures
- Learn Lists, Tuples, Dictionaries & Sets
- Perform common operations on each data structure
- Use built-in methods effectively
- Apply data structures in AI/ML examples
- Solve practical coding exercises

## 1. Python Data Structures

Python provides built-in data structures for storing collections of data.

| Data Structure | Ordered | Mutable | Duplicates |
|----------------|---------|---------|------------|
| List | ✅	 | ✅ | ✅ | 
| Tuple | ✅ | ❌ | ✅ |
| Dictionary | ✅* | ✅ | Keys Unique |
| Set | ❌ | ✅ | ❌ |

## 2. Lists

A List is an ordered and mutable collection that allows duplicate values.

**Creating a List**

    fruits = ["Apple", "Banana", "Mango"]
    print(fruits)

**Accessing Elements**

    print(fruits[0])
    print(fruits[-1])

**List Slicing**

    numbers = [10,20,30,40,50]
    print(numbers[1:4])
    print(numbers[:3])
    print(numbers[::2])

**Common List Methods**

| Method | Purpose |
|--------|----------|
| append() | Add element at end |
| insert() | Insert at specific position |
| extend() | Add multiple elements |
| remove() | Remove by value |
| pop() | Remove by index |
| clear() | Remove all elements |
| sort() | Sort list |
| reverse() | Reverse list |
| copy() | Create copy |

Example

    numbers = [5,2,8]
    numbers.append(10)
    numbers.sort()
    print(numbers)

**Output**

[2,5,8,10]

## 3. Tuples

A Tuple is an ordered but immutable collection.

    colors = ("Red","Green","Blue")
    print(colors[1])

**Tuple Packing**

    student = ("John",20,"BTech")

**Tuple Unpacking**

    name,age,course = student
    print(name)
    print(age)
    print(course)

**Tuple Methods**

| Method | Purpose |
|--------|----------|
| count() | Count occurrences |
| index() | Return index |

Example

    numbers = (1,2,2,3)
    print(numbers.count(2))
    print(numbers.index(3))

## 4. Dictionaries

A Dictionary stores data in key-value pairs.

    student = {
    "name":"Alice",
    "Age":20,
    "Course":"AI"
    }

**Accessing Values**

    print(student["name"])
    print(student.get("Age"))

**Adding & Updating**

    student["Age"] = 21
    student["City"] = "Delhi"

**Removing Items**

    student.pop("City")

**Dictionary Methods**

| Method | Purpose |
|--------|----------|
| keys() | Returns all keys |
| values() | Returns all values |
| items() | Returns key-value pairs |
| get() | Returns value safely |
| update() | Update dictionary |
| pop() | Remove key |

**Iterating Dictionary**

    for key,value in student.items():
    print(key,value)

## 5. Sets

A Set is an unordered collection of unique elements.

    numbers = {1,2,2,3,4}
    print(numbers)

**Output**

{1,2,3,4}

**Set Operations**

    A = {1,2,3}
    B = {3,4,5}

**Union**

    print(A | B)

**Intersection**

    print(A & B)

**Difference**

    print(A - B)

**Symmetric Difference**

    print(A ^ B)

**Set Methods**

| Method | Purpose |
|--------|----------|
| add() | Add element |
| remove() | Remove element |
| discard() | Remove safely |
| clear() | Empty set |
| union() | Combine sets |
| intersection() | Common elements |
| difference() | Difference between sets |

## AI/ML Applications

- Lists → Store datasets and predictions.
- Tuples → Store fixed records.
- Dictionaries → Feature mappings and model parameters.
- Sets → Remove duplicate values and unique labels.

**Practice Example**

    marks = [80,92,75,60]
    average = sum(marks)/len(marks)
    print("Average =",average)

**Exercise 1 – List Operations**

    numbers=[10,20,30]
    numbers.append(40)
    numbers.remove(20)
    print(numbers)

**Output**

[10,30,40]

**Exercise 2 – Tuple Unpacking**

    student=("Rahul",19,"BCA")
    name,age,course=student
    print(name)
    print(age)
    print(course)

**Exercise 3 – Dictionary Update**

    employee={
    "name":"Amit",
    "salary":40000
    }
    employee["salary"]=50000
    employee["department"]="IT"
    print(employee)

**Exercise 4 – Set Operations**

    A={1,2,3,4}
    B={3,4,5}
    print(A|B)
    print(A&B)
    print(A-B)

