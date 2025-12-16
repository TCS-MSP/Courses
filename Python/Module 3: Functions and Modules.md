[Previous Module - Module 2: Control Structures](./Module%202:%20Control%20Structures.md)

# Module 3: Functions and Modules 🧩
⏱️ **Estimated reading time:** ~25 minutes

Functions and modules are essential tools for structuring Python programs. **Functions** let you group logic into reusable blocks, while **modules** allow you to organize related code into separate files. Together, they help keep code clean, scalable, and easier to reason about as programs grow.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Define and call functions
* Use parameters, arguments, and return values effectively
* Understand variable scope and lifetime
* Write and use lambda (anonymous) functions
* Import built-in and custom modules
* Install and use third-party packages with `pip`

---

## Lesson 3.1: Functions

### Defining and Calling Functions

A **function** is a reusable block of code that performs a specific task. Functions reduce repetition, improve readability, and make programs easier to maintain.

### Basic Function Structure

```python
def function_name(parameters):
    # Code block (Lesson 3.1)
    return result
```

* `def` tells Python you are defining a function
* The function body must be indented
* `return` sends a value back to the caller

---

### Simple Function Example

```python
def greet():
    # This function prints a greeting (Lesson 3.1)
    print("Hello, World!")

greet()  # Output: Hello, World!
```

---

### Function with Parameters and Return Value

```python
def multiply_number_by_5(num):
    # Multiply the input by 5 and return the result
    return num * 5

result = multiply_number_by_5(3)
print(result)  # Output: 15
```

> 💡 Parameters are placeholders; arguments are actual values passed in.

---

### Scope and Lifetime of Variables

#### Local Scope

* Variables defined **inside a function**
* Exist only while the function runs

```python
def example():
    local_var = 10  # Local variable
    print(local_var)

example()
# print(local_var)  # ❌ NameError (out of scope)
```

#### Global Scope

* Variables defined **outside all functions**
* Accessible throughout the module

```python
count = 0  # Global variable

def increment():
    global count  # Refers to the global variable
    count += 1

increment()
print(count)  # Output: 1
```

#### Shadowing

```python
x = 10  # Global variable

def shadow_example():
    x = 5  # Local variable shadows global x
    print(x)

shadow_example()  # Output: 5
print(x)          # Output: 10
```

---

## Arguments, Parameters, and Return Values

### Positional Arguments

Arguments are matched to parameters by position.

```python
def multiply(x, y):
    return x * y

print(multiply(2, 3))  # Output: 6
```

---

### Keyword Arguments

Keyword arguments improve readability and allow reordering.

```python
def greet(name, age):
    print(f"Hello, {name}. You are {age} years old.")

greet(age=30, name="Alice")
# Output: Hello, Alice. You are 30 years old.
```

---

### Default Parameters

Default values are used when no argument is provided.

```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()        # Output: Hello, Guest!
greet("John")  # Output: Hello, John!
```

---

### Variable-Length Arguments

#### *args (Multiple Positional Arguments)

```python
def add(*args):
    # args is a tuple of all passed values
    return sum(args)

print(add(1, 2, 3, 4))  # Output: 10
```

---

#### **kwargs (Multiple Keyword Arguments)

```python
def display_info(**kwargs):
    # kwargs is a dictionary of key-value pairs
    for key, value in kwargs.items():
        print(f"{key}: {value}")

display_info(name="Alice", age=30)
# Output:
# name: Alice
# age: 30
```

---

### Returning Multiple Values

Python functions can return multiple values using tuples.

```python
def divide(a, b):
    quotient = a // b  # Integer division
    remainder = a % b
    return quotient, remainder

q, r = divide(10, 3)
print(q, r)  # Output: 3 1
```

---

### Lambda Functions ⚡

Lambda functions are **small, anonymous functions** used for short operations. They are commonly passed into functions like `map()`, `filter()`, and `sorted()`.

#### Basic Lambda Example

```python
add = lambda x, y: x + y
print(add(3, 5))  # Output: 8
```

---

#### Lambda with `map()`

