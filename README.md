# TRCS102-Daily-Report
## DAY1 Of TRAINING 

**Python Basics – Variables & Data Types** 

The concepts that are covered on Day 1 of Industrial Training for AI & Machine Learning are - Python fundamentals such as variables, data types, memory references, mutability, type casting, and coding exercises.

**Learning Objectives:-**

- Variables and Python’s memory reference model

- Built-in data types

- Mutable vs Immutable objects

- Type casting (Implicit & Explicit)

- Variable naming conventions (PEP 8)

- Basic Python programming through assignments and exercises

## 1. Variables

A variable is a reference (name) that points to an object stored in memory.

Example

    x = 42

    print(x)

    print(type(x))

    print(id(x))

Variables store references, not values.

type() returns the object’s data type.

id() returns the memory address.

## 2. Sharing References

Assigning one variable to another creates another reference to the same object.

    x = 42

    y = x

    print(id(x))

    print(id(y))

    print(x is y)

**Output**

True

## 3. Dynamic Typing

Python automatically determines the data type.

    value = 100

    print(type(value))

    value = "Hello"

    print(type(value))

## 4. Built-in Data Types

**Numeric Types**

int

float

complex

    a = 10

    b = 3.14

    c = 2 + 3j

**String**

    text = "Hello World"

Strings are enclosed in single, double, or triple quotes.


**Boolean**

True

False

None

    value = None

Represents the absence of a value.


## 5. Collection Data Types 

**List**

Ordered

Mutable

Allows duplicates

    fruits = ["Apple", "Banana", "Apple"]

**Tuple**

Ordered

Immutable

Allows duplicates

    fruits = ("Apple", "Banana")

**Dictionary**

Stores data in key-value pairs.

    student = {

    "name": "Alice",

    "age": 20

    }

**Set**

Unordered

Mutable

No duplicate elements

    numbers = {1,2,2,3}

    print(numbers)

Output

{1,2,3}

## 6. Mutable vs Immutable

**Immutable Objects**

Cannot be changed after creation.

Examples

int

float

str

tuple

bool

Example

    a = 5

    a = a + 1

A new object is created.

**Mutable Objects**

Can be modified without creating a new object.

Examples

list

dict

set

Example

    numbers = [1,2,3]
    numbers.append(4)

Memory address remains the same.

**Copying Lists**

Instead of

    list_b = list_a

Use

    list_b = list_a.copy()

to avoid changing the original list.


## 7. Type Casting

**Implicit Type Casting**

Python converts automatically.

10 + 5.5

Output

15.5

**Explicit Type Casting**

int("123")

float("10")

str(100)

list(tuple_data)

tuple(list_data)

set(list_data)

## 8. Variable Naming Rules

Rules

Start with a letter or _

Cannot start with numbers

Only letters, numbers and _

Case-sensitive

Cannot use keywords

**Best Practices (PEP 8)**

*Variables*

student_name

learning_rate

*Classes*

Student
NeuralNetwork

*Constants*

PI
MAX_EPOCHS

Always use meaningful names.

**Assignment** 

*Student Result Card*

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

**Coding Exercises**

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

- is compares memory addresses.

- == compares values.

**Exercise 2 – Modify Tuple**

    fruits = ("apple","pear","cherry")

    temp = list(fruits)

    temp[1] = "banana"

    fruits = tuple(temp)

    print(fruits)

Output

('apple', 'banana', 'cherry')

**Exercise 3 – AI Hyperparameters Dictionary**

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

**Exercise 4 – Set Magic**

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
 
## DAY 2 OF TRAINING

Python Operators, Control Flow & Loops

Day 2 focused on understanding Python Operators, Decision Making, and Loops, which are essential for writing logical programs. The session covered different types of operators, conditional statements, looping constructs, loop control statements, and practical programming exercises like ATM Simulator and Shopping Cart.


**Learning Objectives:-**

- Understand Python Operators and Expressions
- Perform Arithmetic, Comparison, Logical, Assignment, Bitwise, Membership & Identity operations
- Use Conditional Statements (if, elif, else)
- Learn for and while loops
- Use Loop Control Statements (break, continue, pass)
- Understand range(), enumerate(), and zip()
- Build simple real-world applications using loops and conditions

**1. Python Operators**

Operators are special symbols used to perform operations on variables and values.

## Types of Python Operators

