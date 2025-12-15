[Previous Module - Module 8: Working with Data (Intro to Data Science)](./Module%208:%20Working%20with%20Data%20%28Intro%20to%20Data%20Science%29.md)

⏱️ **Estimated reading time:** ~35–40 minutes

# Module 9: Working with APIs and Web Scraping 🌐

This module covers how to **access data from external sources**, either via **APIs** or by **scraping websites**. These are essential skills for real-world data gathering when datasets are not directly available.

---

## Learning Objectives 🎯

By the end of this module, you should be able to:

* Explain what APIs are and why they are used
* Work with REST APIs using Python’s `requests` library
* Understand API responses, status codes, and authentication
* Parse HTML content with **Beautiful Soup**
* Use **Scrapy** to build scalable web crawlers
* Decide when to use APIs vs web scraping

---

## Lesson 9.1: Introduction to APIs

### What are APIs?

* **API (Application Programming Interface):** A set of rules that allows software applications to communicate with each other.
* **Web APIs:** Access data/services over the web using HTTP.
* **REST APIs:** Use HTTP methods (GET, POST, PUT, DELETE) for CRUD operations.
* **JSON:** Common format for data exchange between client and server.

**Examples of APIs:**

* Social media (Twitter, Instagram)
* Weather (OpenWeatherMap)
* Finance (stocks, currency rates)

---

### Working with REST APIs using `requests`

#### Installation

```bash
pip install requests
```

---

#### Making GET Requests

```python
import requests

response = requests.get("https://api.github.com")
print(response.status_code)  # 200 if successful
print(response.json())       # JSON response content
```

---

#### Making POST Requests

```python
url = "https://jsonplaceholder.typicode.com/posts"
data = {
    "title": "foo",
    "body": "bar",
    "userId": 1
}

response = requests.post(url, json=data)
print(response.status_code)  # 201 if created successfully
print(response.json())
```

---

#### Handling API Responses

```python
try:
    response = requests.get("https://api.github.com/invalid")
    response.raise_for_status()  # Raises HTTPError for bad responses
except requests.exceptions.HTTPError as err:
    print(f"HTTP error occurred: {err}")
except Exception as err:
    print(f"Other error occurred: {err}")
```

---

#### Authentication with APIs

```python
headers = {"Authorization": "Bearer YOUR_ACCESS_TOKEN"}
response = requests.get("https://api.example.com/protected", headers=headers)
```

> 💡 Many APIs require keys or tokens for secure access.

---

## Lesson 9.2: Web Scraping with Beautiful Soup and Scrapy

### Parsing HTML with Beautiful Soup

**Installation:**

```bash
pip install beautifulsoup4 requests
```

---

#### Basic HTML Parsing

```python
from bs4 import BeautifulSoup
import requests

url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.content, "html.parser")

title = soup.title.text
print(title)
```

---

#### Navigating the Parse Tree

```python
# Finding first paragraph
first_paragraph = soup.find('p')
print(first_paragraph.text)

# Finding all links
links = soup.find_all('a')
for link in links:
    print(link.get('href'))
```

---

#### Extracting Table Data

```python
table = soup.find('table')
if table:
    rows = table.find_all('tr')
    for row in rows:
        cols = row.find_all('td')
        data = [col.text for col in cols]
        print(data)
```

---

### Scraping Data with Scrapy

**Installation:**

```bash
pip install scrapy
```

---

#### Creating a Scrapy Project

```bash
scrapy startproject myproject
```

---

#### Creating a Simple Spider

```python
# myproject/spiders/example_spider.py
import scrapy

class ExampleSpider(scrapy.Spider):
    name = "example"
    start_urls = ['https://example.com']

    def parse(self, response):
        title = response.css('title::text').get()
        yield {'title': title}
```

---

#### Running a Scrapy Spider

```bash
scrapy crawl example
```

---

#### Scrapy Pipelines

* Pipelines process and store scraped data.
* Can clean data, save to databases, or export to files.

---

#### Handling Requests and Responses

* Scrapy supports headers, cookies, and user agents.
* Helps avoid detection as a bot.

---

## Key Takeaways 🔑

* **APIs** are the preferred method to access structured data.
* **Web scraping** is a workaround when APIs are unavailable, but is more fragile.
* `requests` simplifies HTTP interactions in Python.
* Beautiful Soup is excellent for parsing and extracting HTML content.
* Scrapy is ideal for large-scale, automated web scraping projects.

---

## Practice Exercises 📝

1. Use a public API (like OpenWeatherMap) to fetch and display JSON data.
2. Parse a webpage to extract all headlines or links using Beautiful Soup.
3. Build a simple Scrapy spider to scrape titles from a website.
4. Combine API and web scraping data to create a mini dataset.

---

This concludes the Python course modules! 🎓
