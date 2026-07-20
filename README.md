# TRCS102-Daily-Report
## DAY 1 Of TRAINING 

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

## DAY 8 OF TRAINING

**Pandas Basics – Series, DataFrames & Data Exploration**

Day 8 focused on the fundamentals of **Pandas**, a powerful Python library used for data manipulation and analysis. The session covered creating Series and DataFrames, loading datasets, exploring data, selecting rows and columns, and understanding dataset structure through various built-in functions.

**Learning Objectives:-**

- Understand Pandas and its importance
- Create Series and DataFrames
- Load datasets using `read_csv()`
- Explore datasets using built-in functions
- Select rows and columns
- Use `loc[]` and `iloc[]`
- Perform basic data analysis
- Solve practical exercises

## 1. Introduction to Pandas

**Pandas** is an open-source Python library used for data manipulation, analysis, and preprocessing. It provides fast, flexible, and easy-to-use data structures.

**Why Pandas?**

- Easy data handling
- Fast processing
- Supports CSV, Excel & SQL
- Handles missing values
- Used extensively in AI & Machine Learning

```python
import pandas as pd
```

## 2. Pandas Data Structures

Pandas mainly provides two data structures.

| Data Structure | Description |
|---------------|-------------|
| **Series** | One-dimensional labeled array |
| **DataFrame** | Two-dimensional table with rows and columns |

## 3. Pandas Series

A **Series** is a one-dimensional array capable of holding any data type.

**Example**

```python
import pandas as pd

marks = pd.Series([90,85,78,95])

print(marks)
```

**Output**

```text
0    90
1    85
2    78
3    95
dtype: int64
```

## 4. Pandas DataFrame

A **DataFrame** is a two-dimensional tabular data structure consisting of rows and columns.

**Example**

```python
student = {

    "Name":["Alice","Bob","John"],

    "Age":[20,21,19],

    "Marks":[90,80,95]

}

df = pd.DataFrame(student)

print(df)
```

## 5. Reading CSV Files

Datasets are commonly loaded using `read_csv()`.

```python
df = pd.read_csv("data.csv")

print(df.head())
```

## 6. Exploring the Dataset

**Display First Rows**

```python
df.head()
```

Displays the first **5 rows**.

**Display Last Rows**

```python
df.tail()
```

Displays the last **5 rows**.

**Dataset Information**

```python
df.info()
```

Shows:

- Number of rows
- Number of columns
- Data types
- Missing values
- Memory usage

**Statistical Summary**

```python
df.describe()
```

Displays:

- Count
- Mean
- Standard Deviation
- Minimum
- Maximum
- Quartiles

**Display Column Names**

```python
print(df.columns)
```

**Display Data Types**

```python
print(df.dtypes)
```

Example Output

```text
CustomerID      int64
Age           float64
Gender         object
Income        float64
Purchased      object
```

## 7. Selecting Data

**Selecting a Single Column**

```python
income = df["Income"]

print(income)
```

Returns a **Series**.

**Selecting Multiple Columns**

```python
features = df[["Age","Income"]]

print(features)
```

Returns a **DataFrame**.

## 8. Row Selection using `iloc[]`

`iloc[]` selects data using **index positions**.

**Example**

```python
df.iloc[1:4,1:4]
```

## 9. Row Selection using `loc[]`

`loc[]` selects data using **row labels and column names**.

**Example**

```python
df.loc[1,"Age"]
```

**Output**

```text
47
```

**Exercise 1 – Create a DataFrame**

```python
student = {

    "Name":["Rahul","Priya","Aman"],

    "Age":[20,21,19],

    "Marks":[88,92,85]

}

df = pd.DataFrame(student)

print(df)
```

**Exercise 2 – Dataset Exploration**

```python
df = pd.read_csv("students.csv")

print(df.head())

print(df.info())

print(df.describe())
```

**Exercise 3 – Column Selection**

```python
print(df["Marks"])

print(df[["Name","Marks"]])
```

**Exercise 4 – Row Selection**

```python
print(df.iloc[0:3])

print(df.loc[2])
```

## DAY 9 OF TRAINING

**Pandas Data Cleaning, Boolean Indexing & GroupBy**

Day 9 focused on **data preprocessing using Pandas**, including filtering datasets with Boolean Indexing, handling missing values, grouping data for analysis, and solving practical data-cleaning exercises commonly used in AI & Machine Learning.

**Learning Objectives:-**

- Understand Boolean Indexing
- Filter data using single and multiple conditions
- Detect Missing Values
- Handle missing data using `fillna()`
- Remove missing values using `dropna()`
- Perform GroupBy operations
- Calculate Aggregate Statistics
- Solve Data Cleaning Exercises

## 1. Boolean Indexing

Boolean Indexing is used to filter rows that satisfy a given condition.

**Example**

```python
high_income = df[df["Income"] > 60000]

print(high_income)
```

Returns all customers having income greater than **60000**.

**Multiple Conditions**

```python
filtered = df[(df["Age"] >= 25) & (df["Gender"] == "F")]

print(filtered)
```

**Using Boolean Mask**

```python
mask = df["Income"] > 60000

print(mask)

high_income = df[mask]

print(high_income)
```

## 2. Missing Values

Real-world datasets usually contain missing values that must be handled before training Machine Learning models.

**Detect Missing Values**

```python
df.isnull().sum()
```

**Example Output**

```text
CustomerID    0
Age           1
Gender        1
Income        1
Purchased     0
```

**Fill Missing Values**

Replace missing **Age** values with the column mean.

```python
mean_age = df["Age"].mean()

df["Age"] = df["Age"].fillna(mean_age)
```

Replace missing **Income** values.

```python
mean_income = df["Income"].mean()

df["Income"] = df["Income"].fillna(mean_income)
```

**Drop Missing Values**

Remove rows containing missing Gender values.

```python
df = df.dropna(subset=["Gender"])
```

**Verify Dataset**

```python
df.isnull().sum()
```

**Output**

```text
CustomerID    0
Age           0
Gender        0
Income        0
Purchased     0
```

## 3. GroupBy

`groupby()` groups similar records together for analysis.

**Average Income by Gender**

```python
df.groupby("Gender")["Income"].mean()
```

**Average Age by Gender**

```python
df.groupby("Gender")["Age"].mean()
```

**Multiple Columns**

```python
cols = ["Income","Age"]

df.groupby("Gender")[cols].mean()
```

**Output**

| Gender | Income | Age |
|---------|--------:|----:|
| F | 44666.67 | 26.27 |
| M | 69875.00 | 39.00 |

**Group by Purchased**

```python
df.groupby("Purchased")[cols].mean()
```

**Output**

| Purchased | Income | Age |
|------------|--------:|----:|
| No | 42250 | 25.0 |
| Yes | 73500 | 40.9 |

## 4. Aggregate Functions

Common aggregation functions used with GroupBy.

| Function | Purpose |
|----------|---------|
| `mean()` | Average value |
| `sum()` | Total |
| `count()` | Number of records |
| `max()` | Maximum value |
| `min()` | Minimum value |
| `std()` | Standard Deviation |

**Exercise 1 – Dataset Inspection**

```python
eval_df = pd.read_csv("student.csv")

print(eval_df.head())

print(eval_df.info())

print(eval_df.describe())
```

**Exercise 2 – Data Filtering**

Display students who passed.

```python
passed = eval_df[eval_df["Passed"]=="Yes"]

print(passed)
```

Display only selected columns.

```python
passed = eval_df[eval_df["Passed"]=="Yes"][["HoursStudied","Grade"]]

print(passed)
```

**Exercise 3 – Missing Value Handling**

```python
mean_hours = eval_df["HoursStudied"].mean()

clean_df = eval_df.copy()

clean_df["HoursStudied"] = clean_df["HoursStudied"].fillna(mean_hours)

clean_df = clean_df.dropna(subset=["Grade"])

print(clean_df)
```

**Exercise 4 – GroupBy Summary**

```python
summary = clean_df.groupby("Passed")[["HoursStudied","Grade","Attendance"]].mean()

print(summary)
```

**Output**

