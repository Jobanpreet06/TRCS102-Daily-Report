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

**Python Operators, Control Flow & Loops**

Day 2 focused on understanding Python Operators, Decision Making, and Loops, which are essential for writing logical programs. The session covered different types of operators, conditional statements, looping constructs, loop control statements, and practical programming exercises like ATM Simulator and Shopping Cart.


**Learning Objectives:-**

- Understand Python Operators and Expressions
- Perform Arithmetic, Comparison, Logical, Assignment, Bitwise, Membership & Identity operations
- Use Conditional Statements (if, elif, else)
- Learn for and while loops
- Use Loop Control Statements (break, continue, pass)
- Understand range(), enumerate(), and zip()
- Build simple real-world applications using loops and conditions

## 1. Python Operators

Operators are special symbols used to perform operations on variables and values.

**Types of Python Operators**

| Operator Type | Purpose | Operators | Example |
|---------------|---------|-----------|---------|
| Arithmetic Operators | Perform mathematical calculations | `+`, `-`, `*`, `/`, `//`, `%`, `**` | `10 + 5 = 15`, `10 % 3 = 1`, `2 ** 3 = 8` |
| Comparison Operators | Compare two values and return `True` or `False` | `==`, `!=`, `>`, `<`, `>=`, `<=` | `10 > 5` → `True`<br>`10 == 5` → `False` |
| Logical Operators | Combine multiple conditions | `and`, `or`, `not` | `(10 > 5 and 8 > 3)` → `True`<br>`not True` → `False` |
| Assignment Operators | Assign or update variable values | `=`, `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=` | `x = 5`<br>`x += 3` → `8` |
| Bitwise Operators | Perform operations on binary values | `&`, `|`, `^`, `~`, `<<`, `>>` | `5 & 3 = 1`<br>`5 \| 3 = 7`<br>`5 << 1 = 10` |
| Membership Operators | Check whether a value exists in a sequence | `in`, `not in` | `"apple" in ["apple","banana"]` → `True` |
| Identity Operators | Check whether two variables refer to the same object | `is`, `is not` | `a=[1,2]`<br>`b=a`<br>`a is b` → `True` |

**Exercise 1 – Operators & Expressions**

*Problem*

Write a program to check:

- Number is positive and even.
- Number is divisible by 5 or 3.
- Print both results.

*Solution*

    number = 30
    is_pos_even = number > 0 and number % 2 == 0
    is_div = number % 5 == 0 or number % 3 == 0
    print(is_pos_even)
    print(is_div)

**Additional Practice Programs**

*Check Prime Number*

    n = int(input("Enter a number: "))
    for i in range(2, n):
    if n % i == 0:
        print("Not Prime")
        break
    else:
    print("Prime")

*Greatest of Three Numbers*

    a = int(input())
    b = int(input())
    c = int(input())
    if a>b and a>c:
    print("a is greatest")
    elif b>a and b>c:
    print("b is greatest")
    else:
    print("c is greatest")

*Odd and Even using Bitwise Operators*

    def is_even(num):
    return (num & 1) == 0
    def is_odd(num):
    return (num & 1) == 1
    print(is_even(4))
    print(is_odd(7))

**Output**

True

True

## 2. Python Loops

Loops allow a block of code to execute repeatedly until a condition becomes false or all elements of a sequence are processed.

Python provides two looping statements:

- for loop
- while loop

## 2.1 The for Loop

The for loop is used to iterate over a sequence such as a list, tuple, string, dictionary, or a range of numbers.

range() Function

range(start, stop, step)

- start (optional) – Defaults to 0
- stop (required) – Stops before this value
- step (optional) – Increment/Decrement value

Example

    for i in range(0,11):
    print(i)

**Output**

0

1

2

3

4

5

6

7

8

9

10

**Multiplication Table**

    n = int(input("Enter any number: "))
    for i in range(11):
    print(f"{n} x {i} = {n*i}")

**Iterating Through a List**

    numbers = [10,20,30,40]
    for num in numbers:
    print(num)

**Example with Strings**

    languages = ["Python","SQL","C++"]
    for lang in languages:
    print(f"I am learning {lang} having {len(lang)} characters")

**Output**

I am learning Python having 6 characters

I am learning SQL having 3 characters

I am learning C++ having 3 characters

**Reverse Counting**

    for i in range(10,0,-2):
    print(i,end=" ")

**Output**

