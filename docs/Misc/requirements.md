# Requirements

## 1. What is `requirements.txt`?

`requirements.txt` is a **plain text file** that lists all the **Python packages** your project depends on.

Its main purposes are:

-   ✅ Make your project **reproducible**
-   ✅ Let others install **exactly the same dependencies**
-   ✅ Simplify deployment (servers, Docker, CI/CD)
-   ✅ Avoid “works on my machine” problems

In short:

>   **`requirements.txt` = dependency list for your Python project**

------

## 2. Why Do We Need It?

Imagine this situation:

-   You write a Python project using:
    -   `flask`
    -   `requests`
    -   `pandas`
-   It runs perfectly on your laptop
-   Your teammate or server tries to run it → ❌ **ImportError**

Because those libraries are **not installed**.

With `requirements.txt`, they can simply run:

```bash
pip install -r requirements.txt
```

And everything works.

------

## 3. Basic Format of `requirements.txt`

Each line represents **one dependency**.

### Example

```text
flask
requests
pandas
```

This means:

-   Install the **latest available version** of each package.

------

## 4. Specifying Package Versions (Very Important)

To avoid unexpected bugs, you should **pin versions**.

### Common Version Specifiers

| Syntax | Meaning            |
| ------ | ------------------ |
| `==`   | Exact version      |
| `>=`   | Minimum version    |
| `<=`   | Maximum version    |
| `~=`   | Compatible release |
| `!=`   | Exclude version    |

### Examples

```text
flask==2.3.3
requests>=2.31.0
pandas<=2.1.0
numpy~=1.26.0
```

🔹 **Best practice for production**:
Use **exact versions (`==`)**.

------

## 5. Installing from `requirements.txt`

### Step 1: Create a virtual environment (recommended)

```bash
python -m venv venv
```

Activate it:

-   macOS / Linux

```bash
source venv/bin/activate
```

-   Windows

```bash
venv\Scripts\activate
```

### Step 2: Install dependencies

```bash
pip install -r requirements.txt
```

------

## 6. How to Generate `requirements.txt`

### Method 1: `pip freeze` (most common)

After installing packages:

```bash
pip freeze > requirements.txt
```

Example output:

```text
flask==2.3.3
itsdangerous==2.1.2
jinja2==3.1.2
requests==2.31.0
urllib3==2.0.4
```

⚠️ Note:

-   This includes **all installed packages**, even indirect ones.
-   Best used inside a **clean virtual environment**.

------

### Method 2: Manually Write It (Recommended for learning)

Example:

```text
flask==2.3.3
requests==2.31.0
```

This keeps the file **clean and readable**.

------

## 7. Comments and Blank Lines

You can add comments using `#`.

```text
# Web framework
flask==2.3.3

# HTTP client
requests==2.31.0
```

This is very helpful in team projects.

------

## 8. Advanced Usage

### 8.1 Install from a Git Repository

```text
git+https://github.com/psf/requests.git
```

Or with branch/tag:

```text
git+https://github.com/psf/requests.git@v2.31.0
```

------

### 8.2 Local Packages

```text
-e .
```

Common in development mode for your own project.

------

### 8.3 Multiple Requirement Files

Large projects often split dependencies:

```text
requirements.txt
requirements-dev.txt
requirements-prod.txt
```

Example:

**requirements.txt**

```text
flask==2.3.3
requests==2.31.0
```

**requirements-dev.txt**

```text
-r requirements.txt
pytest==7.4.0
black==23.9.1
```

Install dev dependencies:

```bash
pip install -r requirements-dev.txt
```

------

## 9. Common Mistakes

❌ Forgetting to use a virtual environment
❌ Using `pip freeze` in a polluted environment
❌ Not pinning versions
❌ Mixing development and production dependencies

------

## 10. Best Practices Summary

✅ Always use a virtual environment
✅ Pin versions for production
✅ Keep `requirements.txt` minimal
✅ Use comments for clarity
✅ Separate dev and prod dependencies when needed

------

## 11. When Not to Use `requirements.txt`

Modern tools may replace it:

| Tool             | Use Case               |
| ---------------- | ---------------------- |
| `pipenv`         | Small–medium projects  |
| `poetry`         | Dependency + packaging |
| `conda`          | Scientific computing   |
| `pyproject.toml` | Modern Python standard |

Still, **`requirements.txt` remains the most universal** and widely supported format.

------

## 12. Final Takeaway

>   `requirements.txt` is the **contract** that defines your Python project’s runtime environment.

If you can share your project folder with only:

-   source code
-   `requirements.txt`

and it still runs — you did it right.