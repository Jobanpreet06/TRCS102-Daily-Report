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