| Passed | HoursStudied | Grade | Attendance |
|---------|-------------:|------:|-----------:|
| No | 6.75 | 53.50 | 88.00 |
| Yes | 15.10 | 86.00 | 94.33 |

**AI/ML Applications**

- Data Cleaning
- Feature Selection
- Missing Value Treatment
- Customer Data Analysis
- Exploratory Data Analysis (EDA)
- Dataset Preprocessing
- Model Preparation

## DAY 10 OF TRAINING

**Data Visualization using Matplotlib & Seaborn**

Day 10 focused on **Data Visualization** using **Matplotlib** and **Seaborn**, two of the most widely used Python libraries for graphical data representation. The session covered different types of plots, chart customization, and visualization techniques used in Data Analysis, AI, and Machine Learning.

**Learning Objectives:-**

- Understand Data Visualization
- Learn Matplotlib Basics
- Create Line, Bar and Scatter Plots
- Customize Charts
- Understand Seaborn
- Visualize Data Effectively
- Solve Practical Visualization Exercises

## 1. Introduction to Data Visualization

**Data Visualization** is the graphical representation of data that helps identify patterns, trends, relationships, and insights easily.

**Why Data Visualization?**

- Easy to understand large datasets
- Detect trends and patterns
- Compare values visually
- Identify outliers
- Improve decision-making
- Essential in AI & Machine Learning

## 2. Introduction to Matplotlib

**Matplotlib** is a Python library used to create static, animated, and interactive graphs.

**Import Library**

```python
import matplotlib.pyplot as plt
```

**Features**

- Easy to use
- Highly customizable
- Supports multiple chart types
- Widely used in Data Science

## 3. Line Plot

A **Line Plot** is used to show trends over time or continuous data.

**Syntax**

```python
plt.plot(x, y)
plt.show()
```

**Example**

```python
import matplotlib.pyplot as plt

days = [1,2,3,4,5]

sales = [120,150,180,170,210]

plt.plot(days, sales)

plt.title("Daily Sales")

plt.xlabel("Days")

plt.ylabel("Sales")

plt.show()
```

**Output**

Displays a line graph representing daily sales.

**Customized Line Plot**

```python
plt.plot(days, sales,
         color="blue",
         marker="o",
         linestyle="--",
         linewidth=2)

plt.title("Daily Sales")

plt.grid(True)

plt.show()
```

**Common Parameters**

| Parameter | Purpose |
|-----------|---------|
| color | Changes line color |
| marker | Displays data points |
| linestyle | Changes line style |
| linewidth | Changes line thickness |
| label | Adds legend label |

## 4. Bar Plot

A **Bar Plot** compares values between different categories.

**Syntax**

```python
plt.bar(x, y)
plt.show()
```

**Example**

```python
subjects = ["Python","ML","AI","DBMS"]

marks = [92,85,88,80]

plt.bar(subjects, marks)

plt.title("Student Marks")

plt.xlabel("Subjects")

plt.ylabel("Marks")

plt.show()
```

**Output**

Displays a vertical bar chart.

**Horizontal Bar Chart**

```python
plt.barh(subjects, marks)

plt.title("Student Marks")

plt.show()
```

## 5. Scatter Plot

A **Scatter Plot** shows the relationship between two numerical variables.

**Syntax**

```python
plt.scatter(x, y)
plt.show()
```

**Example**

```python
study_hours = [1,2,3,4,5,6,7]

marks = [40,50,58,67,75,86,95]

plt.scatter(study_hours, marks)

plt.title("Study Hours vs Marks")

plt.xlabel("Study Hours")

plt.ylabel("Marks")

plt.show()
```

**Output**

Displays individual points showing the relationship between study hours and marks.

**Customized Scatter Plot**

```python
plt.scatter(study_hours,
            marks,
            color="red",
            marker="*",
            s=150)

plt.grid(True)

plt.show()
```

## 6. Multiple Plots

Different plots can be displayed in the same figure.

```python
plt.figure(figsize=(8,5))

plt.plot(days, sales)

plt.scatter(days, sales)

plt.show()
```

## 7. Adding Legend

```python
plt.plot(days, sales,
         label="Sales")

plt.legend()

plt.show()
```

## 8. Introduction to Seaborn

**Seaborn** is a Python data visualization library built on top of **Matplotlib**. It provides attractive and informative statistical graphics with minimal code.

**Import Seaborn**

```python
import seaborn as sns
import matplotlib.pyplot as plt
```

**Advantages of Seaborn**

- Beautiful default themes
- Better statistical plots
- Easy integration with Pandas
- Supports complex visualizations
- Ideal for Exploratory Data Analysis (EDA)

## 9. Histogram

A **Histogram** shows the frequency distribution of numerical data.

**Syntax**

```python
sns.histplot(data)
plt.show()
```

**Example**

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [45,52,67,72,81,90,55,61,77,84]

sns.histplot(marks, bins=5)

plt.title("Distribution of Marks")

plt.show()
```

**Output**

Displays the frequency distribution of student marks.

## 10. Box Plot

A **Box Plot** represents the spread of data and helps identify outliers.

**Example**

```python
sns.boxplot(y=marks)

plt.title("Box Plot of Marks")

plt.show()
```

**Applications**

- Detect Outliers
- Compare Distributions
- Analyze Data Spread

## 11. Heatmap

A **Heatmap** displays data values using different colors.

**Example**

```python
import numpy as np

data = np.array([
    [1,2,3],
    [4,5,6],
    [7,8,9]
])

sns.heatmap(data,
            annot=True,
            cmap="Blues")

plt.show()
```

**Output**

Displays a colored matrix with annotated values.

## 12. Plot Comparison

| Plot | Purpose |
|------|---------|
| Line Plot | Shows trends over time |
| Bar Plot | Compares categories |
| Scatter Plot | Shows relationship between variables |
| Histogram | Displays frequency distribution |
| Box Plot | Detects outliers and spread |
| Heatmap | Visualizes matrix values |

## 13. Chart Customization

Useful functions for improving visualizations.

```python
plt.title("Chart Title")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.grid(True)
plt.legend()
plt.show()
```

**Coding Exercise 1 – Line Plot**

```python
import matplotlib.pyplot as plt

months = ["Jan","Feb","Mar","Apr","May"]

sales = [120,135,150,170,190]

plt.plot(months, sales, marker="o")

plt.title("Monthly Sales")

plt.xlabel("Month")

plt.ylabel("Sales")

plt.grid(True)

plt.show()
```

**Coding Exercise 2 – Bar Chart**

```python
subjects = ["Python","ML","AI","DBMS"]

marks = [92,88,95,85]

plt.bar(subjects, marks)

plt.title("Subject Marks")

plt.xlabel("Subjects")

plt.ylabel("Marks")

plt.show()
```

**Coding Exercise 3 – Scatter Plot**

```python
hours = [1,2,3,4,5,6]

marks = [35,48,59,72,85,94]

plt.scatter(hours, marks,
            color="red")

plt.title("Study Hours vs Marks")

plt.xlabel("Study Hours")

plt.ylabel("Marks")

plt.grid(True)

plt.show()
```

**Coding Exercise 4 – Histogram**

```python
import seaborn as sns

ages = [18,19,20,20,21,22,22,23,24,25,25,26]

sns.histplot(ages, bins=5)

plt.title("Age Distribution")

plt.show()
```

**Coding Exercise 5 – Box Plot**

```python
salary = [25000,28000,30000,32000,34000,35000,90000]

sns.boxplot(y=salary)

plt.title("Employee Salary Distribution")

plt.show()
```

**Coding Exercise 6 – Heatmap**

```python
import numpy as np

matrix = np.array([
    [5,7,8],
    [6,9,4],
    [3,8,2]
])

sns.heatmap(matrix,
            annot=True,
            cmap="viridis")

plt.title("Sample Heatmap")

