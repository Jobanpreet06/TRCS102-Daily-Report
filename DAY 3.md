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
