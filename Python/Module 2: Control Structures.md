[Previous Module - Module 1: Introduction to Python](./Module%201:%20Introduction%20to%20Python.md)

# Module 2: Control Structures 🔀
⏱️ **Estimated reading time:** ~25 minutes

Control structures allow a program to **make decisions**, **repeat actions**, and **handle errors gracefully**. Without them, programs would run top-to-bottom with no flexibility. This module introduces the core tools that make Python programs dynamic and responsive.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Use conditional statements to control program flow
* Write `for` and `while` loops to repeat actions
* Control loops using `break`, `continue`, and `pass`
* Handle runtime errors using `try` and `except`
* Write programs that fail safely instead of crashing

---

## Lesson 2.1: Conditional Statements

Conditional statements allow your program to **choose different paths** based on whether a condition evaluates to `True` or `False`.

### if, elif, and else Statements

#### The `if` Statement

The `if` statement runs code **only when a condition is true**.

```python
num = 10

# Check if the number is positive
if num > 0:
    print("The number is positive.")
```

> 💡 Conditions are expressions that evaluate to `True` or `False`.

---

#### The `elif` Statement

Use `elif` (“else if”) when **multiple conditions** need to be checked in order.

```python
score = 75

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
else:
    print("Grade: C")
```

* Conditions are evaluated **top to bottom**
* The first matching condition wins

---

#### The `else` Statement

The `else` block runs when **none of the previous conditions** are true.

```python
num = 0

if num > 0:
    print("Positive")
elif num < 0:
    print("Negative")
else:
    print("Zero")
```

> ⚠️ An `else` block is optional, but often improves clarity.

---

### Nested Conditions

A **nested condition** is an `if` statement placed inside another conditional block.

#### When to Use Nested Conditions

* When a second decision depends on the first
* When modeling real-world decision trees

```python
x = 4
y = 11

if x > 5:
    if y > 15:
        print("Both conditions are met.")
    else:
        print("Only x condition is met.")
```

> 💡 Nesting increases complexity—use it thoughtfully.

---

## Lesson 2.2: Loops 🔁

Loops allow a program to **repeat a block of code multiple times**. They are essential for working with collections, automating tasks, and processing data.

Python provides two main loop types:

* `for` loops → iterate over sequences
* `while` loops → repeat while a condition remains true

---

### for Loop

#### Overview

A `for` loop runs once for **each item in a sequence** such as a list, string, or range.

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
```

* `fruit` is the loop variable
* Each iteration assigns the next value from the sequence

---

#### Using `range()`

The `range()` function generates a sequence of numbers.

```python
for i in range(5):
    print(i)  # Prints 0 through 4
```

Common patterns:

* `range(5)` → 0 to 4
* `range(1, 6)` → 1 to 5
* `range(0, 10, 2)` → even numbers

---

#### for Loop with `else`

The `else` block runs **only if the loop completes without a `break`**.

```python
for i in range(3):
    print(i)
else:
    print("Loop completed normally.")
```

> 💡 This is useful when searching for items.

---

### while Loop

#### Overview

A `while` loop repeats as long as a condition remains `True`.

```python
count = 10

while count < 15:
    print(count)
    count += 2
```

* Be sure the condition eventually becomes `False`
* Otherwise, you’ll create an infinite loop

---

#### Infinite Loop with `break`

Sometimes infinite loops are intentional, with a controlled exit.

```python
while True:
    num = int(input("Enter a number (0 to quit): "))
    
    if num == 0:
        break  # Exit the loop
    
    print("You entered:", num)
```

> ⚠️ Always ensure there is a clear exit condition.

---

### Loop Control Statements

#### break

Immediately exits the loop.

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

---

#### continue

Skips the current iteration and moves to the next one.

```python
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)
```

---

#### pass

A placeholder statement that does nothing.

```python
for i in range(5):
    if i == 3:
        pass  # Placeholder for future logic
    print(i)
```

> 💡 `pass` is often used when sketching program structure.

---

## Lesson 2.3: Error Handling ⚠️

Error handling allows programs to respond gracefully to problems instead of crashing. Python uses **exceptions** to represent runtime errors.

---

### try, except, and finally

#### Overview

* `try`: Code that might raise an error
* `except`: Code that runs if an error occurs
* `finally`: Code that always runs

```python
try:
    num = int(input("Enter a number: "))
    print(10 / num)
except ZeroDivisionError:
    print("Cannot divide by zero!")
except ValueError:
    print("Invalid input! Please enter a number.")
finally:
    print("Execution completed.")
```

> 💡 Catch specific exceptions whenever possible.

---

### Handling Specific Exceptions

Different errors require different responses.

```python
try:
    file = open("non_existent_file.pdf", "r")
except FileNotFoundError:
    print("File not found!")
except IOError:
    print("Error reading the file!")
```

#### Why This Matters

* Prevents program crashes
* Improves user experience
* Makes debugging easier

---

## Key Takeaways 🔑

* Conditional statements control decision-making
* Loops automate repetition
* Loop control statements fine-tune execution
* Exceptions allow safe error handling

---

## Practice Exercises 📝

1. Write a program that checks if a number is even or odd.
2. Use a `for` loop to print numbers from 1 to 100.
3. Write a loop that stops when the user enters `"quit"`.
4. Add error handling to safely divide two numbers.

---

## What’s Next? 🚀

In **Module 3**, we’ll learn how to:

* Write reusable code with **functions**
* Organize code using **modules and packages**
* Extend Python using third-party libraries

[Next Module - Module 3: Functions and Modules](./Module%203:%20Functions%20and%20Modules.md)