plt.show()
```

**AI/ML Applications**

- Exploratory Data Analysis (EDA)
- Model Performance Visualization
- Feature Relationship Analysis
- Outlier Detection
- Correlation Analysis
- Dataset Presentation
- Business Intelligence Dashboards

## DAY 11 OF TRAINING

**Data Visualization Hands-on Practice – Titanic Dataset**

Day 11 focused on applying **Matplotlib** and **Seaborn** to a real-world dataset (Titanic Dataset). The session involved exploring passenger information, visualizing trends, identifying outliers, and understanding relationships between different features using various graphs. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Load and inspect a real-world dataset
- Perform Exploratory Data Analysis (EDA)
- Visualize Age Distribution
- Analyze Passenger Survival
- Detect Outliers using Box Plot
- Study Relationship between Age & Fare
- Create Correlation Heatmaps
- Interpret visualization results

## 1. Load the Dataset

Import the required libraries and load the Titanic dataset.

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("train.csv")

df.head(3)
```

**Check Missing Values**

```python
df.isnull().sum()
```

**Output**

```text
PassengerId      0
Survived         0
Pclass           0
Name             0
Sex              0
Age              0
SibSp            0
Parch            0
Ticket           0
Fare             0
Cabin          687
Embarked         2
```

The notebook begins by loading the Titanic dataset, displaying the first three rows, and checking missing values in each column. :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2}

**Exercise 1 – Load & Inspect Dataset**

**Task**

- Import NumPy, Pandas, Matplotlib and Seaborn.
- Load **train.csv**.
- Display first three rows.
- Check missing values.

**Solution**

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_csv("train.csv")

print(df.head(3))

print(df.isnull().sum())
```

## 2. Age Distribution Histogram

A histogram helps visualize the distribution of passenger ages.

**Code**

```python
plt.figure(figsize=(8,5))

sns.histplot(
    data=df,
    x="Age",
    color="teal",
    kde=True,
    edgecolor="darkgreen"
)

plt.title("Titanic Passenger Age Distribution")

plt.xlabel("Age")

plt.ylabel("Passenger Count")

plt.show()
```

**Observation**

- Most passengers were **young adults (20–35 years)**.

:contentReference[oaicite:3]{index=3}

**Exercise 2 – Age Distribution**

**Task**

- Create histogram
- Enable KDE
- Add title
- Label axes
- Identify most common age group

**Solution**

```python
plt.figure(figsize=(8,5))

sns.histplot(
    data=df,
    x="Age",
    kde=True,
    bins=20,
    color="purple"
)

plt.title("Titanic Passenger Age Distribution")

plt.xlabel("Age (Years)")

plt.ylabel("Passenger Count")

plt.show()
```

**Insight**

Most passengers were between **20–35 years**. :contentReference[oaicite:4]{index=4}

## 3. Survival Count Plot

Count plots compare categorical values.

**Code**

```python
plt.figure(figsize=(8,5))

sns.countplot(
    data=df,
    x="Survived",
    palette="Set2"
)

plt.title("Passenger Survival Count")

plt.xlabel("Survival")

plt.ylabel("Passengers")

plt.show()
```

**Exercise 3 – Passenger Survival**

**Task**

Visualize the number of passengers who survived and those who did not.

**Solution**

```python
plt.figure(figsize=(6,4))

sns.countplot(
    data=df,
    x="Survived",
    palette="Set2"
)

plt.title("Passenger Survival Counts (0 = Died, 1 = Survived)")

plt.xlabel("Survival Status")

plt.ylabel("Number of Passengers")

plt.show()
```

**Insight**

More passengers **died** than survived. :contentReference[oaicite:5]{index=5}

## 4. Box Plot – Fare Distribution

A box plot helps identify outliers.

**Code**

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    data=df,
    x="Fare",
    color="teal"
)

plt.title("Titanic Passenger Fare")

plt.show()
```

**Exercise 4 – Fare Outliers**

**Task**

- Draw a Box Plot
- Identify outliers
- Estimate highest fare

**Solution**

```python
plt.figure(figsize=(8,4))

sns.boxplot(
    data=df,
    x="Fare",
    color="pink"
)

plt.title("Ticket Fare Distribution & Outliers")

plt.xlabel("Ticket Fare")

plt.show()
```

**Insight**

- Many outliers are present.
- Highest fare is **above \$500**.
- Most passengers paid **less than \$50**. :contentReference[oaicite:6]{index=6}

## 5. Scatter Plot – Age vs Fare

Scatter plots show relationships between numerical variables.

**Handle Missing Values**

```python
median_age = df["Age"].median()

df["Age"] = df["Age"].fillna(median_age)
```

**Code**

```python
plt.figure(figsize=(8,5))

sns.scatterplot(
    data=df,
    x="Age",
    y="Fare",
    hue="Survived"
)

plt.title("Passenger Age vs Ticket Fare")

plt.grid(True)

plt.show()
```

**Exercise 5 – Age vs Fare**

**Task**

- Fill missing Age values
- Draw Scatter Plot
- Color passengers using Survival

**Solution**

```python
median_age = df["Age"].median()

df["Age"] = df["Age"].fillna(median_age)

plt.figure(figsize=(8,5))

sns.scatterplot(
    data=df,
    x="Age",
    y="Fare",
    hue="Survived",
    palette="coolwarm"
)

plt.title("Passenger Age vs Ticket Fare")

plt.xlabel("Age (Years)")

plt.ylabel("Ticket Fare")

plt.grid(True)

plt.show()
```

**Insight**

Passengers who paid **higher fares** had a greater chance of survival. :contentReference[oaicite:7]{index=7}

## 6. Correlation Heatmap

Heatmaps display correlation among numerical features.

**Code**

```python
columns = ["Survived","Pclass","Age","Fare"]

corr = df[columns].corr()

sns.heatmap(
    corr,
    annot=True,
    cmap="coolwarm",
    vmax=1,
    vmin=-1
)

plt.show()
```

**Exercise 6 – Correlation Matrix**

**Task**

- Calculate correlation matrix
- Plot Heatmap
- Analyze relationships

**Solution**

```python
numeric_df = df[
    ["Survived","Pclass","Age","Fare"]
]

corr_matrix = numeric_df.corr()

plt.figure(figsize=(6,4.5))

sns.heatmap(
    corr_matrix,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1
)

plt.title("Titanic Features Correlation Grid")

plt.show()
```

**Insights**

- **Pclass** has a **negative correlation** with survival.
- **Fare** has a **positive correlation** with survival.
- First-class passengers had better survival chances. :contentReference[oaicite:8]{index=8}

**AI/ML Applications**

- Exploratory Data Analysis (EDA)
- Outlier Detection
- Data Cleaning
- Feature Relationship Analysis
- Customer Behaviour Analysis
- Data Preprocessing
- Pattern Recognition

## DAY 12 OF TRAINING

**Exploratory Data Analysis (EDA) on House Price Dataset**

Day 12 focused on **Exploratory Data Analysis (EDA)** using a real-world **King County House Price Dataset**. The session covered loading and cleaning data, understanding dataset statistics, performing univariate and bivariate analysis, visualizing data using Seaborn & Matplotlib, identifying outliers, analyzing feature relationships, and preparing the dataset for Machine Learning. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Exploratory Data Analysis (EDA)
- Load and inspect datasets
- Select important features
- Perform statistical analysis
- Create visualizations using Seaborn
- Detect outliers
- Study feature relationships
- Generate correlation heatmaps
- Prepare data for Machine Learning

## 1. Import Libraries

Import the required Python libraries.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## 2. Load Dataset

Load the King County House Price dataset.

```python
df = pd.read_csv("kc_house_data.csv")

print(df.head())
```

Display dataset size.

```python
print(df.shape)
```

**Output**

```
21613 Rows
21 Columns
```

The dataset contains **21,613 houses** with **21 features**. :contentReference[oaicite:1]{index=1}

## 3. Select Important Features

Choose only useful columns for analysis.

```python
friendly_cols = [

"price",

"bedrooms",

"bathrooms",

"sqft_living",

"floors",

"waterfront",

"yr_built",

"condition"

]

df = df[friendly_cols]

df.head()
```

Selected Features

| Feature | Description |
|----------|-------------|
| price | House Price |
| bedrooms | Number of Bedrooms |
| bathrooms | Number of Bathrooms |
| sqft_living | Living Area |
| floors | Number of Floors |
| waterfront | Waterfront View |
| yr_built | Year Built |
| condition | House Condition |

