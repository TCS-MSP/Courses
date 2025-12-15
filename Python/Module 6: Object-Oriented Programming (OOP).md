[Previous Module - Module 5: File Handling](./Module%205:%20File%20Handling.md)

⏱️ **Estimated reading time:** ~35 minutes

# Module 6: Object-Oriented Programming (OOP) 🧱

Object-Oriented Programming (OOP) is a programming paradigm that organizes code around **objects**, which bundle **data (attributes)** and **behavior (methods)** together. In Python, OOP is built around defining **classes** and creating **objects** from those classes.

OOP helps you write code that is:

* Modular
* Reusable
* Easier to reason about as projects grow

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Explain the difference between classes and objects
* Define classes with attributes and methods
* Use constructors to initialize objects
* Apply inheritance and polymorphism
* Understand encapsulation and abstraction in Python

---

## Lesson 6.1: Introduction to OOP

### Classes and Objects

A **class** is a blueprint for creating objects.
An **object** is an instance of a class.

* Classes define *what an object knows* (attributes)
* Classes define *what an object can do* (methods)

---

### Creating a Class

```python
class Dog:
    def __init__(self, name, breed):
        self.name = name    # Attribute: unique to each Dog object
        self.breed = breed

    def bark(self):
        # Method: behavior shared by all Dog objects
        print(f"{self.name} says Woof!")
```

* `__init__` is the constructor (Lesson 6.1)
* `self` refers to the current object

---

### Creating Objects (Instantiation)

```python
my_dog = Dog("Rex", "Labrador")  # Create a Dog object
my_dog.bark()                   # Output: Rex says Woof!
```

> 💡 Each object has its own data but shares the same methods.

---

## Methods and Constructors

### Methods

Methods are functions defined inside a class and operate on object data.

```python
class Circle:
    def __init__(self, radius):
        self.radius = radius  # Instance attribute

    def area(self):
        # Uses the object's own data (Lesson 6.1)
        return 3.14 * self.radius ** 2
```

---

### Constructors (`__init__`)

The constructor initializes a new object when it is created.

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        print(f"Hello, my name is {self.name} and I am {self.age} years old.")
```

```python
person = Person("Alice", 30)
person.greet()
# Output: Hello, my name is Alice and I am 30 years old.
```

> 💡 Constructors ensure objects start in a valid state.

---

## Lesson 6.2: Advanced OOP Concepts

### Inheritance 🧬

Inheritance allows a **child class** to reuse and extend a **parent class**.

* Parent (base) class → shared behavior
* Child (derived) class → specialized behavior

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        pass  # Intended to be overridden
```

```python
class Dog(Animal):
    def speak(self):
        return f"{self.name} barks."
```

```python
class Cat(Animal):
    def speak(self):
        return f"{self.name} meows."
```

```python
dog = Dog("Buddy")
cat = Cat("Whiskers")

print(dog.speak())  # Output: Buddy barks.
print(cat.speak())  # Output: Whiskers meows.
```

> 💡 `pass` is often used as a placeholder in base classes.

---

### Polymorphism 🔁

Polymorphism allows different objects to respond to the **same method name** in different ways.

```python
class Bird:
    def fly(self):
        print("Most birds can fly.")
```

```python
class Penguin(Bird):
    def fly(self):
        print("Penguins cannot fly.")
```

```python
birds = [Bird(), Penguin()]

for bird in birds:
    bird.fly()
```

```text
# Output:
# Most birds can fly.
# Penguins cannot fly.
```

> 💡 Polymorphism enables flexible, reusable code.

---

### Encapsulation and Abstraction 🔒

#### Encapsulation

Encapsulation bundles data and behavior together and discourages direct access to internal state.

* `_protected` → convention (internal use)
* `__private` → name-mangled (harder to access)

> ⚠️ Python does not enforce true privacy—this is a **developer convention**.

```python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance  # Private attribute (Lesson 6.2)

    def deposit(self, amount):
        self.__balance += amount
        print(f"Deposited {amount}, new balance is {self.__balance}")

    def withdraw(self, amount):
        if amount <= self.__balance:
            self.__balance -= amount
            print(f"Withdrew {amount}, new balance is {self.__balance}")
        else:
            print("Insufficient funds")
```

---

#### Abstraction

Abstraction hides implementation details and exposes **only what the user needs to know**.

* Users interact with methods
* Internal logic can change without breaking external code

> 💡 Abstraction reduces cognitive load and improves maintainability.

---

## Key Takeaways 🔑

* Classes define structure; objects represent real instances
* Constructors initialize object state
* Inheritance enables code reuse
* Polymorphism allows flexible behavior
* Encapsulation and abstraction manage complexity

---

## Practice Exercises 📝

1. Create a class representing a `Car` with attributes and methods.
2. Implement inheritance with a base `Employee` class and subclasses.
3. Demonstrate polymorphism using a list of different objects.
4. Add private attributes to protect internal data.

---

[Next Module - Module 7: Advanced Python Concepts](./Module%207:%20Advanced%20Python%20Concepts.md)
