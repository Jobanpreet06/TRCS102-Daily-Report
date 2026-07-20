
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