This simplifies the dataset by keeping only the most understandable and relevant features. :contentReference[oaicite:2]{index=2}

## 4. Dataset Statistics

Display summary statistics.

```python
df.describe()
```

Displays

- Count
- Mean
- Standard Deviation
- Minimum
- Maximum
- Quartiles

**Dataset Information**

```python
df.info()
```

Shows

- Data types
- Memory usage
- Non-null values

The selected dataset has **8 columns**, all without missing values. :contentReference[oaicite:3]{index=3}

## 5. Univariate Analysis – Price Distribution

Visualize house prices using Histogram.

```python
plt.figure(figsize=(10,5))

sns.histplot(
    data=df,
    x="price",
    bins=50,
    kde=True,
    color="red"
)

plt.title("House Price Distribution")

plt.xlabel("Price")

plt.ylabel("Number of Houses")

plt.show()
```

**Observation**

- Most houses have moderate prices.
- Very expensive houses appear as outliers.

:contentReference[oaicite:4]{index=4}

## 6. Bedroom Count Analysis

Display the frequency of bedroom counts.

```python
plt.figure(figsize=(10,5))

sns.countplot(
    data=df,
    x="bedrooms",
    hue="bedrooms",
    palette="Set2",
    legend=False
)

plt.title("Bedroom Counts")

plt.show()
```

**Detect Outliers**

```python
giant_outlier = df[df["bedrooms"] > 10]

print(giant_outlier)
```

**Observation**

- Most houses contain **3–4 bedrooms**.
- Two extreme houses have more than **10 bedrooms**, including one with **33 bedrooms**.

:contentReference[oaicite:5]{index=5}

## 7. Bivariate Analysis – Size vs Price

Study the relationship between living area and price.

```python
plt.figure(figsize=(10,6))

sns.scatterplot(
    data=df,
    x="sqft_living",
    y="price",
    hue="waterfront"
)

plt.title("House Size vs Price")

plt.show()
```

**Observation**

- Larger houses generally cost more.
- Waterfront houses tend to have higher prices.

:contentReference[oaicite:6]{index=6}

## 8. Waterfront vs Price

Compare prices of waterfront and non-waterfront houses.

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    x="waterfront",
    y="price",
    data=df,
    hue="waterfront",
    palette="pastel"
)

plt.title("Waterfront vs House Price")

plt.show()
```

**Observation**

- Waterfront houses are significantly more expensive.

:contentReference[oaicite:7]{index=7}

## 9. House Condition vs Price

Analyze the effect of house condition on price.

```python
plt.figure(figsize=(8,5))

sns.barplot(
    x="condition",
    y="price",
    data=df,
    hue="condition",
    palette="coolwarm"
)

plt.title("House Condition vs Price")

plt.show()
```

**Observation**

Better-maintained houses usually have higher average prices.

:contentReference[oaicite:8]{index=8}

## 10. Correlation Heatmap

Display correlation between numerical features.

```python
plt.figure(figsize=(10,8))

correlation = df.corr()

sns.heatmap(
    correlation,
    annot=True,
    cmap="coolwarm",
    linewidths=0.5,
    vmin=-1,
    vmax=1
)

plt.title("Correlation Heatmap")

plt.show()
```

**Observation**

- Living area has the strongest positive correlation with price.
- Waterfront also positively affects price.

:contentReference[oaicite:9]{index=9}

## 11. Save Processed Dataset

```python
df.to_csv(
    "kc_house_filtered.csv",
    index=False
)
```

The filtered dataset is saved for further Machine Learning tasks. :contentReference[oaicite:10]{index=10}

**Summary of Findings**

- House size has the strongest impact on price.
- Waterfront houses are generally more expensive.
- Outliers such as houses with unusually high bedroom counts were identified.
- Correlation analysis helps understand relationships between variables.
- The cleaned dataset is ready for further Machine Learning analysis.

**AI/ML Applications**

- Exploratory Data Analysis (EDA)
- Feature Selection
- Outlier Detection
- Data Cleaning
- Correlation Analysis
- Data Visualization
- Dataset Preparation for Machine Learning

## DAY 13 OF TRAINING

**Data Preprocessing for Machine Learning**

Day 13 focused on **Data Preprocessing**, an essential step before training Machine Learning models. The session covered handling missing values, treating outliers, feature scaling, one-hot encoding, and preparing the final cleaned dataset for ML algorithms using Scikit-learn and Pandas. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Data Preprocessing
- Load and inspect datasets
- Handle Missing Values (Imputation)
- Detect & Treat Outliers
- Perform Feature Scaling
- Apply One-Hot Encoding
- Prepare final ML-ready dataset
- Save preprocessed data

## 1. Import Libraries & Load Dataset

Import required libraries and load the filtered house dataset.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.preprocessing import StandardScaler, MinMaxScaler

df = pd.read_csv("kc_house_filtered.csv")

df.head()
```

Check missing values.

```python
df.isnull().sum()
```

**Output**

```
price            0
bedrooms         0
bathrooms        0
sqft_living      0
floors           0
waterfront       0
yr_built         0
condition        0
```

The dataset is loaded successfully and contains no missing values initially. :contentReference[oaicite:1]{index=1}

## 2. Missing Value Imputation

To understand missing-value handling, random values are removed from the **Year Built** column and replaced using the **Median**.

**Why Median?**

- Less affected by extreme values
- Suitable for skewed numerical data
- Produces better estimates than mean in many cases

Median is preferred because it is robust against outliers. :contentReference[oaicite:2]{index=2}

**Exercise 1 – Missing Value Handling**

**Task**

- Identify missing values
- Replace missing values using Median

**Solution**

```python
median_year = df["yr_built"].median()

df["yr_built"] = df["yr_built"].fillna(median_year)
```

## 3. Outlier Capping using IQR

Extreme values can negatively affect Machine Learning models.

Instead of deleting them, **IQR (Interquartile Range) Capping** is used.

**Formula**

```
IQR = Q3 - Q1

Lower Limit = Q1 − 1.5 × IQR

Upper Limit = Q3 + 1.5 × IQR
```

**Function**

```python
def find_caps(column):

    Q1 = column.quantile(0.25)

    Q3 = column.quantile(0.75)

    IQR = Q3 - Q1

    lower = Q1 - 1.5 * IQR

    upper = Q3 + 1.5 * IQR

    return lower, upper
```

Apply capping.

```python
columns = ["price","sqft_living","bedrooms"]

for col in columns:

    lower, upper = find_caps(df[col])

    df[col] = df[col].clip(lower, upper)
```

**Output**

```
Price Outliers Capped

Sqft Living Outliers Capped

Bedroom Outliers Capped
```

IQR capping limits extreme values while preserving the dataset. :contentReference[oaicite:3]{index=3}

**Exercise 2 – Outlier Detection**

**Task**

- Detect outliers
- Cap them using IQR

**Solution**

```python
sns.boxplot(data=df,
            y="sqft_living")

plt.show()
```

## 4. Feature Scaling

Machine Learning algorithms perform better when numerical features are on similar scales.

Two scaling techniques are used.

| Scaler | Purpose |
|---------|----------|
| MinMaxScaler | Converts values between 0 and 1 |
| StandardScaler | Mean = 0, Standard Deviation = 1 |

:contentReference[oaicite:4]{index=4}

**Min-Max Scaling**

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()

df["Scaled_size"] = scaler.fit_transform(
    df[["sqft_living"]]
)
```

**Standard Scaling**

```python
from sklearn.preprocessing import StandardScaler

std = StandardScaler()

df["Year_Scaled"] = std.fit_transform(
    df[["yr_built"]]
)
```

**Output**

New columns created

```
Scaled_size

Year_Scaled
```

**Exercise 3 – Scaling Features**

**Task**

Normalize house size and standardize construction year.

**Solution**

```python
minmax = MinMaxScaler()

df["Scaled_size"] = minmax.fit_transform(
    df[["sqft_living"]]
)

standard = StandardScaler()

