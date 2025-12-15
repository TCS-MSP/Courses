[Previous Module - Module 4: Data Structures](./Module%204:%20Data%20Structures.md)

# Module 5: File Handling 📁

File handling allows Python programs to **read data from files** and **write data to files** on disk. This is essential for tasks like saving program output, loading configuration data, processing datasets, and interacting with external systems.

In Python, file operations are performed using the built-in `open()` function, which opens a file in a specific **mode** such as reading, writing, or appending.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Open and close files correctly
* Read data from text files using multiple methods
* Write and append data to files
* Safely manage file resources using `with`
* Work with structured data formats like CSV and JSON

---

## Lesson 5.1: Reading and Writing Files

### Opening and Closing Files

The `open()` function opens a file and returns a **file object**, which can then be used to read or write data.

```python
# Open a file in read mode (Lesson 5.1)
file = open("example.txt", "r")
print(file.read())  # Outputs the entire contents of the file
file.close()        # Always close files when done
```

> ⚠️ Forgetting to close files can lead to memory leaks and file locks.

---

### File Modes

| Mode | Meaning                          |
| ---- | -------------------------------- |
| `r`  | Read (default)                   |
| `w`  | Write (overwrites existing file) |
| `a`  | Append (adds to end of file)     |
| `b`  | Binary mode (e.g., images)       |

---

### Best Practice: Using the `with` Statement ✅

The `with` statement automatically closes the file, even if an error occurs.

```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
# File is automatically closed here
```

> 💡 This is the recommended way to work with files in Python.

---

## Reading from Files 📖

Reading from files allows you to work with **external data** stored on disk.

---

### Reading the Entire File: `read()`

```python
with open("example.txt", "r") as file:
    content = file.read()
    print(content)  # Output: full file as a single string
```

---

### Reading One Line at a Time: `readline()`

```python
with open("example.txt", "r") as file:
    line = file.readline()
    
    while line:
        print(line.strip())  # strip() removes newline characters
        line = file.readline()
```

> 💡 Useful for processing large files line by line.

---

### Reading All Lines into a List: `readlines()`

```python
with open("example.txt", "r") as file:
    lines = file.readlines()

    for line in lines:
        print(line.strip())
```

---

## Writing to Files ✍️

Writing allows programs to **persist data** for later use.

---

### Writing Text with `write()`

```python
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("Writing to files in Python.")
```

> ⚠️ Opening a file in `w` mode will overwrite existing contents.

---

### Writing Multiple Lines with `writelines()`

```python
with open("output.txt", "w") as file:
    lines = [
        "First line\n",
        "Second line\n",
        "Third line\n"
    ]
    file.writelines(lines)
```

---

### Appending to Files

```python
with open("output.txt", "a") as file:
    file.write("This line will be appended.\n")
```

> 💡 Append mode preserves existing data.

---

## Working with CSV and JSON 📊

CSV and JSON are common formats for storing and exchanging structured data.

---

### Working with CSV Files

#### Reading CSV Files

```python
import csv

with open("data.csv", "r") as file:
    reader = csv.reader(file)
    
    for row in reader:
        print(row)
        # Output example: ['Alice', '30', 'New York']
```

---

#### Writing CSV Files

```python
import csv

with open("data.csv", "w", newline="") as file:
    writer = csv.writer(file)
    
    writer.writerow(["Name", "Age", "City"])
    writer.writerow(["Alice", 30, "New York"])
```

---

### Working with JSON Files

#### Reading JSON Files

```python
import json

with open("data.json", "r") as file:
    data = json.load(file)
    print(data)
    # Output: {'name': 'Alice', 'age': 30, 'city': 'New York'}
```

---

#### Writing JSON Files

```python
import json

data = {
    "name": "Alice",
    "age": 30,
    "city": "New York"
}

with open("data.json", "w") as file:
    json.dump(data, file, indent=4)
```

> 💡 `indent=4` makes JSON easier to read for humans.

---

## Key Takeaways 🔑

* Files must be opened before reading or writing
* Always close files—or better, use `with`
* Choose the correct file mode (`r`, `w`, `a`)
* CSV is ideal for tabular data
* JSON is ideal for structured, nested data

---

## Practice Exercises 📝

1. Write a program that reads a text file and counts the number of lines.
2. Append user input to a file until the user types `"quit"`.
3. Read a CSV file and print only one column.
4. Save a Python dictionary to a JSON file and load it back.

---

[Next Module - Module 6: Object-Oriented Programming (OOP)](./Module%206:%20Object-Oriented%20Programming%20%28OOP%29.md)