10 8 6 4 2

**Password Strength Checker**

    passwords=["abc123","abc","abcdfe","12"]
    for password in passwords:
    if len(password)>=6:
        print(password,"is a Strong Password")
    else:
        print(password,"is a Weak Password")

## 2.2 The while Loop

The while loop executes as long as the condition remains True.

Always update the loop variable to avoid an infinite loop.

Example

    count=1
    while count<=3:
    print(count)
    count+=1

**Output**

1

2

3

## 2.3 Loop Control Statements

These statements change the normal execution of loops.

**break**

Stops the loop immediately.

Example

    for num in range(1,10):
    if num==5:
        print("Found 5!")
        break
    print(num)

**Output**

1

2

3

4

Found 5!

**continue**

Skips the current iteration and moves to the next.

    for num in range(1,10):
    if num==5:
        continue
    print(num)

**Output**

1

2

3

4

6

7

8

9

**pass**

Acts as a placeholder when no action is required.

    for num in range(1,6):
    if num==3:
        pass
    else:
        print(num)

**Output**

1

2

4

5

## 2.4 Loop else

The else block executes only if the loop finishes normally (without break).

Example

    fruits=["apple","banana","cherry"]
    target="orange"
    for fruit in fruits:
    if fruit==target:
        print("Found")
        break
    else:
    print("Not Found")

**Output**

Not Found

## 2.5 enumerate()

Returns both index and value.

    fruits=["apple","banana","cherry"]
    for index,fruit in enumerate(fruits):
    print(index,fruit)

**Output**

0 apple

1 banana

2 cherry

##!2.6 zip()

Combines multiple iterables.

    fruits=["apple","banana","cherry"]
    prices=[120,40,150]
    for fruit,price in zip(fruits,prices):
    print(f"{fruit} costs ₹{price}")

**Login Attempt Example**

    correct_password="abc123"
    for i in range(5):
    password=input("Enter Password: ")
    if password==correct_password:
        print("Login Successful")
        break
    else:
        print("Wrong Password")
    else:
    print("Try again after 30 minutes")

**Exercise 2 – Password Validation**

*Problem*

Find the first password whose length is at least 6 characters.

*Solution*

    passwords=["abc","12345","securepwd123","short"]
    for password in passwords:
    if len(password)>=6:
        print("Password Found:",password)
        break

**Output**

Password Found: securepwd123

## 3. Control Flow Statements

Control flow allows a program to make decisions using conditional statements.

Python uses

- if
- elif
- else

**Syntax**

if condition:
    ...
elif condition:
    ...
else:
    ...

*^Exercise 3 – Age Classification**

    age=25
    if age<13:
    print("Child")
    elif age<=19:
    print("Teenager")
    elif age<=59:
    print("Adult")
    else:
    print("Senior")

**Print Even Numbers (0–20)**

    for i in range(21):
    if i%2==0:
        print(i)

**Practical Question 1 – ATM Simulator**

Create an ATM Menu using a while loop.

Features

- Check Balance
- Deposit Money
- Withdraw Money
- Exit

*Solution*

    balance=10000
    while True:
    print("\n1. Check Balance")
    print("2. Deposit")
    print("3. Withdraw")
    print("4. Exit")
    choice=int(input("Enter Choice: "))
    if choice==1:
        print("Balance:",balance)
    elif choice==2:
        amount=int(input("Enter Deposit Amount: "))
        balance+=amount
    elif choice==3:
        amount=int(input("Enter Withdraw Amount: "))
        if amount<=balance:
            balance-=amount
        else:
            print("Insufficient Balance")
    elif choice==4:
        print("Thank You!")
        break
    else:
        print("Invalid Choice")

**Practical Question 2 – Shopping Cart**

Menu

- Add Item
- Show Total
- Checkout
- Exit

*Solution*

    total=0
    item_count=0
    while True:
    print("\n1.Add Item")
    print("2.Show Total")
    print("3.Checkout")
    print("4.Exit")
    choice=input("Enter Choice: ")
    if choice=="1":
        item=input("Item Name: ")
        price=float(input("Price: "))
        quantity=int(input("Quantity: "))
        total+=price*quantity
        item_count+=1
    elif choice=="2":
        print("Items:",item_count)
        print("Total:",total)
    elif choice=="3":
        if item_count==0:
            print("Cart is Empty")
        else:
            print("Bill:",total)
            payment=input("Pay? (yes/no): ")
            if payment.lower()=="yes":
                print("Payment Successful")
                total=0
                item_count=0
            else:
                print("Payment Cancelled")
    elif choice=="4":
        print("Goodbye!")
        break
    else:
        print("Invalid Choice")

