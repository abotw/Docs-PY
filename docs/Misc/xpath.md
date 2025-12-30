# XPath: Overview

## 1. What Is XPath?

**XPath (XML Path Language)** is a query language used to **locate elements in HTML/XML documents**.

In Python web crawling, XPath is commonly used with libraries like:

-   **lxml** (most popular & powerful)
-   **Scrapy** (built on lxml)
-   **parsel** (Scrapy selector)

XPath allows you to **precisely extract data** such as:

-   Titles
-   Links
-   Images
-   Prices
-   Tables
-   Any structured content in a web page

------

## 2. Why Use XPath Instead of Regex?

| Feature         | XPath       | Regex     |
| --------------- | ----------- | --------- |
| Structured HTML | ✅ Excellent | ❌ Poor    |
| Readability     | ✅ Clear     | ❌ Hard    |
| Maintenance     | ✅ Easy      | ❌ Fragile |
| Nested elements | ✅ Strong    | ❌ Weak    |

👉 **Rule of thumb**:
Use **XPath** for HTML structure, **Regex** only for plain text.

------

## 3. Basic Python Setup

### Install Required Library

```bash
pip install lxml
```

### Minimal Example

```python
from lxml import etree

html = """
<html>
    <body>
        <h1>Hello XPath</h1>
        <a href="https://example.com">Example</a>
    </body>
</html>
"""

tree = etree.HTML(html)
```

------

## 4. XPath Basic Syntax

### 4.1 Absolute vs Relative Path

| Expression      | Meaning              |
| --------------- | -------------------- |
| `/html/body/h1` | Absolute path        |
| `//h1`          | Anywhere in document |

```python
tree.xpath('//h1/text()')
```

------

### 4.2 Selecting Elements

| XPath     | Description          |
| --------- | -------------------- |
| `//a`     | All `<a>` elements   |
| `//div/p` | `<p>` inside `<div>` |
| `//*`     | All elements         |

------

## 5. Extracting Text and Attributes

### 5.1 Extract Text

```python
tree.xpath('//h1/text()')
```

Result:

```python
['Hello XPath']
```

------

### 5.2 Extract Attributes

```python
tree.xpath('//a/@href')
```

Result:

```python
['https://example.com']
```

------

## 6. Using Conditions (Very Important)

### 6.1 By Attribute Value

```python
//a[@href]
//a[@class="nav"]
```

------

### 6.2 `contains()` (Most Used)

```python
//a[contains(@href, "example")]
//div[contains(@class, "content")]
```

------

### 6.3 Multiple Conditions

```python
//a[contains(@href, "news") and contains(@class, "item")]
```

------

## 7. Position and Indexing

⚠️ XPath index starts from **1**, not 0.

```python
//li[1]      # first
//li[last()] # last
//li[position() <= 3]
```

Example:

```python
tree.xpath('//li[1]/text()')
```

------

## 8. Parent, Child, and Sibling Axes

### 8.1 Parent Node

```python
//span/parent::div
```

------

### 8.2 Following Sibling

```python
//h2/following-sibling::p
```

------

### 8.3 Preceding Sibling

```python
//h2/preceding-sibling::p
```

------

## 9. Real Crawling Example (Requests + XPath)

```python
import requests
from lxml import etree

url = "https://example.com"
response = requests.get(url, timeout=10)
response.encoding = "utf-8"

tree = etree.HTML(response.text)

titles = tree.xpath('//h1/text()')
links = tree.xpath('//a/@href')

print(titles)
print(links)
```

------

## 10. Common XPath Patterns (Cheat Sheet)

| Goal           | XPath                          |
| -------------- | ------------------------------ |
| All text       | `//text()`                     |
| Images         | `//img/@src`                   |
| Links          | `//a/@href`                    |
| Class contains | `//*[contains(@class,"item")]` |
| Table rows     | `//table//tr`                  |
| Form inputs    | `//input/@value`               |

------

## 11. Handling Missing Elements Safely

```python
title = tree.xpath('//h1/text()')
title = title[0] if title else None
```

------

## 12. Debugging XPath (Highly Recommended)

### Use Browser DevTools

1.  Open page in Chrome
2.  Press **F12**
3.  Select an element
4.  Right-click → **Copy → Copy XPath**
5.  Optimize it manually

👉 **Tip**: Avoid absolute XPath copied directly from browser.

------

## 13. XPath vs CSS Selector (Quick Comparison)

| Feature          | XPath    | CSS       |
| ---------------- | -------- | --------- |
| Parent selection | ✅ Yes    | ❌ No      |
| Text extraction  | ✅ Yes    | ❌ No      |
| Complex logic    | ✅ Strong | ⚠ Limited |

👉 **For crawlers**: XPath is usually **more powerful**.

------

## 14. Common Beginner Mistakes

❌ Using absolute XPath
❌ Overusing `//` everywhere
❌ Forgetting XPath index starts at 1
❌ Assuming element always exists

------

## 15. When You Are Ready for Next Level

Next steps after mastering XPath:

-   Combine XPath + Regex
-   Use **Scrapy selectors**
-   Handle **AJAX-loaded pages**
-   Anti-crawler strategies
-   Pagination crawling

------

## 16. Summary

-   XPath is **essential** for Python web crawlers
-   Learn:
    -   `//`
    -   `text()`
    -   `@attribute`
    -   `contains()`
-   Practice on real websites
-   Keep XPath **simple & robust**

