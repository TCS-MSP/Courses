[Previous Module - Module 3: Functions and Modules](./Module%203:%20Functions%20and%20Modules.md)

# Module 4: Data Structures 🧺
⏱️ **Estimated reading time:** ~30 minutes

Data structures are ways to **store, organize, and manage data efficiently**. Python provides several powerful built-in data structures—**lists, tuples, sets, and dictionaries**—each designed for different use cases and access patterns.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Create and manipulate lists, tuples, sets, and dictionaries
* Choose the appropriate data structure for a given problem
* Use list comprehensions for concise data transformations
* Perform common set operations
* Work effectively with key-value pairs in dictionaries

---

## Lesson 4.1: Lists, Tuples, and Sets

Python provides multiple ways to store collections of items:

* **Lists** → ordered, mutable, allow duplicates
* **Tuples** → ordered, immutable
* **Sets** → unordered, mutable, no duplicates

Understanding when to use each one is critical.

---

### Defining and Manipulating Lists

#### What is a List?

A list is an **ordered, mutable collection** that allows duplicate elements.

#### Creating Lists

```python
# Using square brackets (Lesson 4.1)
fruits = ["apple", "banana", "cherry"]
```

```python
# Using the list() function
numbers = list(range(5))
print(numbers)  # Output: [0, 1, 2, 3, 4]
```

---

#### Accessing Elements

```python
print(fruits[0])    # Output: apple (first element)
print(fruits[-1])   # Output: cherry (last element)
print(fruits[1:3])  # Output: ['banana', 'cherry'] (slice)
```

> 💡 Lists support both positive and negative indexing.

---

#### Modifying Lists

##### Adding Elements

```python
fruits.append("orange")              # Adds to the end
fruits.insert(1, "kiwi")             # Inserts at index 1
fruits.extend(["mango", "pear"])     # Adds multiple items
```

##### Removing Elements

```python
fruits.remove("banana")  # Removes first occurrence
popped = fruits.pop()    # Removes and returns last item
del fruits[0]            # Deletes element at index 0
```

---

#### Sorting and Reversing Lists

```python
numbers = [3, 1, 4, 1, 5]

numbers.sort()      # Sorts list in place (ascending)
numbers.reverse()   # Reverses list in place

print(sorted(numbers))  # Returns a sorted copy
print(numbers)          # Output: [5, 4, 3, 1, 1]
```

> ⚠️ `.sort()` and `.reverse()` modify the original list
> ✅ `sorted()` returns a new list and leaves the original unchanged

---

#### Common List Methods

```python
numbers = [1, 2, 2, 3]

print(numbers.index(2))  # Output: 1
print(numbers.count(2))  # Output: 2

numbers.clear()
print(numbers)           # Output: []
```

---

### List Comprehensions ⚡

List comprehensions provide a **concise and readable** way to create lists.

#### General Syntax

```python
[expression for item in iterable if condition]
```

---

#### Basic Example

```python
squares = [x ** 2 for x in range(10)]
print(squares)
# Output: [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

---

#### With a Condition

```python
even_numbers = [x for x in range(20) if x % 2 == 0]
print(even_numbers)
# Output: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

> 💡 List comprehensions replace many multi-line `for` loops.

---

### Tuples vs. Lists

| Feature     | List                 | Tuple                 |
| ----------- | -------------------- | --------------------- |
| Mutability  | Mutable              | Immutable             |
| Syntax      | `[1, 2, 3]`          | `(1, 2, 3)`           |
| Use Case    | Data that may change | Fixed, read-only data |
| Performance | Slightly slower      | Slightly faster       |

---

#### Creating Tuples

```python
coordinates = (10.0, 20.0)
point = 1, 2, 3  # Parentheses optional
```

#### Accessing Tuple Elements

```python
print(coordinates[0])  # Output: 10.0
```

---

#### Tuple Use Cases

##### Swapping Values

```python
a, b = 5, 10
a, b = b, a

print(a, b)  # Output: 10 5
```