df["Year_Scaled"] = standard.fit_transform(
    df[["yr_built"]]
)
```

## 5. One-Hot Encoding

Machine Learning models cannot understand text values directly.

One-Hot Encoding converts categorical values into binary columns.

Example

| Neighborhood | Budget | Mid-Range | Premium |
|--------------|:------:|:---------:|:-------:|
| Budget | 1 | 0 | 0 |
| Premium | 0 | 0 | 1 |
| Mid-Range | 0 | 1 | 0 |

A random **Neighborhood** category is created and encoded using `pd.get_dummies()`. :contentReference[oaicite:5]{index=5}

**Code**

```python
neighborhoods = [

"Budget",

"Mid-Range",

"Premium"

]

df["Neighborhood"] = np.random.choice(
    neighborhoods,
    size=len(df)
)

df_encoded = pd.get_dummies(
    df,
    columns=["Neighborhood"],
    prefix="Loc",
    dtype=int
)
```

**New Columns**

```
Loc_Budget

Loc_Mid-Range

Loc_Premium
```

**Exercise 4 – One-Hot Encoding**

**Task**

Convert Neighborhood into numerical columns.

**Solution**

```python
df_encoded = pd.get_dummies(

    df,

    columns=["Neighborhood"],

    prefix="Loc"

)
```

## 6. Final Dataset Preparation

Select only important ML features.

```python
final_cols = [

"price",

"bedrooms",

"bathrooms",

"Scaled_size",

"floors",

"waterfront",

"sqft_living",

"condition",

"Loc_Budget",

"Loc_Mid-Range",

"Loc_Premium"

]

df_final = df_encoded[final_cols]
```

Save dataset.

```python
df_final.to_csv(

"kc_house_preprocessed.csv",

index=False

)
```

**Output**

```
Preprocessed data saved successfully as

kc_house_preprocessed.csv
```

The final dataset contains cleaned, scaled, and encoded features ready for Machine Learning. :contentReference[oaicite:6]{index=6}

**Summary**

The preprocessing pipeline includes:

- Loading dataset
- Handling missing values
- Outlier treatment
- Feature scaling
- One-Hot Encoding
- Saving final ML-ready dataset

**AI/ML Applications**

- Data Cleaning
- Missing Value Treatment
- Outlier Handling
- Feature Engineering
- Data Transformation
- Machine Learning Preprocessing
- Model Optimization

## DAY 14 OF TRAINING

**Linear Regression – Building Our First House Price Prediction Model**

Day 14 focused on training our **first Machine Learning model using Linear Regression**. We used the preprocessed house dataset created in previous sessions, split the data into training and testing sets, trained both **Simple Linear Regression** and **Multiple Linear Regression** models, predicted house prices, and evaluated model performance using **MAE** and **R² Score**. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Linear Regression
- Train our first Machine Learning model
- Perform Train-Test Split
- Build Simple Linear Regression
- Build Multiple Linear Regression
- Predict House Prices
- Evaluate model accuracy
- Understand MAE and R² Score
- Compare different regression models

## 1. What is Linear Regression?

Linear Regression is a Machine Learning algorithm used to predict continuous numerical values.

Example:

- Predict House Price
- Predict Salary
- Predict Temperature
- Predict Sales

It finds the **best-fit straight line** that represents the relationship between input features and output values. :contentReference[oaicite:1]{index=1}

**Linear Equation**

```text
y = mx + c
```

Where:

- y = Predicted Price
- x = Input Feature
- m = Slope (Coefficient)
- c = Intercept

## 2. Import Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, r2_score
```

## 3. Load Preprocessed Dataset

```python
df = pd.read_csv("kc_house_preprocessed.csv")

print("Successfully loaded")

df.head()
```

The dataset contains **21,613 rows and 11 columns**. :contentReference[oaicite:2]{index=2}

## 4. Train-Test Split

Before training, the dataset is divided into:

| Dataset | Purpose |
|---------|---------|
| Training Set | Used to train the model |
| Testing Set | Used to evaluate the model |

80% data is used for training and 20% for testing. :contentReference[oaicite:3]{index=3}

**Separate Features and Target**

```python
X = df.drop(columns=["price"])

y = df["price"]
```

**Split Dataset**

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)
```

**Output**

```text
Training Set = 17,290 rows

Testing Set = 4,323 rows
```

:contentReference[oaicite:4]{index=4}

## 5. Simple Linear Regression

Simple Linear Regression uses only **one feature** to predict the target value.

Here we use:

```text
Scaled_size → Price
```

**Select Feature**

```python
X_train_simple = X_train[["Scaled_size"]]

X_test_simple = X_test[["Scaled_size"]]
```

**Initialize Model**

```python
model = LinearRegression()
```

**Train Model**

```python
model.fit(
    X_train_simple,
    y_train
)
```

**Output**

```text
Simple Linear Regression model has been trained successfully!
```

:contentReference[oaicite:5]{index=5}

## 6. Intercept and Coefficient

```python
m = model.coef_[0]

c = model.intercept_
```

**Output**

```text
Robot Intercept = $142,507.74

Robot Coefficient = $822,686.02
```

**Equation**

```text
Price = (822686.02 × Scaled_size) + 142507.74
```

:contentReference[oaicite:6]{index=6}

## 7. Predict Prices

```python
y_pred_simple = model.predict(
    X_test_simple
)
```

The model predicts prices for unseen houses.

## 8. Best Fit Line Visualization

```python
plt.figure(figsize=(10,6))

plt.scatter(
    X_test_simple["Scaled_size"],
    y_test,
    color="royalblue",
    alpha=0.3,
    label="Actual Houses"
)

plt.plot(
    X_test_simple["Scaled_size"],
    y_pred_simple,
    color="crimson",
    linewidth=3,
    label="Prediction Line"
)

plt.xlabel("Scaled Size")

plt.ylabel("Price")

plt.title("House Price Prediction")

plt.legend()

plt.show()
```

This graph displays the **Best-Fit Line** generated by Linear Regression. :contentReference[oaicite:7]{index=7}

## 9. Multiple Linear Regression

Instead of one clue, Multiple Regression uses **all available features**.

Examples:

- Bedrooms
- Bathrooms
- Floors
- Size
- Waterfront
- Condition
- Neighborhood

Using more useful information generally improves predictions. :contentReference[oaicite:8]{index=8}

**Train Multiple Regression Model**

```python
multiple_model = LinearRegression()

multiple_model.fit(
    X_train,
    y_train
)
```

**Predict Prices**

```python
y_pred_multiple = multiple_model.predict(
    X_test
)
```

## 10. Predict Custom House Price

```python
custom_house = pd.DataFrame([{

'bedrooms':3.0,

'bathrooms':2.0,

'Scaled_size':0.35,

'floors':2.0,

'waterfront':0,

'sqft_living':1800.0,

'condition':4,

'Loc_Budget':0,

'Loc_Mid-Range':1,

'Loc_Premium':0

}])
```

```python
custom_house = custom_house[X_train.columns]

predicted_price = multiple_model.predict(
    custom_house
)[0]

print(predicted_price)
```

**Output**

```text
Predicted Price = $506,195.81
```

:contentReference[oaicite:9]{index=9}

## 11. Model Evaluation

Two metrics are used.

**Mean Absolute Error (MAE)**

Measures average prediction error.

**Formula**

```text
MAE = Average(|Actual − Predicted|)
```

Lower MAE is better. :contentReference[oaicite:10]{index=10}

**R² Score**

Measures how much variation is explained by the model.

Range:

```text
0 → Poor Model

1 → Perfect Model
```

Higher R² is better. :contentReference[oaicite:11]{index=11}

## 12. Calculate Evaluation Metrics

```python
mae_simple = mean_absolute_error(
    y_test,
    y_pred_simple
)

r2_simple = r2_score(
    y_test,
    y_pred_simple
)

mae_multiple = mean_absolute_error(
    y_test,
    y_pred_multiple
)

