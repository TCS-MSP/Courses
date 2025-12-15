[Previous Module - Module 8: Working with Data (Intro to Data Science)](./Module%208:%20Working%20with%20Data%20%28Intro%20to%20Data%20Science%29.md)

# Module 9: Working with APIs and Web Scraping 🌐
⏱️ **Estimated reading time:** ~35–40 minutes

This module covers how to access external data using **APIs** and **web scraping**. Both methods allow Python programs to gather information from the web, but APIs are generally more stable and structured, while scraping is a workaround when no API exists.

---

## **Lesson 9.1: Introduction to APIs**

### **1. What are APIs?**

* **Definition:** An API (Application Programming Interface) is a set of rules and tools that allow one software program to interact with another.
* **Use Case:** Accessing data from services like Twitter, GitHub, or weather platforms without directly interacting with their web pages.

### **2. Types of APIs**

* **Web APIs:** Use HTTP to request data from a server.
* **REST (Representational State Transfer):** Popular API style using standard HTTP methods: GET, POST, PUT, DELETE.
* **JSON:** A lightweight, human-readable format for data exchange.

### **3. Example: Accessing a Protected API**

```python
import requests

# Example: Accessing a protected endpoint
headers = {
    "Authorization": "Bearer YOUR_ACCESS_TOKEN"  # Replace YOUR_ACCESS_TOKEN with your API token
}
response = requests.get("https://api.example.com/protected", headers=headers)

print(response.status_code)  # 200 means success
print(response.json())       # JSON response from the API
```

**Notes:**

* `"Bearer"` is the standard prefix for OAuth 2.0 tokens.
* Replace `YOUR_ACCESS_TOKEN` with the token provided by the API service.

---

### **4. Making GET and POST Requests**

* **GET:** Retrieve data.

```python
response = requests.get("https://api.github.com")
print(response.json())
```

* **POST:** Send data.

```python
url = "https://jsonplaceholder.typicode.com/posts"
data = {"title": "foo", "body": "bar", "userId": 1}
response = requests.post(url, json=data)
print(response.status_code)  # 201 means created successfully
```

### **5. Handling Errors**

```python
try:
    response = requests.get("https://api.github.com/invalid")
    response.raise_for_status()
except requests.exceptions.HTTPError as err:
    print(f"HTTP error: {err}")
except Exception as err:
    print(f"Other error: {err}")
```

---

## **Lesson 9.2: Web Scraping**

### **1. Using Beautiful Soup**

**Purpose:** Extract information from HTML when an API is not available.

**Installation:**

```bash
pip install beautifulsoup4 requests
```

**Example:**

```python
from bs4 import BeautifulSoup
import requests

url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.content, "html.parser")

# Extract page title
print(soup.title.text)

# Extract all links
for link in soup.find_all('a'):
    print(link.get('href'))
```

**Extracting Tables:**

```python
table = soup.find('table')
if table:
    for row in table.find_all('tr'):
        data = [col.text for col in row.find_all('td')]
        print(data)
```

---

### **2. Using Scrapy for More Advanced Crawling**

Scrapy is a **framework** for scalable, automated web scraping.

**Step 1: Install Scrapy**

```bash
pip install scrapy
```

**Step 2: Create a Scrapy project**

```bash
scrapy startproject myproject
```

**What this does:**

* Creates a folder `myproject/` **automatically**.
* Inside it:

```
myproject/
├── scrapy.cfg               # Main configuration
├── myproject/               # Python module with same name
│   ├── __init__.py
│   ├── items.py
│   ├── middlewares.py
│   ├── pipelines.py
│   └── spiders/            # Automatically created folder for spiders
```

**Step 3: Add a spider**

* File: `myproject/myproject/spiders/example_spider.py`

```python
import scrapy

class ExampleSpider(scrapy.Spider):
    name = "example"  # Used by `scrapy crawl`
    start_urls = ['https://example.com']

    def parse(self, response):
        yield {'title': response.css('title::text').get()}
```

**Step 4: Run the spider**

```bash
scrapy crawl example
```

**Important Notes:**

* You **do not** include the path to the spider file; Scrapy automatically searches `myproject/myproject/spiders/` for a spider with the matching `name`.
* Multiple spiders can exist; each must have a **unique `name`**.

**Folder example with multiple spiders:**
```
myproject/                 <-- Root folder created by `scrapy startproject myproject`
├── scrapy.cfg             <-- Scrapy configuration file (always at root)
├── myproject/             <-- Python module (same name as project)
│   ├── __init__.py
│   ├── items.py           <-- Define data models (optional)
│   ├── middlewares.py     <-- Custom middlewares (optional)
│   ├── pipelines.py       <-- Data pipelines (optional)
│   └── spiders/           <-- Folder for all spiders
│       ├── __init__.py
│       ├── example_spider.py     <-- Spider named "example"
│       └── weather_spider.py     <-- Another spider named "weather"
```

Run each spider by its name:

```bash
scrapy crawl example
scrapy crawl weather
```

---

### ✅ **Key Takeaways**

1. **APIs** are structured and preferred; use `requests` to GET or POST data.
2. **Beautiful Soup** is great for simple scraping of HTML.
3. **Scrapy** is for larger, scalable scraping projects.

   * `scrapy startproject` creates the folder structure automatically.
   * Spiders live in `myproject/myproject/spiders/`.
   * `scrapy crawl <spider_name>` runs a spider by its unique `name`, not file path.

---

Cogratulations ── this concludes the course!