| Operator Type | Purpose | Operators | Example |
|---------------|---------|-----------|---------|
| ➕ Arithmetic Operators | Perform mathematical calculations | `+`, `-`, `*`, `/`, `//`, `%`, `**` | `10 + 5 = 15`, `10 % 3 = 1`, `2 ** 3 = 8` |
| ⚖️ Comparison Operators | Compare two values and return `True` or `False` | `==`, `!=`, `>`, `<`, `>=`, `<=` | `10 > 5` → `True`<br>`10 == 5` → `False` |
| 🔗 Logical Operators | Combine multiple conditions | `and`, `or`, `not` | `(10 > 5 and 8 > 3)` → `True`<br>`not True` → `False` |
| 📝 Assignment Operators | Assign or update variable values | `=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=` | `x = 5`<br>`x += 3` → `8` |
| 💻 Bitwise Operators | Perform operations on binary values | `&`, `|`, `^`, `~`, `<<`, `>>` | `5 & 3 = 1`<br>`5 \| 3 = 7`<br>`5 << 1 = 10` |
| 🔍 Membership Operators | Check whether a value exists in a sequence | `in`, `not in` | `"apple" in ["apple","banana"]` → `True` |
| 🆔 Identity Operators | Check whether two variables refer to the same object | `is`, `is not` | `a=[1,2]`<br>`b=a`<br>`a is b` → `True` |

Used for mathematical calculations.

Operator	Meaning
+	Addition
-	Subtraction
*	Multiplication
/	Division
//	Floor Division
%	Modulus
**	Exponent

Example

a = 20
b = 3
print(a+b)
print(a-b)
print(a*b)
print(a/b)
print(a//b)
print(a%b)
print(a**b)

⸻

1.2 Comparison Operators

Used to compare two values.

Operator	Meaning
==	Equal
!=	Not Equal
>	Greater Than
<	Less Than
>=	Greater Than or Equal
<=	Less Than or Equal

Example

x = 10
y = 20
print(x == y)
print(x != y)
print(x < y)
print(x >= y)

Output

False
True
True
False

⸻

1.3 Logical Operators

Used to combine multiple conditions.

* and → True if both conditions are True.
* or → True if at least one condition is True.
* not → Reverses the result.

Note: Python uses Short-Circuit Evaluation for and and or.

Example

a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
c = int(input("Enter third number: "))
if a>b and a>c:
    print("a is greatest")
elif b>a and b>c:
    print("b is greatest")
else:
    print("c is greatest")

Another Example

is_sunny = True
is_weekend = False
print(is_sunny and is_weekend)
print(is_sunny or is_weekend)
print(not is_sunny)

Output

False
True
False

Bitwise NOT Example

print(~12)

Output

-13

⸻

1.4 Assignment Operators

Used to assign and update values.

Operator	Example
=	Assignment
+=	Add & Assign
-=	Subtract & Assign
*=	Multiply & Assign
/=	Divide & Assign
//=	Floor Divide
%=	Modulus
**=	Exponent

Example

num = 10
num += 5
print(num)
num *= 2
print(num)
num //= 3
print(num)

⸻

1.5 Bitwise Operators

Perform operations on binary values.

Operator	Meaning
&	AND
`	`
^	XOR
~	NOT
<<	Left Shift
>>	Right Shift

Example

n1 = 5
n2 = 3
print(n1 & n2)
print(n1 | n2)
print(n1 ^ n2)
print(1 << 3)

⸻

1.6 Membership Operators

Used to check whether a value exists in a sequence.

* in
* not in

Example

fruits = ["apple","banana","cherry"]
print("apple" in fruits)
print("kiwi" not in fruits)
print("kiwi" in fruits)

Output

True
True
False

⸻

1.7 Identity Operators

Compare memory addresses rather than values.

* is
* is not

Example

list_x = [1,2,3]
list_y = [1,2,3]
print(list_x is list_y)
print(list_x == list_y)

Output

False
True

Explanation

* is compares object identity (memory location).
* == compares object values.

⸻

Exercise 1 – Operators & Expressions

Problem

Write a program to check:

* Number is positive and even.
* Number is divisible by 5 or 3.
* Print both results.

Solution

number = 30
is_pos_even = number > 0 and number % 2 == 0
is_div = number % 5 == 0 or number % 3 == 0
print(is_pos_even)
print(is_div)

⸻

Additional Practice Programs

Check Prime Number

n = int(input("Enter a number: "))
for i in range(2, n):
    if n % i == 0:
        print("Not Prime")
        break
else:
    print("Prime")

⸻

Greatest of Three Numbers

a = int(input())
b = int(input())
c = int(input())
if a>b and a>c:
    print("a is greatest")
elif b>a and b>c:
    print("b is greatest")
else:
    print("c is greatest")

⸻

Odd and Even using Bitwise Operators

def is_even(num):
    return (num & 1) == 0
def is_odd(num):
    return (num & 1) == 1
print(is_even(4))
print(is_odd(7))

Output