r2_multiple = r2_score(
    y_test,
    y_pred_multiple
)
```

## 13. Model Comparison

| Model | MAE | R² Score |
|--------|------|---------|
| Simple Linear Regression | $141,707.41 | 49.9% |
| Multiple Linear Regression | $136,392.66 | 53.3% |

:contentReference[oaicite:12]{index=12}

## 14. Interpretation

- Multiple Regression gives lower error.
- Multiple Regression explains more price variation.
- More useful features improve prediction accuracy.
- Feature Engineering plays an important role in Machine Learning. :contentReference[oaicite:13]{index=13}

**Exercise 1 – Change Train-Test Split**

**Task**

Change:

```python
test_size = 0.20
```

to

```python
test_size = 0.30
```

Train the model again and compare the **R² Score**.

**Solution**

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score

X = df.drop(columns=["price"])
y = df["price"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.30,
    random_state=42
)

model = LinearRegression()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

print("R² Score:", r2_score(y_test, y_pred))
```

**Observation**

- Training data becomes **70%** while testing data becomes **30%**.
- The R² Score may change slightly depending on the dataset.
- A larger testing dataset provides better model evaluation.

**Exercise 2 – Predict Using Bedrooms**

**Task**

Train a Simple Linear Regression model using **Bedrooms** instead of **Scaled_size**.

**Solution**

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, r2_score

X = df[["bedrooms"]]
y = df["price"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)

model = LinearRegression()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

print("MAE :", mean_absolute_error(y_test, y_pred))
print("R² Score :", r2_score(y_test, y_pred))
```

**AI/ML Applications**

- House Price Prediction
- Stock Market Forecasting
- Sales Prediction
- Weather Prediction
- Demand Forecasting
- Business Analytics
- Real Estate Analysis

## DAY 15 OF TRAINING

**Polynomial Regression – Teaching Our Robot to Curve!**

Day 15 focused on **Polynomial Regression**, an advanced form of Linear Regression that can model **curved relationships** between input features and target values. We trained a Polynomial Regression model, evaluated its performance using **MAE** and **R² Score**, and learned how polynomial features improve prediction accuracy when data is non-linear. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Polynomial Regression
- Compare Linear vs Polynomial Regression
- Train a Polynomial Regression model
- Create Polynomial Features
- Evaluate model performance
- Interpret MAE and R² Score
- Visualize polynomial curves
- Understand non-linear prediction

## 1. What is Polynomial Regression?

Polynomial Regression is a Machine Learning algorithm that extends Linear Regression by fitting a **curved line** instead of a straight line.

**Why Polynomial Regression?**

Sometimes data does not follow a straight-line relationship.

Examples:

- House Price Prediction
- Population Growth
- Sales Forecasting
- Temperature Prediction

Polynomial Regression introduces higher-degree terms (like **x²**) to capture these curves. :contentReference[oaicite:1]{index=1}

## 2. Linear vs Polynomial Regression

| Linear Regression | Polynomial Regression |
|-------------------|----------------------|
| Fits a straight line | Fits a curved line |
| Works for linear data | Works for non-linear data |
| Simple model | More flexible model |
| Less complex | Better captures complex patterns |

## 3. Import Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score
```

## 4. Load Dataset

Load the preprocessed house price dataset.

```python
df = pd.read_csv("kc_house_preprocessed.csv")

print("Successfully loaded!")

df.head()
```

To make visualization simpler, a random sample of **80 houses** is selected.

```python
df_sample = df.sample(
    n=80,
    random_state=42
)
```

Split the dataset.

```python
X = df_sample.drop(columns="price")

y = df_sample["price"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)
```

**Output**

```
Training Set : 64 Houses

Testing Set : 16 Houses
```

The notebook loads the preprocessed dataset, samples 80 houses, and splits them into **64 training** and **16 testing** records. :contentReference[oaicite:2]{index=2}

## 5. Train Polynomial Regression Model

A Polynomial Regression model of **Degree 2** is created using a Scikit-learn pipeline.

```python
poly_model = make_pipeline(

    PolynomialFeatures(degree=2),

    LinearRegression()

)
```

Train the model.

```python
poly_model.fit(
    X_train,
    y_train
)

print("Polynomial Regression model trained successfully!")
```

**Output**

```
Polynomial Regression model trained successfully!
```

The model creates squared features internally, allowing it to learn curved relationships. :contentReference[oaicite:3]{index=3}

## 6. Predict House Prices

Predict prices for the testing dataset.

```python
y_pred = poly_model.predict(X_test)
```

Predict prices for the training dataset.

```python
y_train_pred = poly_model.predict(X_train)
```

## 7. Evaluate Model Performance

Calculate prediction accuracy.

```python
mae = mean_absolute_error(
    y_test,
    y_pred
)

accuracy = r2_score(
    y_test,
    y_pred
)

train_accuracy = r2_score(
    y_train,
    y_train_pred
)
```

**Output**

```
Average Miss (MAE) : $174,951.08

Testing Accuracy (R²) : 43.28%

Training Accuracy (R²) : 71.13%
```

These metrics summarize how well the polynomial model performs on both training and testing data. :contentReference[oaicite:4]{index=4}

## 8. Visualize Polynomial Curve

```python
plt.figure(figsize=(10,6))

plt.scatter(
    X,
    y,
    color="royalblue",
    alpha=0.7,
    label="Actual Houses"
)

x_range = np.linspace(
    X["sqft_living"].min(),
    X["sqft_living"].max(),
    500
).reshape(-1,1)

y_range_pred = poly_model.predict(x_range)

plt.plot(
    x_range,
    y_range_pred,
    color="crimson",
    linewidth=3,
    label="Polynomial Curve"
)

plt.title("Polynomial Regression - House Price Prediction")

plt.xlabel("House Size")

plt.ylabel("Price")

plt.legend()

plt.grid(True)

plt.show()
```

**Note**

The notebook reports a **ValueError (`x and y must be the same size`)** while plotting because the scatter plot uses feature and target arrays with incompatible dimensions. This needs to be corrected before the visualization can be displayed. :contentReference[oaicite:5]{index=5}

## 9. Performance Metrics

**Mean Absolute Error (MAE)**

Measures the average prediction error.

**Formula**

```text
MAE = Average(|Actual − Predicted|)
```

Lower MAE indicates better predictions.

**R² Score**

Measures how well the model explains the variation in the data.

| R² Score | Interpretation |
|-----------|----------------|
| 0 | Poor Model |
| 1 | Perfect Model |

Higher R² indicates better model performance. :contentReference[oaicite:6]{index=6}

## 10. Advantages of Polynomial Regression

- Captures curved relationships
- Better prediction for non-linear data
- Improves flexibility
- More accurate than linear regression for complex datasets
- Easy to implement using Scikit-learn

**Exercise 1 – Change Polynomial Degree**

**Task**

Change the polynomial degree from **2** to **3** and compare the model accuracy.

**Solution**

```python
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_absolute_error, r2_score

poly_model = make_pipeline(
    PolynomialFeatures(degree=3),
    LinearRegression()
)

poly_model.fit(X_train, y_train)

y_pred = poly_model.predict(X_test)

print("MAE :", mean_absolute_error(y_test, y_pred))
print("R² Score :", r2_score(y_test, y_pred))
```

**Observation**

- Increasing the polynomial degree makes the model more flexible.
- It may improve prediction accuracy for complex datasets.
- Very high degrees can lead to **overfitting**.

**Exercise 2 – Compare Linear and Polynomial Regression**

**Task**

Train both **Linear Regression** and **Polynomial Regression** models and compare their performance.

**Solution**

```python
from sklearn.linear_model import LinearRegression
from sklearn.pipeline import make_pipeline
from sklearn.preprocessing import PolynomialFeatures
from sklearn.metrics import mean_absolute_error, r2_score

# Linear Regression
linear_model = LinearRegression()

linear_model.fit(X_train, y_train)

linear_pred = linear_model.predict(X_test)

# Polynomial Regression
poly_model = make_pipeline(
    PolynomialFeatures(degree=2),
    LinearRegression()
)

poly_model.fit(X_train, y_train)

poly_pred = poly_model.predict(X_test)

print("Linear Regression")
print("MAE :", mean_absolute_error(y_test, linear_pred))
print("R² :", r2_score(y_test, linear_pred))

print("\nPolynomial Regression")
print("MAE :", mean_absolute_error(y_test, poly_pred))
print("R² :", r2_score(y_test, poly_pred))
```