```python
numbers = [1, 2, 3, 4]

# Square each number using a lambda (Lesson 3.1)
squared = list(map(lambda x: x ** 2, numbers))

print(squared)  # Output: [1, 4, 9, 16]
```

> 💡 Use lambdas for short, simple logic—avoid complex expressions.

---

## Lesson 3.2: Modules and Packages 📦

Modules are Python files containing reusable code. **Packages** are collections of related modules organized into directories.

---

### Importing Built-in Modules

#### Using the `math` Module

```python
import math

print(math.sqrt(16))  # Output: 4.0
print(math.pi)        # Output: 3.141592653589793
```

---

#### Using the `random` Module

```python
import random

print(random.randint(1, 10))
# Output: A random number between 1 and 10
```

---

### Alias Imports

Aliases shorten long module names.

```python
import numpy as np

print(np.array([1, 2, 3]))
# Output: [1 2 3]
```

---

### Creating and Using Custom Modules

#### Creating a Module (`mymodule.py`)

```python
# File: mymodule.py
def greet(name):
    print(f"Hello, {name}!")
```

---

#### Using the Custom Module

```python
# File: main.py
import mymodule

mymodule.greet("Alice")
# Output: Hello, Alice!
```

---

#### Importing Specific Functions

```python
from mymodule import greet

greet("Bob")
# Output: Hello, Bob!
```

> 💡 Importing only what you need improves readability.

---

## Using pip to Install External Packages 🧰

### What is pip?

`pip` is Python’s package manager for installing third-party libraries.

#### Installing a Package

```bash
pip install requests
```

---

#### Checking Installed Packages

```bash
pip list
```

---

#### Uninstalling a Package

```bash
pip uninstall requests
```

---

#### Using an Installed Package

```python
import requests

response = requests.get("https://api.github.com")
print(response.status_code)
# Output: 200
```

---

## Key Takeaways 🔑

* Functions promote reuse and clarity
* Scope determines where variables are accessible
* Lambdas are concise, one-off functions
* Modules organize code across files
* `pip` extends Python beyond the standard library

---

## Practice Exercises 📝

1. Write a function that calculates the area of a rectangle.
2. Create a function that accepts any number of arguments and returns their average.
3. Write a custom module with at least two functions.
4. Install a third-party package and use one of its functions.

```python
# Exercises for module 3:
"""
1. Write a function that calculates the area of a rectangle.
2. Create a function that accepts any number of arguments and returns their average.
3. Write a custom module with at least two functions.
4. Install a third-party package and use one of its functions.
"""
# Exercise 1:
print("\n\nExercises for module 3")
print("\nExercise 1 - Calculate the area of a rectangle: ")
def rect_area(width, height):
  area = width*height
  print(f"The area of a rectangle with width {width} and height {height} is: "+ str(area))

rect_area(3,5) 
"""
Notice, I could have added a return statement and saved the area with "return area" in the function, and setting rect_area(3,5) equal to something with "rect1 = rect_area(3,5)"

That would look like the following:

def rect_area(width, height):
  area = width*height
  return area

area1 = rect_area(width, height)
print(area1)

# However, this would not produce the nice sentence we have above (The area of the rectangle with width... etc.)
""""


# Exercise 2 - Create a function that accepts any number of arguments and returns their average.:
print("\nExercise 2:\n")
def avg(*args): # Creates a tuple (val1, val2, val3, val4 ....)
  sum1 = 0
  number_of_items = 0

  for arg in args:
    sum1 += arg
    counter += 1

  return sum1/counter

avg1 = avg(3, 4, 5)

# Creates the tuple (3, 4, 5)
  
  # for arg in args
  # loop 1: arg = 3
  # loop 2: arg = 4
  # loop 3: arg = 5

  # sum1 += args
  # loop 1: sum1 = 3
  # loop 2: sum1 = 3 + 4 = 7
  # loop 3: sum1 = 3 + 4 + 5 = 12

  # counter += 1:
  # loop 1: counter = 1
  # loop 2: counter = 2
  # loop 3: counter = 3

"""
We did not demonstrate exercise 3 or 4 due to hardware/software limitations.
"""
```
---

[Next Module - Module 4: Data Structures](./Module%204:%20Data%20Structures.md)