##### Returning Multiple Values from a Function

```python
def divide(x, y):
    # Returns quotient and remainder (Lesson 4.1)
    return x // y, x % y

quotient, remainder = divide(10, 3)
print(quotient, remainder)  # Output: 3 1
```

---

### Set Operations 🔢

Sets are ideal for **membership tests** and **removing duplicates**.

#### Creating Sets

```python
colors = {"red", "green", "blue"}
unique_numbers = set([1, 2, 2, 3, 4])

print(unique_numbers)  # Output: {1, 2, 3, 4}
```

---

#### Adding and Removing Elements

```python
colors.add("yellow")
colors.remove("red")
```

---

#### Common Set Operations

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}
```

##### Union

```python
print(set1.union(set2))  # Output: {1, 2, 3, 4, 5}
print(set1 | set2)       # Same result using | operator
```

##### Intersection

```python
print(set1.intersection(set2))  # Output: {3}
print(set1 & set2)
```

##### Difference

```python
print(set1.difference(set2))  # Output: {1, 2}
print(set1 - set2)
```

##### Symmetric Difference

```python
print(set1.symmetric_difference(set2))  # Output: {1, 2, 4, 5}
print(set1 ^ set2)
```

---

## Lesson 4.2: Dictionaries 🗂️

Dictionaries store data as **key-value pairs**, enabling fast lookups and flexible data modeling.

---

### Creating and Accessing Dictionaries

```python
# Dictionary with keys and values (Lesson 4.2)
student = {
    "name": "Alice",
    "age": 25,
    "grades": [88, 92, 85]
}
```

> ⚠️ Keys must be unique—later duplicates overwrite earlier values.

---

#### Using `dict()`

```python
person = dict(name="Bob", age=30)
```

---

#### Accessing and Modifying Values

```python
print(student["name"])  # Output: Alice

student["age"] = 26     # Modify existing value
student["major"] = "Computer Science"  # Add new key
```

---

### Dictionary Methods

```python
print(student.keys())
# Output: dict_keys(['name', 'age', 'grades', 'major'])

print(student.values())
# Output: dict_values([...])

for key, value in student.items():
    print(key, value)
```

---

#### Safe Access with `get()`

```python
print(student.get("age", "Not found"))     # Output: 26
print(student.get("height", "Not found"))  # Output: Not found
```

---

#### Updating and Removing Entries

```python
student.update({"gpa": 3.8})
removed_age = student.pop("age")
```

---

### Working with Key-Value Pairs

```python
student = {"name": "Alex", "age": 21, "grade": "A"}

for key, value in student.items():
    print(f"{key}: {value}")
```

```python
if "name" in student:
    print("Name exists in the dictionary.")
```

---

## Key Takeaways 🔑

* Lists are flexible and widely used
* Tuples protect data from modification
* Sets eliminate duplicates and support mathematical operations
* Dictionaries enable fast, meaningful data access
* Choosing the right data structure matters

---

## Practice Exercises 📝

1. Create a list of numbers and remove duplicates using a set.
2. Write a function that returns both the minimum and maximum values from a list.
3. Convert a list of tuples into a dictionary.
4. Use a dictionary to count word occurrences in a sentence.

```python
# Exercise 4: Use a dictionary to count word occurrences in a sentence.
sentence = "The little man with the blue car chased the blue pelican to the blue ocean with a blue sky into the blue sea"

split_sent = sentence.lower().split(' ') # .lower() puts in lowercase ('The' treated same as 'the');
# .split() separates words and puts each word in a list
# print(split_sent)

new_dict = {}
for word in split_sent:
  if word in new_dict: # If the word is already in the dictionary, increment its number of occurrences
    new_dict[word] += 1
  else: # If the word doesn't exist, add it to the dictionary with value one
    new_dict[word] = 1
print(new_dict)
```

---
[Next Module - Module 5: File Handling](./Module%205:%20File%20Handling.md)