## DAY 3 OF TRAINING

**Python Functions, Arguments, Scope & Recursion**

Day 3 covered the fundamentals of **Python Functions**, including creating and calling functions, passing arguments, returning values, variable scope, recursion, and solving practical programming problems.

**Learning Objectives:-**

- Understand Python Functions
- Create and call functions
- Work with Parameters & Arguments
- Use the `return` statement
- Learn Positional, Keyword & Default Arguments
- Understand `*args` and `**kwargs`
- Learn Local & Global Scope
- Use Recursive Functions
- Solve practical coding exercises

Great! We’ll do it exactly like Day 1 and Day 2. Here’s Part 1 of the GitHub README.

## 1. Functions

A function is a reusable block of code that performs a specific task. Instead of writing the same code repeatedly, we define it once and call it whenever needed.

Advantages

- Code Reusability
- Better Readability
- Easy Maintenance
- Modular Programming
- Reduces Repetition

**Function Syntax**

    def function_name(parameters):
    # Function Body
    statements

Example

    def greet():
    print("Hello World!")
    greet()

**Output**

Hello World!

## 2. Creating & Calling Functions

Functions execute only when they are called.

Example

    def welcome_student():
    print("Welcome to AI/ML Industrial Training!")
    print("Let's build some functions today!")
    welcome_student()

**Output**

Welcome to AI/ML Industrial Training!
Let's build some functions today!

## 3. Parameters and Arguments

Functions become more useful when data is passed into them.

| Term | Meaning |
|------|---------|
| Parameter	| Variable defined inside the function |
| Argument | Actual value passed while calling the function |

Example

    def greet_user(username, course):
    print(f"Hello {username}! Welcome to {course}")
    greet_user("Amit", "BTech")
    greet_user("Priya", "BCA")

**Output**

Hello Amit! Welcome to BTech

Hello Priya! Welcome to BCA

**Calculator Function**

    def calculate(a, b, operator):
    if operator=="+":
        print(a+b)
    elif operator=="-":
        print(a-b)
    elif operator=="*":
        print(a*b)
    elif operator=="/":
        print(a/b)
    calculate(20,30,"+")

**Output**

50

**Multiplication Table Function**

    def table(num):
    for i in range(11):
        print(f"{num} x {i} = {num*i}")
    table(5)

**Output**

5 x 0 = 0

...

5 x 10 = 50

**Exercise 1 – Create an Add Function**

*Problem*

Create a function named add_numbers that

- Takes two parameters
- Calculates their sum
- Prints the result

*Solution*

    def add_numbers(num1, num2):
    result = num1 + num2
    print("Sum inside function:", result)
    add_numbers(15,25)

**Output**

Sum inside function: 40

## 4. Return Statement

The return statement sends a value back to the caller so it can be stored and reused.

- Note: Once return executes, the function immediately stops.

Example

    def calculate_square(number):
    square = number * number
    return square
    result = calculate_square(5)
    print(result)

**Output**

25

**Using Returned Value**

    adjusted_score = result + 10
    print(adjusted_score)

**Output**

35

**Exercise 2 – Prime Number Function**

*Problem*

Create a function is_prime(n) that

- Returns True if number is prime
- Returns False otherwise

*Solution*

    def is_prime(n):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5)+1):
        if n%i==0:
            return False
    return True
    result = is_prime(11)
    print(result)

**Output**

True

**Another Output**

Is 11 prime?: True

## 5. Types of Arguments

Python provides different ways of passing arguments to functions.

| Argument Type | Description | Example |
|----------------|-------------|----------|
| Positional Arguments | Arguments are assigned based on their order. | intro("Sahil",17,"11th") |
| Keyword Arguments | Arguments are passed using parameter names, so order doesn’t matter. | intro(name="Sakshi", age=15, course="9th") |
| Default Arguments | A parameter has a predefined value if no argument is passed. | intro("Priya") |

**5.1 Positional Arguments**

Arguments are assigned according to their position.

    def intro(name, age=18, course="12th"):
    print(f"{name} is {age} years old and studies in {course}")
    intro("Sahil",17,"11th")

