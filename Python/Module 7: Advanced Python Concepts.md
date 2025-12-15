[Previous Module - Module 6: Object-Oriented Programming (OOP)](./Module%206:%20Object-Oriented%20Programming%20%28OOP%29.md)

⏱️ **Estimated reading time:** ~30 minutes

# Module 7: Advanced Python Concepts 🚀

This module explores powerful Python features that improve **flexibility**, **readability**, and **performance** in real-world applications.

You will learn about:

* **Decorators** for extending function behavior without modifying source code
* **Generators and `yield`** for memory-efficient iteration
* **Working with dates and times** using the `datetime` module
* **Formatting and parsing dates/times** for logging, scheduling, and data processing

Together, these tools help you write cleaner, more scalable, and more Pythonic code.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Explain what decorators are and when to use them
* Create and apply decorators with and without arguments
* Build generators using the `yield` keyword
* Work with dates and times using `datetime` and `timedelta`
* Format and parse date/time values using `strftime()` and `strptime()`

---

## Lesson 7.1: Decorators and Generators

### Using Decorators for Function Enhancement

#### What Is a Decorator?

A **decorator** is a function that wraps another function to extend or modify its behavior **without changing the original function’s code** (Lesson 7.1).

Decorators are applied using the `@decorator_name` syntax.

---

### Basic Decorator Example

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()  # Calls the original function
        print("Something is happening after the function is called.")
    return wrapper
```

```python
@my_decorator
def say_hello():
    print("Hello!")
```

```python
say_hello()
```

```text
# Output:
# Something is happening before the function is called.
# Hello!
# Something is happening after the function is called.
```

> 💡 The decorator adds behavior *before and after* `say_hello()` runs.

---

### Common Decorator Use Cases

* **Logging**: Track function calls
* **Access Control**: Check permissions before execution
* **Timing**: Measure performance
* **Caching (Memoization)**: Store expensive results

---

### Decorators with Arguments

Decorators that accept arguments require an **extra level of nesting**.

```python
def repeat(num_times):
    def decorator_repeat(func):
        def wrapper(*args, **kwargs):
            for _ in range(num_times):
                func(*args, **kwargs)
        return wrapper
    return decorator_repeat
```

```python
@repeat(3)
def greet(name):
    print(f"Hello, {name}!")
```

```python
greet("Alice")
```

```text
# Output:
# Hello, Alice!
# Hello, Alice!
# Hello, Alice!
```

> 💡 This example demonstrates decorators with parameters (Lesson 7.1).

---

## Generators and `yield`

### What Is a Generator?

A **generator** is a special function that returns an iterator and produces values **one at a time** using the `yield` keyword.

* Execution pauses at `yield`
* Resumes where it left off
* Values are generated **lazily**

---

### Basic Generator Example

```python
def countdown(n):
    while n > 0:
        yield n  # Produces a value without ending the function
        n -= 1
```

```python
for num in countdown(5):
    print(num)
```

```text
# Output:
# 5
# 4
# 3
# 2
# 1
```

---

### Why Use Generators?

* **Memory Efficient**: No need to store all values at once
* **Ideal for Large Data**: Files, streams, infinite sequences
* **Pipeline Friendly**: Can chain generators together

---

### Common Generator Use Cases

* Reading large files line by line
* Processing streams of data
* Generating infinite sequences (e.g., Fibonacci numbers)

---

## Lesson 7.2: Working with Dates and Times

### The `datetime` Module

The `datetime` module provides tools for creating, manipulating, and comparing dates and times.

```python
from datetime import datetime, timedelta
```

---

### Creating Date and Time Objects

```python
now = datetime.now()
print(now)  # Output: current date and time
```

```python
birthday = datetime(1990, 7, 15)
print(birthday)
```

---

### Calculating Time Differences

```python
delta = now - birthday
print(f"Days since birth: {delta.days}")
```

> 💡 Subtracting two `datetime` objects returns a `timedelta`.

---

### Using `timedelta`

```python
future_date = now + timedelta(days=7)
print(f"Future date: {future_date}")
```

> 💡 `timedelta` represents a duration, not a specific date.

---

## Formatting Dates and Times

### Converting Dates to Strings (`strftime`)

```python
formatted_date = now.strftime("%A, %B %d, %Y")
print(formatted_date)
```

```text
# Output example:
# Thursday, August 28, 2024
```

> 💡 Formatting is useful for logs, reports, and UI display.

---

### Parsing Strings into Dates (`strptime`)

```python
date_string = "2024-08-28"
parsed_date = datetime.strptime(date_string, "%Y-%m-%d")
print(parsed_date)
```

> 💡 Parsing is essential when reading dates from files or user input.

---

## Key Takeaways 🔑

* Decorators extend function behavior cleanly
* Generators improve performance and memory usage
* `yield` enables lazy iteration
* `datetime` and `timedelta` handle time-based logic
* `strftime()` and `strptime()` convert between strings and dates

---

## Practice Exercises 📝

1. Write a decorator that logs function execution time.
2. Create a generator that yields even numbers indefinitely.
3. Calculate how many days remain until a future date.
4. Parse user-entered dates and format them for display.

---

[Next Module - Module 8: Working with Data (Intro to Data Science)](./Module%208:%20Working%20with%20Data%20%28Intro%20to%20Data%20Science%29.md)
