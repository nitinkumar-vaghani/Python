it’s time to learn how to **organize multiple functions and classes across files** using **modules, imports, and packages** — this is essential before building any real-world FastAPI or Python project.

Let’s go step-by-step, with clear examples and best practices.

---

# **1. What Are Modules in Python**

### **Definition**

A **module** is simply a **Python file** (`.py`) that contains **functions, variables, and classes** you can import and reuse in other files.

It’s Python’s way of organizing code logically and making it reusable across multiple scripts or projects.

---

### **Example: Creating and Using a Module**

#### **Step 1: Create a file `math_utils.py`**

```python
# math_utils.py
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

PI = 3.14159
```

#### **Step 2: Import and use it in another file**

```python
# main.py
import math_utils

print(math_utils.add(10, 5))      # 15
print(math_utils.subtract(10, 5)) # 5
print(math_utils.PI)              # 3.14159
```

✅ **Explanation:**

* `math_utils` is a **module name** (the file name without `.py`).
* Everything inside it is accessible via `math_utils.<name>`.

---

# **2. Importing Modules**

Python provides multiple ways to import.

---

### **2.1 Basic Import**

```python
import module_name
```

You access everything with the module prefix.

---

### **2.2 Import with Alias**

```python
import math_utils as mu

print(mu.add(2, 3))
```

✅ **Why use aliases?**

* To shorten long module names
* To avoid naming conflicts

---

### **2.3 Import Specific Items**

```python
from math_utils import add, subtract

print(add(10, 5))
```

✅ You can now use `add()` directly — no module prefix needed.

---

### **2.4 Import All Items (Not Recommended)**

```python
from math_utils import *
```

✅ Works, but pollutes the namespace and risks overwriting existing names.

---

### **2.5 Importing Built-in Modules**

Python includes many **standard library** modules:

```python
import math
import datetime
import os

print(math.sqrt(16))          # 4.0
print(datetime.date.today())  # current date
print(os.getcwd())            # current working directory
```

---

# **3. Module Search Path**

When you import a module, Python looks for it in:

1. The current working directory
2. The directories listed in `sys.path`
3. The standard library directories

You can check where Python looks:

```python
import sys
print(sys.path)
```

✅ If your custom module is not in any of these paths, Python will raise:

```
ModuleNotFoundError
```

You can dynamically add your path:

```python
import sys
sys.path.append("/path/to/your/module")
```

---

# **4. What Are Packages**

### **Definition**

A **package** is a **collection of modules** grouped inside a **directory** with an `__init__.py` file.

It allows you to organize related modules under a common namespace.

---

### **Example: Package Structure**

```
my_project/
│
├── main.py
└── utils/
    ├── __init__.py
    ├── math_utils.py
    ├── string_utils.py
```

* `utils` is a **package**.
* Each `.py` file inside it is a **module**.
* The `__init__.py` file makes the directory a **package** (it can be empty or initialize something).

---

### **4.1 Using a Package**

```python
# main.py
from utils import math_utils, string_utils

print(math_utils.add(5, 10))
```

✅ You can import multiple modules from one package.

---

### **4.2 Nested Packages**

Packages can have subpackages.

```
my_app/
│
├── api/
│   ├── __init__.py
│   ├── routes/
│   │   ├── __init__.py
│   │   ├── user.py
│   │   ├── product.py
```

Example:

```python
from api.routes import user
```

---

# **5. The `__init__.py` File**

The `__init__.py` file is executed when the package is imported.

### **Example:**

```python
# utils/__init__.py
print("Initializing utils package")
```

When you do:

```python
import utils
```

✅ Output:

```
Initializing utils package
```

You can also define what should be exported:

```python
# utils/__init__.py
__all__ = ["math_utils", "string_utils"]
```

This restricts what `from utils import *` brings in.

---

# **6. Relative vs Absolute Imports**

### **6.1 Absolute Import**

Specifies the full path from the project root.

```python
from utils.math_utils import add
```

---

### **6.2 Relative Import**

Used **inside a package** using dots (`.`):

* `.` means *current package*
* `..` means *one level up*

Example inside `utils/string_utils.py`:

```python
from .math_utils import add
```

✅ Relative imports are common inside modular applications (like FastAPI projects).

---

# **7. Standard Library vs Third-Party Packages**

| Type                 | Description                           | Example                                 | Installation          |
| -------------------- | ------------------------------------- | --------------------------------------- | --------------------- |
| **Standard Library** | Comes with Python                     | `os`, `sys`, `math`, `json`, `datetime` | Pre-installed         |
| **Third-Party**      | External packages installed via `pip` | `fastapi`, `pydantic`, `sqlalchemy`     | `pip install fastapi` |

You can view installed packages:

```bash
pip list
```

---

# **8. Creating Your Own Package (Reusable Library)**

Let’s say you want to publish or reuse your code.

### **Folder Structure**

```
my_library/
│
├── my_library/
│   ├── __init__.py
│   ├── math_utils.py
│   ├── string_utils.py
│
├── pyproject.toml
└── README.md
```

You can then install it locally:

```bash
pip install .
```

Or publish it to [PyPI](https://pypi.org) for public use.

---

# **9. Common Built-in Modules You’ll Use Often**

| Module        | Purpose                     |
| ------------- | --------------------------- |
| `os`          | File & directory handling   |
| `sys`         | System-specific parameters  |
| `math`        | Mathematical functions      |
| `random`      | Random number generation    |
| `datetime`    | Dates & times               |
| `json`        | JSON encoding/decoding      |
| `re`          | Regular expressions         |
| `collections` | Specialized data structures |
| `itertools`   | Iteration utilities         |
| `logging`     | Application logging         |

---

# **10. Example: Organizing a Real Project**

Let’s simulate a real-world project folder.

```
ecommerce/
│
├── app/
│   ├── __init__.py
│   ├── models/
│   │   ├── __init__.py
│   │   └── user.py
│   ├── utils/
│   │   ├── __init__.py
│   │   ├── math_utils.py
│   │   └── validator.py
│   └── main.py
```

### `app/utils/math_utils.py`

```python
def calculate_discount(price, percent):
    return price - (price * percent / 100)
```

### `app/main.py`

```python
from utils.math_utils import calculate_discount

result = calculate_discount(200, 10)
print(result)
```

✅ Output:

```
180.0
```

This modular structure is how real-world Python (and FastAPI) projects are organized.

---

# **11. Summary**

| Concept                 | Description                                      | Example                                    |
| ----------------------- | ------------------------------------------------ | ------------------------------------------ |
| **Module**              | A single `.py` file with code                    | `math_utils.py`                            |
| **Package**             | A folder with `__init__.py` and multiple modules | `utils/`                                   |
| **Import**              | Bring code from modules into others              | `import module`, `from module import func` |
| **Alias**               | Shorten names                                    | `import numpy as np`                       |
| **Relative import**     | Import within package                            | `from .file import func`                   |
| **Third-party package** | Installed via pip                                | `import fastapi`                           |

---