**Output**

Sahil is 17 years old and studies in 11th

**5.2 Default Arguments**

If no value is passed, Python uses the default value.

    intro("Priya")

**Output**

Priya is 18 years old and studies in 12th

**5.3 Keyword Arguments**

Arguments are passed using parameter names.

    intro(course="9th", name="Sakshi", age=15)

**Output**

Sakshi is 15 years old and studies in 9th

## 6. Variable-Length Arguments (*args & **kwargs)

Sometimes we don’t know how many arguments a function will receive.

Python provides:

| Symbol | Description	| Stores Data As |
|--------|--------------|----------------|
| *args | Collects multiple positional arguments	| Tuple |
| **kwargs | Collects multiple keyword arguments | Dictionary |

**6.1 Dictionary .items()**

Used to access both keys and values.

    dict1 = {
    "Name":"Swastik",
    "Class":"BTech"
    }
    for key,value in dict1.items():
    print(key,value)

**Output**

Name Swastik

Class BTech

6.2 Example of *args.

    def calculate_total_expenses(*expenses):
    print(f"Expenses received: {expenses}")
    return sum(expenses)
    total = calculate_total_expenses(12.5,45.0,100.25,7.8)
    print(total)

**Output**

Expenses received: (12.5, 45.0, 100.25, 7.8)

165.55

6.3 Example of **kwargs

    def print_model_parameters(**hyperparams):
    for key,value in hyperparams.items():
        print(f"{key}: {value}")
    print_model_parameters(
    learning_rate=0.001,
    batch_size=64,
    dropout=0.3
    )

**Output**

learning_rate : 0.001

batch_size : 64

dropout : 0.3

## 7. Variable Scope

Variable scope determines where a variable can be accessed.

| Scope	| Description |
|-------|-------------|
| Global Scope | Variable declared outside any function. |
| Local Scope | Variable declared inside a function. |


Example

    metric_name = "Accuracy"
    def evaluate():
    score = 0.95
    print(f"{metric_name} score is {score}")
    evaluate()
    print(metric_name)

**Output**

Accuracy score is 0.95

Accuracy

Trying to print score outside the function results in a NameError, because it is a local variable.

## 8. The global Keyword

Used to modify a global variable inside a function.

    a = 10
    def change():
    global a
    a = 20
    print("After changing:",a)
    change()
    print("Original:",a)

**Output**

After changing: 20

Original: 20

**Another Example**

    epoch_counter = 5
    def run_epoch():
    global epoch_counter
    epoch_counter += 1
    print(epoch_counter)
    run_epoch()

**Output**

6

## 9. Recursive Functions

A recursive function is a function that calls itself.

Every recursive function has two parts:

- Base Case → Stops recursion.
- Recursive Case → Calls itself with a smaller problem.

**Factorial using Recursion**

Formula

n! = n × (n−1)!

0! = 1

1! = 1

Program

    def calculate_factorial(n):
    if n==0 or n==1:
        return 1
    return n*calculate_factorial(n-1)
    print(calculate_factorial(5))

**Output**

120

**Exercise 3 – Recursive Fibonacci Sequence**

*Problem*

Write a recursive function fibonacci(n) that returns the nth Fibonacci number.

Formula

fib(0)=0

fib(1)=1

fib(n)=fib(n−1)+fib(n−2)

*Solution*

    def fibonacci(n):
    if n==0 or n==1:
        return n
    return fibonacci(n-1)+fibonacci(n-2)
    print(fibonacci(6))

**Output**

8

**Testing**

print(f"Fibonacci(6) = {fibonacci(6)}")

**Output**

Fibonacci(6) = 8

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

## DAY 5 OF TRAINING

**Python Strings, List Comprehensions & Nested Data Structures**

Day 5 focused on Python Strings and Advanced Data Structures, including string manipulation, formatting, list comprehensions, nested data structures, and their practical applications in AI/ML. The session also included multiple real-world exercises and complete solutions for data preprocessing and analysis.

**Learning Objectives:-**

- Understand Python Strings
- Perform String Indexing & Slicing
- Learn Common String Methods
- Use String Formatting Techniques
- Understand List Comprehensions
- Work with Nested Data Structures
- Solve AI/ML-based Programming Exercises

## 1. Strings

A String is an immutable sequence of characters enclosed in single, double, or triple quotes.

Example

    text = "Artificial Intelligence"
    print(text)

