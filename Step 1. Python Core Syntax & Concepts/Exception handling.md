This topic teaches how to make your programs **robust**, **error-tolerant**, and **graceful** when something goes wrong.

Let’s dive deep into how Python handles exceptions, how to use `try`, `except`, `else`, and `finally`, and best practices for real-world development.

---

# **1. What Are Exceptions?**

### **Definition**

An **exception** is a runtime error that interrupts the normal flow of your program.

When an error occurs, Python:

1. **Raises** an exception object.
2. **Stops** normal execution.
3. **Looks** for code to handle it (`try/except` block).
4. If no handler exists, the program **crashes** with an error message.

---

### **Example: Unhandled Exception**

```python
x = 10 / 0
```

✅ Output:

```
ZeroDivisionError: division by zero
```

This is an exception — the program stops immediately because Python cannot divide by zero.

---

# **2. Handling Exceptions Using `try` and `except`**

The `try` block contains code that might raise an exception.
The `except` block defines how to handle it.

---

### **Basic Syntax**

```python
try:
    # Code that may raise error
except:
    # Handle the error
```

---

### **Example 1: Generic Exception Handling**

```python
try:
    x = 10 / 0
except:
    print("Something went wrong!")
```

✅ Output:

```
Something went wrong!
```

⚠️ **Note:** This catches *any* error, but it’s not best practice — we should catch specific exceptions when possible.

---

### **Example 2: Catching Specific Exception**

```python
try:
    x = int("abc")  # invalid conversion
except ValueError:
    print("Invalid number format!")
```

✅ Output:

```
Invalid number format!
```

---

### **Example 3: Multiple Except Blocks**

You can handle different errors differently.

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ValueError:
    print("Please enter a valid integer.")
except ZeroDivisionError:
    print("You cannot divide by zero.")
```

✅ Output (for `0` input):

```
You cannot divide by zero.
```

✅ Output (for `"abc"` input):

```
Please enter a valid integer.
```

---

# **3. Using `else` with `try/except`**

The `else` block runs **only if no exception occurs** in the `try` block.

```python
try:
    num = int(input("Enter a number: "))
except ValueError:
    print("Invalid number.")
else:
    print(f"You entered {num}")
```

✅ Output (for `10` input):

```
You entered 10
```

✅ Output (for `"abc"` input):

```
Invalid number.
```

---

# **4. Using `finally` Block**

The `finally` block **always runs**, whether an exception occurred or not.
Commonly used for **cleanup** actions like closing files, releasing resources, or closing database connections.

---

### **Example 1: Basic finally**

```python
try:
    file = open("example.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found.")
finally:
    print("Closing file.")
```

✅ Output (if file missing):

```
File not found.
Closing file.
```

✅ Output (if file exists):

```
<file content>
Closing file.
```

Even if the file doesn’t exist, the `finally` block executes.

---

### **Example 2: Combining All**

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ValueError:
    print("Not a number!")
except ZeroDivisionError:
    print("Cannot divide by zero!")
else:
    print("Result:", result)
finally:
    print("Execution complete.")
```

✅ Output (for `2`):

```
Result: 5.0
Execution complete.
```

✅ Output (for `0`):

```
Cannot divide by zero!
Execution complete.
```

✅ Output (for `abc`):

```
Not a number!
Execution complete.
```

---

# **5. Catching Multiple Exceptions Together**

You can catch multiple exceptions in one block:

```python
try:
    result = 10 / int("abc")
except (ZeroDivisionError, ValueError) as e:
    print("Error:", e)
```

✅ Output:

```
Error: invalid literal for int() with base 10: 'abc'
```

Here, the exception object `e` contains the error message.

---

# **6. Accessing Exception Details**

Every exception object carries information about the error.

```python
try:
    result = 10 / 0
except ZeroDivisionError as e:
    print("Error details:", e)
```

✅ Output:

```
Error details: division by zero
```

---

# **7. Raising Exceptions Manually (`raise`)**

You can **manually raise** an exception using the `raise` keyword.

### **Example 1: Raise Built-in Exception**

```python
def set_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative!")
    print(f"Age set to {age}")

set_age(-5)
```

✅ Output:

```
ValueError: Age cannot be negative!
```

---

### **Example 2: Raise Custom Exception**

You can define your own error classes (used often in APIs).

```python
class InvalidEmailError(Exception):
    pass

def register(email):
    if "@" not in email:
        raise InvalidEmailError("Invalid email address")
    print("Email registered successfully!")

try:
    register("abc.com")
except InvalidEmailError as e:
    print("Error:", e)
```

✅ Output:

```
Error: Invalid email address
```

---

# **8. Nested Exception Handling**

You can nest try-except blocks for more granular control.

```python
try:
    x = int(input("Enter number: "))
    try:
        result = 10 / x
    except ZeroDivisionError:
        print("Inner: Cannot divide by zero")
except ValueError:
    print("Outer: Invalid input")
```

✅ Handles both input and arithmetic errors separately.

---

# **9. Best Practices for Exception Handling**

| Practice                                      | Example                                     |
| --------------------------------------------- | ------------------------------------------- |
| ✅ Catch specific exceptions                   | `except ValueError:` not just `except:`     |
| ✅ Use `finally` for cleanup                   | Close files, DB, etc.                       |
| ✅ Log errors instead of printing              | Use `logging` module                        |
| ✅ Avoid silent failures                       | Don’t use empty `except:` blocks            |
| ✅ Raise exceptions when invalid data is found | `raise ValueError("Invalid data")`          |
| ✅ Keep try-block small                        | Only wrap code that can raise errors        |
| ✅ Create custom exceptions for business logic | e.g., `InvalidUserError`, `AuthFailedError` |

---

# **10. Real-World Example (File Operation)**

```python
import os

def read_config(filename):
    try:
        if not os.path.exists(filename):
            raise FileNotFoundError(f"File {filename} not found")

        with open(filename, "r") as file:
            data = file.read()
    except FileNotFoundError as e:
        print("Error:", e)
    except PermissionError:
        print("No permission to read file")
    else:
        print("File read successfully:")
        print(data)
    finally:
        print("Operation complete.")
```

✅ Demonstrates proper error handling and cleanup — exactly how production code in APIs or services should behave.

---

# **11. Common Built-in Exceptions**

| Exception           | Description               |
| ------------------- | ------------------------- |
| `ValueError`        | Wrong value type          |
| `TypeError`         | Wrong data type           |
| `ZeroDivisionError` | Division by zero          |
| `IndexError`        | Index out of range        |
| `KeyError`          | Missing key in dictionary |
| `FileNotFoundError` | File not found            |
| `IOError`           | Input/output failure      |
| `ImportError`       | Module import fails       |
| `AttributeError`    | Attribute doesn’t exist   |
| `AssertionError`    | Assertion fails           |

---

# **12. Summary Table**

| Keyword   | Purpose              | Runs When          |
| --------- | -------------------- | ------------------ |
| `try`     | Wraps risky code     | Always             |
| `except`  | Handles exceptions   | When error occurs  |
| `else`    | Executes if no error | No error           |
| `finally` | Cleanup operations   | Always             |
| `raise`   | Manually raise error | When condition met |

---

# **Quick Example Recap**

```python
try:
    # risk
    x = int(input("Enter number: "))
    result = 10 / x
except ZeroDivisionError:
    print("Cannot divide by zero.")
except ValueError:
    print("Invalid input.")
else:
    print("Success:", result)
finally:
    print("End of program.")
```

✅ Output (for `0`):

```
Cannot divide by zero.
End of program.
```

✅ Output (for `2`):

```
Success: 5.0
End of program.
```

---
