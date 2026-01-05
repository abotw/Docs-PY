# JupyterLab

## 1. What Is JupyterLab?

**JupyterLab** is a **web-based interactive development environment** for Python (and many other languages).
It lets you:

-   Write and run Python code **cell by cell**
-   Combine **code, text, math, and plots** in one document
-   Explore data interactively
-   Keep your analysis **reproducible and readable**

Think of JupyterLab as:

>   📓 *A smart notebook for coding, data analysis, and learning.*

------

## 2. Jupyter Notebook vs JupyterLab

| Feature       | Jupyter Notebook | JupyterLab              |
| ------------- | ---------------- | ----------------------- |
| Interface     | Single document  | Full IDE-like workspace |
| File browser  | Limited          | Powerful sidebar        |
| Multiple tabs | ❌                | ✅                       |
| Extensions    | Limited          | Strong support          |
| Status        | Legacy           | **Recommended**         |

👉 **JupyterLab is the modern replacement** for Jupyter Notebook.

------

## 3. Installing JupyterLab

### Option 1: Using pip (recommended)

```bash
pip install jupyterlab
```

Verify installation:

```bash
jupyter lab --version
```

### Option 2: Using Anaconda

If you use Anaconda:

```bash
conda install -c conda-forge jupyterlab
```

------

## 4. Starting JupyterLab

From your terminal:

```bash
jupyter lab
```

What happens:

-   A browser opens automatically

-   URL usually looks like:

    ```
    http://localhost:8888/lab
    ```

⚠️ **Do not close the terminal** while JupyterLab is running.

------

## 5. Understanding the JupyterLab Interface

### Main Areas

1.  **Left Sidebar**
    -   File Browser
    -   Running Kernels
    -   Extensions
2.  **Main Work Area**
    -   Notebooks
    -   Terminals
    -   Text files
    -   Multiple tabs
3.  **Top Menu**
    -   File / Edit / View / Run / Kernel / Help

------

## 6. Creating Your First Notebook

1.  Click **“+”** (Launcher)
2.  Under **Notebook**, choose **Python 3**
3.  A new `.ipynb` file opens

This file is a **Jupyter Notebook**.

------

## 7. Cells: The Core Concept

### Types of Cells

#### 1️⃣ Code Cell

Used for Python code.

```python
print("Hello, JupyterLab!")
```

Run it:

-   **Shift + Enter** → Run & move to next cell
-   **Ctrl + Enter** → Run & stay

------

#### 2️⃣ Markdown Cell

Used for text, explanations, formulas.

Change cell type:

-   Toolbar dropdown
-   Or press `M` (command mode)

Example:

```markdown
# My First Notebook
This notebook demonstrates basic Python usage.
```

------

## 8. Command Mode vs Edit Mode

| Mode         | Border Color | Purpose             |
| ------------ | ------------ | ------------------- |
| Edit Mode    | Green        | Typing code/text    |
| Command Mode | Blue         | Notebook operations |

Switch modes:

-   `Enter` → Edit mode
-   `Esc` → Command mode

Useful shortcuts (Command Mode):

-   `A` → Add cell above
-   `B` → Add cell below
-   `D D` → Delete cell
-   `Z` → Undo delete

------

## 9. Running Python Code

Example:

```python
x = 10
y = 20
x + y
```

✔ The **last expression is automatically displayed**
(no `print()` needed)

------

## 10. Using JupyterLab for Data Analysis

### Example: Simple Plot

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4]
y = [1, 4, 9, 16]

plt.plot(x, y)
plt.show()
```

Plots appear **inline**, right below the cell.

------

## 11. Managing Files

-   Files are saved automatically
-   `.ipynb` contains:
    -   Code
    -   Output
    -   Markdown
-   Can be:
    -   Reopened
    -   Shared
    -   Converted (HTML / PDF)

Export:

```
File → Export Notebook As → HTML
```

------

## 12. Using the Terminal Inside JupyterLab

Open:

```
Launcher → Terminal
```

You can:

-   Run `pip`
-   Use `git`
-   Execute shell commands

Example:

```bash
pip install numpy
```

------

## 13. Kernels Explained (Very Important)

A **kernel** is the Python process running your code.

Key actions:

-   **Restart Kernel** → clears variables
-   **Interrupt Kernel** → stop running code
-   **Change Kernel** → switch Python versions

Menu:

```
Kernel → Restart Kernel
```

------

## 14. Common Beginner Mistakes

❌ Forgetting to run cells in order
❌ Kernel using wrong Python environment
❌ Assuming variables persist after restart
❌ Closing terminal stops JupyterLab

------

## 15. When Should You Use JupyterLab?

Perfect for:

-   Learning Python
-   Data analysis
-   Machine learning
-   Experiments & visualization
-   Teaching and demos

Not ideal for:

-   Large production systems
-   Complex backend services

------

## 16. Recommended Next Steps

-   Learn **Markdown** basics
-   Practice keyboard shortcuts
-   Use **virtual environments**
-   Try libraries:
    -   `numpy`
    -   `pandas`
    -   `matplotlib`

------

## 17. Summary

✔ JupyterLab is an interactive Python workspace
✔ Code runs cell by cell
✔ Great for learning and data analysis
✔ Modern replacement for Jupyter Notebook