**AI/ML Applications**

- House Price Prediction
- Stock Market Analysis
- Weather Forecasting
- Sales Prediction
- Medical Data Analysis
- Demand Forecasting
- Population Growth Prediction

## DAY 16 OF TRAINING

**Ridge & Lasso Regularization – Preventing Overfitting in Machine Learning**

Day 16 focused on **Regularization**, a technique used to prevent **overfitting** in Machine Learning models. We learned how **Ridge Regression (L2)** and **Lasso Regression (L1)** improve Polynomial Regression by controlling model complexity, reducing unnecessary feature weights, and improving prediction performance. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Overfitting
- Learn the concept of Regularization
- Compare Ridge and Lasso Regression
- Train Polynomial Regression with Regularization
- Evaluate model performance
- Compare MAE and R² Score
- Visualize Regularized Models
- Prevent over-complex Machine Learning models

## 1. What is Overfitting?

Overfitting occurs when a Machine Learning model learns the **training data too perfectly**, including noise and unnecessary patterns. As a result, it performs well on training data but poorly on new or unseen data.

**Example**

- **Overfitted Model:** Memorizes every training example.
- **Good Model:** Learns the general pattern and predicts unseen data accurately.

Regularization helps reduce overfitting by limiting model complexity. :contentReference[oaicite:1]{index=1}

## 2. Types of Regularization

| Regularization | Description |
|---------------|-------------|
| **Ridge Regression (L2)** | Shrinks feature weights closer to zero but never makes them exactly zero. |
| **Lasso Regression (L1)** | Shrinks some feature weights to exactly zero, effectively removing less important features. |

## 3. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.preprocessing import PolynomialFeatures
from sklearn.pipeline import make_pipeline
from sklearn.metrics import mean_absolute_error, r2_score
```

## 4. Load Dataset

Load the preprocessed house price dataset.

```python
df = pd.read_csv("kc_house_preprocessed.csv")

print("Successfully loaded!")

df.head()
```

Select a random sample of 80 houses.

```python
df_sample = df.sample(
    n=80,
    random_state=42
)
```

Choose the feature and target.

```python
X = df_sample[["Scaled_size"]]

y = df_sample["price"]
```

Split the dataset.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)
```

**Output**

```text
Successfully loaded 'kc_house_preprocessed.csv'

Training Set : 64 Houses

Testing Set : 16 Houses
```

The notebook loads the cleaned dataset, selects **80 random samples**, and divides them into **64 training** and **16 testing** records. :contentReference[oaicite:2]{index=2}

## 5. Train Polynomial Regression (Without Regularization)

Train a Degree 6 Polynomial Regression model without applying any regularization.

```python
wild_model = make_pipeline(
    PolynomialFeatures(degree=6),
    LinearRegression()
)

wild_model.fit(
    X_train,
    y_train
)
```

Predict house prices.

```python
y_pred_wild = wild_model.predict(X_test)
```

Calculate performance.

```python
mae_wild = mean_absolute_error(
    y_test,
    y_pred_wild
)

accuracy_wild = r2_score(
    y_test,
    y_pred_wild
)
```

**Output**

```text
Average Miss (MAE): $193,581.71

Accuracy Score (R²): 31.47%
```

This model overfits because it tries to fit the training data too closely. :contentReference[oaicite:3]{index=3}

## 6. Ridge Regression (L2 Regularization)

Ridge Regression reduces overfitting by shrinking model coefficients while keeping all features.

```python
ridge_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=0.1)
)

ridge_model.fit(
    X_train,
    y_train
)
```

Predict values.

```python
y_pred_ridge = ridge_model.predict(X_test)
```

Evaluate performance.

```python
mae_ridge = mean_absolute_error(
    y_test,
    y_pred_ridge
)

accuracy_ridge = r2_score(
    y_test,
    y_pred_ridge
)
```

**Output**

```text
Average Miss (MAE): $179,774.23

Accuracy Score (R²): 40.75%
```

Ridge Regression produces smoother predictions and improves model performance. :contentReference[oaicite:4]{index=4}

## 7. Lasso Regression (L1 Regularization)

Lasso Regression removes less important features by forcing some coefficients to become zero.

```python
lasso_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(
        alpha=100.0,
        max_iter=10000
    )
)

lasso_model.fit(
    X_train,
    y_train
)
```

Predict values.

```python
y_pred_lasso = lasso_model.predict(X_test)
```

Evaluate performance.

```python
mae_lasso = mean_absolute_error(
    y_test,
    y_pred_lasso
)

accuracy_lasso = r2_score(
    y_test,
    y_pred_lasso
)
```

**Output**

```text
Average Miss (MAE): $178,785.42

Accuracy Score (R²): 41.45%
```

Lasso improves prediction accuracy while simplifying the model by removing unnecessary polynomial terms. :contentReference[oaicite:5]{index=5}

## 8. Compare All Models

| Model | MAE | R² Score |
|--------|---------|----------|
| Polynomial Regression | $193,581.71 | 31.47% |
| Ridge Regression | $179,774.23 | 40.75% |
| Lasso Regression | $178,785.42 | 41.45% |

**Observation**

- Polynomial Regression overfits the data.
- Ridge reduces coefficient values and improves accuracy.
- Lasso removes less useful features and gives the best performance among the three models. :contentReference[oaicite:6]{index=6}

## 9. Visualize Regularized Models

Plot all models on the same graph for comparison.

```python
plt.figure(figsize=(12,7))

plt.scatter(
    X_train,
    y_train,
    color="royalblue",
    alpha=0.6,
    label="Actual Houses"
)

x_range = np.linspace(
    X["Scaled_size"].min(),
    X["Scaled_size"].max(),
    500
).reshape(-1,1)

plt.plot(
    x_range,
    wild_model.predict(x_range),
    '--',
    color="orange",
    label="Polynomial"
)

plt.plot(
    x_range,
    ridge_model.predict(x_range),
    color="crimson",
    linewidth=3,
    label="Ridge"
)

plt.plot(
    x_range,
    lasso_model.predict(x_range),
    color="forestgreen",
    linewidth=3,
    label="Lasso"
)

plt.title("Regularization Comparison")

plt.xlabel("Scaled House Size")

plt.ylabel("House Price")

plt.legend()

plt.grid(True)

plt.show()
```

**Observation**

The graph shows that Ridge and Lasso produce smoother prediction curves compared to the highly flexible polynomial model, helping reduce overfitting. :contentReference[oaicite:7]{index=7}

**Exercise 1 – Change Ridge Alpha**

**Task**

Change:

```python
Ridge(alpha=0.1)
```

to

```python
Ridge(alpha=1.0)
```

Compare MAE and R² Score.

**Solution**

```python
ridge_model = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=1.0)
)

ridge_model.fit(X_train, y_train)

y_pred = ridge_model.predict(X_test)

print("MAE :", mean_absolute_error(y_test, y_pred))
print("R² Score :", r2_score(y_test, y_pred))
```

**Observation**

Increasing **alpha** applies stronger regularization, producing a simpler model. Very high values may reduce overfitting but can also cause underfitting.

**Exercise 2 – Compare Ridge and Lasso**

**Task**

Train both Ridge and Lasso Regression models and compare their performance.

**Solution**

```python
ridge = make_pipeline(
    PolynomialFeatures(degree=6),
    Ridge(alpha=0.1)
)

lasso = make_pipeline(
    PolynomialFeatures(degree=6),
    Lasso(alpha=100.0, max_iter=10000)
)

ridge.fit(X_train, y_train)
lasso.fit(X_train, y_train)

ridge_pred = ridge.predict(X_test)
lasso_pred = lasso.predict(X_test)

print("Ridge R² :", r2_score(y_test, ridge_pred))
print("Lasso R² :", r2_score(y_test, lasso_pred))
```

**Result**

- Ridge keeps all features while reducing their impact.
- Lasso removes less important features by assigning zero coefficients.
- In this notebook, **Lasso achieved the best R² Score (41.45%)**. :contentReference[oaicite:8]{index=8}

