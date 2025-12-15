[Previous Module - Module 7: Advanced Python Concepts](./Module%207:%20Advanced%20Python%20Concepts.md)

# Module 8: Working with Data (Intro to Data Science) 📊
⏱️ **Estimated reading time:** ~35–40 minutes

This module introduces **data analysis** and **data visualization** using some of the most widely used Python libraries in data science. You’ll learn how to load, inspect, clean, manipulate, and visualize data—skills that are foundational for analytics, machine learning, and real-world decision making.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Explain what Pandas is and why it’s used
* Work with Pandas **Series** and **DataFrames**
* Clean and manipulate datasets
* Perform basic aggregations and grouping
* Create common plots using **Matplotlib** and **Seaborn**
* Understand when to use different plot types

---

## Lesson 8.1: Data Analysis with Pandas

### Introduction to Pandas

**Pandas** is a powerful Python library designed for **data manipulation and analysis**. It provides high-level data structures that make working with structured data fast and intuitive.

Core data structures:

* **Series** → 1D labeled array
* **DataFrame** → 2D table (rows + columns)

#### Installing Pandas

```bash
pip install pandas
```

---

### DataFrames and Series

#### Pandas Series

A **Series** is a one-dimensional array with an index (Lesson 8.1).

```python
import pandas as pd

data = [10, 20, 30]
s = pd.Series(data, index=["a", "b", "c"])
print(s)
```

```text
# Output:
# a    10
# b    20
# c    30
# dtype: int64
```

---

#### Pandas DataFrames

A **DataFrame** is a two-dimensional, table-like data structure.

```python
data = {
    "Name": ["Alice", "Bob", "Charlie"],
    "Age": [25, 30, 35],
    "City": ["New York", "Los Angeles", "Chicago"]
}

df = pd.DataFrame(data)
print(df)
```

```text
# Output:
#       Name  Age         City
# 0    Alice   25     New York
# 1      Bob   30  Los Angeles
# 2  Charlie   35      Chicago
```

---

### Accessing Data

#### Selecting Columns

```python
print(df["Name"])
```

```text
# Output:
# 0      Alice
# 1        Bob
# 2    Charlie
# Name: Name, dtype: object
```

#### Selecting Rows

```python
print(df.loc[0])   # Select by label
print(df.iloc[1])  # Select by index position
```

> 💡 `.loc` is label-based, `.iloc` is position-based.

---

### Data Cleaning and Manipulation

Data cleaning and manipulation turn **raw data into usable insights**.

---

#### Handling Missing Data

```python
df["Age"].fillna(df["Age"].mean(), inplace=True)
```

> 💡 This replaces missing values with the column’s mean (Lesson 8.1).

---

#### Filtering Rows

```python
adults = df[df["Age"] > 30]
print(adults)
```

```text
# Output:
#       Name  Age     City
# 2  Charlie   35  Chicago
```

---

#### Sorting Data

```python
sorted_df = df.sort_values(by="Age")
print(sorted_df)
```

---

#### Aggregations and Grouping

```python
grouped = df.groupby("City").mean()
print(grouped)
```

> 💡 `groupby()` is commonly used for summarizing datasets.

---

## Lesson 8.2: Data Visualization

### Introduction to Matplotlib and Seaborn

* **Matplotlib**: Core plotting library for Python
* **Seaborn**: High-level statistical visualization library built on Matplotlib

#### Installing Visualization Libraries

```bash
pip install matplotlib seaborn
```

---

## Creating Basic Plots

> 📌 All plots below will display when run locally or in Jupyter Notebook.

---

### Line Plot (Trends Over Time)

```python
import matplotlib.pyplot as plt

x = [0, 1, 2, 3, 4]
y = [0, 1, 4, 9, 16]

plt.plot(x, y)
plt.title("Line Plot Example")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.show()
```

> 💡 Line plots are commonly used for trends and time-series data.

---

### Bar Plot (Categorical Comparison)

```python
categories = ["A", "B", "C"]
values = [5, 7, 3]

plt.bar(categories, values)
plt.title("Bar Plot Example")
plt.show()
```

> 💡 Bar plots compare quantities across categories.

---

### Scatter Plot (Relationships Between Variables)

```python
import seaborn as sns

tips = sns.load_dataset("tips")
sns.scatterplot(data=tips, x="total_bill", y="tip")
plt.title("Scatter Plot Example")
plt.show()
```

> 💡 Scatter plots reveal correlations and patterns.

---

### Histogram (Distribution)

```python
plt.hist(tips["total_bill"], bins=20)
plt.title("Histogram Example")
plt.xlabel("Total Bill")
plt.ylabel("Frequency")
plt.show()
```

> 💡 Histograms show how data is distributed.

---

### Box Plot (Statistical Summary)

```python
sns.boxplot(x=tips["total_bill"])
plt.title("Box Plot Example")
plt.show()
```

> 💡 Box plots highlight medians, quartiles, and outliers.

---

## Key Takeaways 🔑

* Pandas is the backbone of data analysis in Python
* DataFrames and Series simplify data handling
* Cleaning data is critical before analysis
* Grouping and aggregation reveal insights
* Matplotlib and Seaborn visualize patterns effectively
* Choosing the right plot matters

---

## Practice Exercises 📝

1. Load a CSV file into a DataFrame and inspect it.
2. Filter rows based on multiple conditions.
3. Group data by a category and calculate averages.
4. Create at least three different plot types from the same dataset.
5. Experiment with Seaborn styling options.

---

[Next Module - Module 9: Working with APIs and Web Scraping](./Module%209:%20Working%20with%20APIs%20and%20Web%20Scraping.md)