**Accessing Characters**

    text = "Python"
    print(text[0])
    print(text[-1])

**Output**

P

n

**String Slicing**

    text = "Machine Learning"
    print(text[:7])
    print(text[8:])
    print(text[::-1])

**Output**

Machine

Learning

gninraeL enihcaM

## 2. Common String Methods

| Method | Purpose | Example |
|--------|----------|---------|
| lower() | Convert to lowercase | "AI".lower() |
| upper()	| Convert to uppercase |	"python".upper() |
| title()	| Capitalize each word | "machine learning".title() |
| strip()	| Remove extra spaces | " AI ".strip() |
| replace()	| Replace text |	"cat".replace("c","b") |
| split()	| Convert string to list | "a b".split() |
| join()	| Join list into string | " ".join(words) |
| find()	| Find index of substring | "python".find("th") |

Example

    sentence = " python programming "
    print(sentence.strip())
    print(sentence.upper())
    print(sentence.replace("python","AI"))

**Output**

python programming

PYTHON PROGRAMMING

AI programming

## 3. String Formatting

Python provides different ways to format strings.

**Using f-Strings**

    name = "Alice"
    age = 20
    print(f"{name} is {age} years old.")

**Output**

Alice is 20 years old.

**Using .format()**

    print("{} scored {} marks".format("Rahul",95))

## 4. List Comprehensions

List comprehensions provide a concise way to create lists.

**Syntax**

[expression for item in iterable if condition]

Example

    numbers = [1,2,3,4,5]
    squares = [x*x for x in numbers]
    print(squares)

**Output**

[1,4,9,16,25]

**Example with Condition**

    even = [x for x in range(11) if x%2==0]
    print(even)

**Output**

[0,2,4,6,8,10]

Example (Removing Invalid Values)

    predictions = [0.15,-99.0,0.82,1.45,-99.0,0.67]
    cleaned = [x for x in predictions if x!=-99.0]
    print(cleaned)

**Output**

[0.15,0.82,1.45,0.67]

## 5. Nested Data Structures

Python allows one data structure to be stored inside another.

Examples

- List of Lists
- Dictionary of Lists
- List of Dictionaries
- Tuple of Lists

Example

    students = [
    {"name":"Alice","marks":90},
    {"name":"Bob","marks":85}
    ]
    print(students[0]["name"])

**Output**

Alice

Example

    matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
    ]
    print(matrix[1][2])

**Output**

6

## AI/ML Applications

- Strings → Text preprocessing
- List Comprehensions → Data cleaning
- Dictionaries → Feature mappings
- Nested Lists → Dataset representation
- Nested Dictionaries → JSON data

**Exercise 1 – Outlier/Noise Filter**

Remove invalid values (-99.0) from prediction data.

    predictions=[0.15,-99.0,0.82,1.45,-99.0,0.67,2.1]
    cleaned=[x for x in predictions if x!=-99.0 and x>0]
    print(cleaned)

**Output**

[0.15,0.82,1.45,0.67,2.1]

**Exercise 2 – Dataset Split Unpacker**

    train,val,test=dataset_splits
    X_train,y_train=train
    X_val,y_val=val
    X_test,y_test=test

**Exercise 3 – Safe Vocabulary Word Indexer**

    def text_to_indices(text,vocab):
    words=text.lower().split()
    return [vocab.get(word,0) for word in words]

**Exercise 4 – Clean & Overlap Checker**

    train={"tumor","healthy","cyst"}
    test={"tumor","healthy","fibroid"}
    print(test-train)

**Output**

{'fibroid'}

**Exercise 5 – Evaluation Metrics**

    actual=[1,0,1,1,0]
    predicted=[1,0,0,1,1]
    tp=tn=fp=fn=0
    for a,p in zip(actual,predicted):
    if a==1 and p==1:
        tp+=1
    elif a==0 and p==0:
        tn+=1
    elif a==0 and p==1:
        fp+=1
    else:
        fn+=1
    print({"TP":tp,"TN":tn,"FP":fp,"FN":fn})

**Exercise 6 – Customer Dataset Preprocessing**

    unique_records=list(set(raw_records))
    cleaned=[r for r in unique_records if r[1]>=0]
    ages=[r[0] for r in cleaned if r[2]==1]
    average_age=sum(ages)/len(ages)
    print(cleaned)
    print(len(cleaned))
    print(average_age)

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
