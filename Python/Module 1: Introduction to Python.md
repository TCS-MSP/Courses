# Module 1: Introduction to Python 🐍
⏱️ **Estimated reading time:** ~20 minutes

This module lays the foundation for the entire course. We’ll introduce the core ideas behind programming and the Python language, focusing on *readability*, *clarity*, and *learning by doing*. By the end of this module, you’ll be able to read, write, and understand simple Python programs—and more importantly, feel comfortable experimenting.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

- Explain what Python is and where it’s commonly used
- Set up a working Python development environment
- Write and run basic Python programs
- Use variables, data types, and operators correctly
- Read Python code and understand what it’s doing

---

## Lesson 1.1: Introduction to Programming and Python

### What is Python?

Python is a **high-level**, **interpreted**, and **general-purpose** programming language designed with simplicity and readability in mind. Python allows you to focus on *what* you want to do, rather than *how* the computer does it.

#### Key Features ✨
- Easy-to-read, English-like syntax
- Cross-platform (Windows, macOS, Linux)
- Extensive standard library
- Open-source and free
- Supports multiple programming paradigms:
  - Procedural
  - Object-oriented
  - Functional

#### Common Use Cases 🧠
- **Web Development**: Django, Flask
- **Data Science**: Pandas, NumPy, Matplotlib
- **Machine Learning**: TensorFlow, PyTorch
- **Automation**: Scripts for repetitive tasks
- **Game Development**: Pygame

> 💡 Python is often called a “glue language” because it connects systems, libraries, and tools together efficiently.

---

### History and Evolution of Python

- **Creator**: Guido van Rossum
- **Origins**: Late 1980s
- **Design Goal**: Code that is easy to read and easy to maintain

#### Python 2 vs Python 3 ⚠️
- Python 2 reached end-of-life in **2020**
- Python 3 introduced:
  - Better Unicode support
  - Clearer syntax decisions
  - Improved libraries

> ✅ **This course uses Python 3 exclusively**

#### Community and Growth 🌍
Python’s growth is driven by:
- A massive open-source community
- Continuous improvement via PEPs (Python Enhancement Proposals)
- Strong support in academia and industry

---

### Python vs Other Programming Languages

| Language     | Strengths                         | Trade-offs                     |
|--------------|----------------------------------|--------------------------------|
| Python       | Readability, rapid development   | Slower than compiled languages |
| Java         | Performance, enterprise use      | Verbose syntax                 |
| C++          | Low-level control, speed         | Complex syntax                 |
| JavaScript   | Web-first, event-driven          | Inconsistent environments      |

#### Why Python for Beginners?
- Minimal syntax overhead
- Immediate feedback
- Large ecosystem of learning resources

---

### Setting Up the Python Environment ⚙️

#### Installing Python
- Download from the official Python website
- Ensure **“Add Python to PATH”** is checked during installation

#### Popular IDEs & Tools 🛠️
- **VS Code**: Lightweight, extensible (recommended)
- **PyCharm**: Full-featured IDE
- **Jupyter Notebook**: Great for data exploration
- **IDLE**: Comes bundled with Python

#### Virtual Environments
Virtual environments keep project dependencies isolated:

```bash
python -m venv venv
source venv/bin/activate  # macOS / Linux
venv\Scripts\activate     # Windows
````

> 💡 You’ll use virtual environments throughout this course.

---

## Lesson 1.2: Basics of Python

### Python Syntax and Structure

Python code is designed to be **readable first**.

#### Key Rules 📏

* Indentation defines code blocks
* No curly braces `{}` required
* One statement per line (typically)

```python
# Indentation defines the block
if True:
    print("This runs")
```

> ⚠️ Incorrect indentation will raise an error.

---

### Writing Your First Python Program

Let’s start with the classic example:

```python
# This is your first Python program
print("Hello, World!")
```

#### Running the Program ▶️

* From the terminal:

  ```bash
  python hello.py
  ```
* Or directly inside your IDE

#### Understanding Output

* `print()` sends text to standard output
* Errors are displayed separately with helpful messages

---

### Comments and Documentation

Comments explain *why* code exists, not just *what* it does.

#### Single-Line Comments

```python
# This is a single-line comment
x = 10
```

#### Multi-Line Comments / Docstrings

```python
"""
This is a multi-line string often used
as documentation.
"""
```

#### Docstrings 📘

Used to document functions, classes, and modules:

```python
def greet(name):
    """Return a friendly greeting."""
    return f"Hello, {name}"
```

> 💡 Good documentation is a professional superpower.

---

## Lesson 1.3: Variables, Data Types, and Operators

### Variables and Constants

Variables store data in memory.

```python
age = 25
name = "Alice"
```

#### Naming Conventions 📝

* Must start with a letter or underscore
* Case-sensitive
* Use `snake_case` for variables

#### Constants

Python doesn’t enforce constants, but conventions matter:

```python
PI = 3.14159
MAX_USERS = 100
```

---

### Basic Data Types

#### Numbers 🔢

```python
integer_number = 10
float_number = 3.14
```

#### Strings 🧵

```python
message = "Hello"
full_message = message + " World"
```

#### Booleans ✅❌

```python
is_logged_in = True
is_admin = False
```

---

### Operators

#### Arithmetic Operators

```python
a = 10
b = 3

print(a + b)   # Addition
print(a - b)   # Subtraction
print(a * b)   # Multiplication
print(a / b)   # Division
print(a // b)  # Floor division
print(a % b)   # Modulus
print(a ** b)  # Exponentiation
```

#### Comparison Operators

```python
print(a == b)
print(a != b)
print(a > b)
print(a <= b)
```

#### Logical Operators

```python
is_adult = age >= 18
has_id = True

print(is_adult and has_id)
print(is_adult or has_id)
print(not has_id)
```

> 💡 These operators will become critical in control flow (next module).

---

## Key Takeaways 🔑

* Python prioritizes readability and simplicity
* Indentation is syntactically meaningful
* Variables store data of different types
* Operators allow you to manipulate and compare values

---

## Practice Exercises 📝

1. Write a program that prints your name and age.
2. Create two numbers and display all arithmetic operations between them.
3. Write a short function with a docstring.

---

## What’s Next? 🚀

In **Module 2**, we’ll explore **control structures**—how to make decisions and repeat actions using:

* `if / elif / else`
* `for` and `while` loops
* Error handling with `try / except`
  
[Next Module - Module 2: Control Structures](./Module%202%3A%20Control%20Structures.md)