**AI/ML Applications**

- Preventing Overfitting
- Feature Selection
- House Price Prediction
- Stock Market Analysis
- Medical Data Prediction
- Financial Forecasting
- Business Analytics

## DAY 17 OF TRAINING

**Classification & Logistic Regression**

Day 17 focused on **Classification** using **Logistic Regression**. Unlike Regression, which predicts continuous values, Classification predicts **categories or labels**. The session used the **Titanic Dataset** to perform both **Binary Classification (Survived/Not Survived)** and **Multiclass Classification (Passenger Class)** using Logistic Regression. :contentReference[oaicite:0]{index=0}

**Learning Objectives:-**

- Understand Classification in Machine Learning
- Learn Binary and Multiclass Classification
- Understand Logistic Regression
- Learn the Sigmoid Function
- Preprocess the Titanic Dataset
- Train Binary Classification Model
- Train Multiclass Classification Model
- Evaluate Models using Accuracy, Confusion Matrix & Classification Report

## 1. What is Classification?

Classification is a supervised Machine Learning technique used to predict **categories or labels** instead of continuous values.

**Types of Classification**

| Type | Description | Example |
|------|-------------|---------|
| Binary Classification | Predicts one of two classes | Survived / Not Survived |
| Multiclass Classification | Predicts one of three or more classes | Passenger Class (1,2,3) |

Examples:

- Spam Detection
- Disease Prediction
- Email Classification
- Titanic Survival Prediction

:contentReference[oaicite:1]{index=1}

## 2. Import Required Libraries

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import (
    accuracy_score,
    confusion_matrix,
    classification_report
)
```

## 3. Load Titanic Dataset

```python
df = pd.read_csv("train.csv")

print(df.shape)

df.head()
```

**Output**

```
Dataset Shape

(891,12)
```

The Titanic dataset contains **891 passenger records** with **12 features** including age, fare, gender, passenger class, and survival status. :contentReference[oaicite:2]{index=2}

## 4. Data Preprocessing

Machine Learning models require numerical data.

**Steps Performed**

- Fill missing values in **Age** using Median
- Fill missing values in **Embarked** using Mode
- Convert **Sex** into numerical values

```python
df["Age"] = df["Age"].fillna(df["Age"].median())

df["Embarked"] = df["Embarked"].fillna(
    df["Embarked"].mode()[0]
)

df["IsFemale"] = df["Sex"].map({
    "female":1,
    "male":0
})
```

Selected Features

```python
features = [

"Age",

"Fare",

"SibSp",

"Parch",

"IsFemale"

]
```

:contentReference[oaicite:3]{index=3}

## 5. Binary Classification

**Target**

```
Survived
```

**Features**

- Age
- Fare
- SibSp
- Parch
- IsFemale

Binary Classification predicts whether a passenger **survived (1)** or **did not survive (0)**. :contentReference[oaicite:4]{index=4}

## 6. Logistic Regression & Sigmoid Function

Logistic Regression calculates a weighted sum of the input features and passes it through the **Sigmoid Function**, producing a probability between **0 and 1**.

**Sigmoid Equation**

```text
σ(z) = 1 / (1 + e⁻ᶻ)
```

**Code**

```python
def sigmoid(z):

    return 1 / (1 + np.exp(-z))
```

If Probability ≥ 0.5

```
Predict Survived
```

Else

```
Predict Not Survived
```

:contentReference[oaicite:5]{index=5}

## 7. Split Dataset

```python
X = df[features]

y = df["Survived"]

X_train, X_test, y_train, y_test = train_test_split(

    X,

    y,

    test_size=0.20,

    random_state=42

)
```

**Output**

```
Training Set : 712 Rows

Testing Set : 179 Rows
```

:contentReference[oaicite:6]{index=6}

## 8. Train Binary Logistic Regression Model

```python
binary_model = LogisticRegression(
    max_iter=1000
)

binary_model.fit(
    X_train,
    y_train
)

y_pred = binary_model.predict(X_test)
```

**Output**

```
Binary Classification Accuracy

78.21%
```

The Binary Logistic Regression model correctly predicts passenger survival with an accuracy of approximately **78.21%**. :contentReference[oaicite:7]{index=7}

## 9. Model Evaluation

**Accuracy**

```python
accuracy_score(y_test,y_pred)
```

Accuracy

```
78.21%
```

**Confusion Matrix**

```python
cm = confusion_matrix(
    y_test,
    y_pred
)
```

Output

```
[[89 16]

 [23 51]]
```

**Classification Report**

```python
print(
classification_report(
y_test,
y_pred
))
```

| Metric | Value |
|---------|-------|
| Precision | 0.78 |
| Recall | 0.77 |
| F1-Score | 0.77 |

:contentReference[oaicite:8]{index=8}

## 10. Multiclass Classification

Instead of predicting survival, the model predicts the **Passenger Class (Pclass)**.

**Target**

```
Pclass
```

**Features**

- Survived
- Age
- Fare
- SibSp
- Parch
- IsFemale

Multiclass Logistic Regression predicts one of **three passenger classes**. :contentReference[oaicite:9]{index=9}

## 11. Train Multiclass Model

```python
features_multi = [

"Survived",

"Age",

"Fare",

"SibSp",

"Parch",

"IsFemale"

]

X = df[features_multi]

y = df["Pclass"]

multiclass_model = LogisticRegression(
    max_iter=1000
)

multiclass_model.fit(
    X_train,
    y_train
)
```

**Output**

```
Multiclass Logistic Regression Model Trained Successfully
```

## 12. Evaluate Multiclass Model

```python
y_pred = multiclass_model.predict(
    X_test
)

accuracy_score(
    y_test,
    y_pred
)
```

**Output**

```
Accuracy

82.68%
```

Classification Report

| Class | Precision | Recall | F1-Score |
|-------|-----------|--------|----------|
| Class 1 | 0.94 | 0.89 | 0.91 |
| Class 2 | 0.62 | 0.30 | 0.41 |
| Class 3 | 0.81 | 0.98 | 0.88 |

:contentReference[oaicite:10]{index=10}

## 13. Binary vs Multiclass Classification

| Feature | Binary | Multiclass |
|----------|---------|------------|
| Number of Classes | 2 | 3 or More |
| Example | Survived / Not Survived | Passenger Class |
| Function Used | Sigmoid | Softmax / One-vs-Rest |
| Output | Two Classes | Multiple Classes |

:contentReference[oaicite:11]{index=11}

**Exercise 1 – Add Pclass Feature**

**Task**

Add **Pclass** to the Binary Classification model and compare the accuracy.

**Solution**

```python
features_with_pclass = [
    "Age",
    "Fare",
    "SibSp",
    "Parch",
    "IsFemale",
    "Pclass"
]

X = df[features_with_pclass]
y = df["Survived"]

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)

model = LogisticRegression(max_iter=1000)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

print(
    accuracy_score(y_test, y_pred)
)
```

**Output**

```
Accuracy with Pclass

81.01%

Previous Accuracy

78.21%
```

**Observation**

Adding **Pclass** improves prediction accuracy because passenger class strongly influences survival chances. :contentReference[oaicite:12]{index=12}

**Exercise 2 – Change Threshold**

**Task**

Change the prediction threshold from **0.5** to **0.7**.

**Solution**

```python
probabilities = binary_model.predict_proba(X_test)

prob_survival = probabilities[:,1]

y_pred_custom = (
    prob_survival >= 0.7
).astype(int)

print(
accuracy_score(
    y_test,
    y_pred_custom
))
```

**Observation**

- Higher threshold makes the model more conservative.
- False Positives decrease.
- False Negatives increase.
- Fewer passengers are predicted to survive.

> **Note:** The notebook shows a `NameError` because it uses `X_test_bin`, which was not defined. Replacing it with `X_test` fixes the code. :contentReference[oaicite:13]{index=13}

**AI/ML Applications**

- Spam Detection
- Email Classification
- Disease Prediction
- Fraud Detection
- Customer Churn Prediction
- Sentiment Analysis
- Titanic Survival Prediction

