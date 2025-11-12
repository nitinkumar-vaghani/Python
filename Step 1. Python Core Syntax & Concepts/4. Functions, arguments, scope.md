now you’re stepping into one of the **most powerful and essential topics in Python:**
**Functions, arguments, and scope.**

These are the foundation of writing reusable, clean, and modular code — absolutely critical for building scalable APIs, background jobs, and database logic in FastAPI or Snowflake integration later.

Let’s go deep into how functions work in Python, how arguments are passed, and how variable scope affects data inside and outside functions.

---

# **1. Functions in Python**

### **Definition**

A **function** is a reusable block of code that performs a specific task.
Functions make your code modular, organized, and easy to maintain.

### **Basic Syntax**

```python
def function_name(parameters):
    """Optional docstring describing the function"""
    # Function body
    return value
```

---

### **Example:**

```python
def greet():
    print("Hello, welcome to Python!")
```

Call the function:

```python
greet()
```

✅ Output:

```
Hello, welcome to Python!
```

---

### **Why use functions?**

* Avoid repeating code (DRY principle)
* Organize logic into blocks
* Improve testing and readability
* Allow reusability and composition

---

# **2. Function with Parameters and Return Value**

### **Example 1: Simple function with parameters**

```python
def greet_user(name):
    print(f"Hello, {name}!")
```

Call it:

```python
greet_user("Nitin")
```

✅ Output:

```
Hello, Nitin!
```

---

### **Example 2: Function returning a value**

```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)
```

✅ Output:

```
8
```

If a function doesn’t explicitly return anything, it returns `None` by default.

---

# **3. Types of Arguments**

Python supports **multiple ways** to pass arguments into functions.
Let’s go through each.

---

## **3.1 Positional Arguments**

These are passed in order.

```python
def multiply(a, b):
    return a * b

print(multiply(2, 3))  # 6
```

✅ The first argument → `a`, second → `b`.

---

## **3.2 Keyword Arguments**

Arguments can be passed by name, not just position.

```python
def student_info(name, grade):
    print(f"Name: {name}, Grade: {grade}")

student_info(grade="A", name="Nitin")
```

✅ Order doesn’t matter when using keywords.

---

## **3.3 Default Arguments**

Provide default values for parameters.

```python
def greet(name="Guest"):
    print(f"Hello, {name}!")

greet()         # Hello, Guest!
greet("Dev")  # Hello, Dev!
```

✅ Useful for optional parameters in APIs.

---

## **3.4 Variable-Length Arguments (`*args`)**

Use `*args` when you don’t know how many **positional arguments** will be passed.

```python
def total_sum(*numbers):
    print(numbers)
    return sum(numbers)

print(total_sum(1, 2, 3, 4))  # 10
```

✅ Inside the function, `args` is a **tuple**.

---

## **3.5 Keyword Variable-Length Arguments (`**kwargs`)**

Use `**kwargs` to pass variable **keyword arguments**.

```python
def user_info(**details):
    print(details)

user_info(name="Nitin", age=30, country="India")
```

✅ Inside the function, `kwargs` is a **dictionary**.

---

## **3.6 Mixing Argument Types**

The order **must always** be:

> positional → *args → keyword → **kwargs

```python
def example(a, b=10, *args, **kwargs):
    print(a, b, args, kwargs)

example(5, 15, 20, 25, name="Nitin", role="Developer")
```

✅ Output:

```
5 15 (20, 25) {'name': 'Nitin', 'role': 'Developer'}
```

---

# **4. Return Statement**

Functions can return **single or multiple** values.

```python
def calculate(a, b):
    return a + b, a * b

add, multiply = calculate(5, 10)
print(add, multiply)
```

✅ Output:

```
15 50
```

Python returns multiple values as a **tuple**.

---

# **5. Lambda (Anonymous) Functions**

A **lambda function** is a small, one-line, anonymous function.
Useful for short, simple tasks.

### **Syntax:**

```python
lambda arguments: expression
```

### **Example:**

```python
square = lambda x: x * x
print(square(4))  # 16
```

You can use it in combination with `map()`, `filter()`, and `sorted()`.

```python
nums = [1, 2, 3, 4]
squares = list(map(lambda x: x**2, nums))
```

---

# **6. Function Scope in Python**

**Scope** defines *where a variable is accessible*.

Python has **LEGB** rule for variable lookup:

1. **L**ocal — inside the current function
2. **E**nclosing — in nested functions
3. **G**lobal — at the top level of the module
4. **B**uilt-in — predefined names (like `len`, `print`)

---

## **6.1 Local Scope**

Defined inside a function, available only there.

```python
def greet():
    message = "Hello"  # local variable
    print(message)

greet()
# print(message)  # Error: NameError
```

---

## **6.2 Global Scope**

Defined outside any function and accessible everywhere (unless shadowed).

```python
x = 10

def show():
    print(x)  # Access global variable

show()
```

---

## **6.3 Modifying Global Variables**

To modify a global variable inside a function, use `global`.

```python
count = 0

def increment():
    global count
    count += 1

increment()
print(count)  # 1
```

✅ Without `global`, Python would treat `count` as a new local variable.

---

## **6.4 Enclosing Scope (Nested Functions)**

```python
def outer():
    x = "outer value"

    def inner():
        print(x)  # access enclosing scope
    inner()

outer()
```

✅ Variables in the **outer (enclosing)** function are accessible to the inner one.

---

## **6.5 `nonlocal` Keyword**

Used inside nested functions to modify enclosing (non-global) variables.

```python
def outer():
    count = 0

    def inner():
        nonlocal count
        count += 1
        print(count)

    inner()
    inner()

outer()
```

✅ Output:

```
1
2
```

---

# **7. Docstrings (Function Documentation)**

A **docstring** is a string literal written as the first line of a function — used for documentation.

```python
def greet(name):
    """This function greets the person by name."""
    print(f"Hello, {name}!")
```

View it using:

```python
print(greet.__doc__)
```

✅ **Best practice:** Always document your functions — tools like FastAPI use them in auto-generated docs.

---

# **8. Practical Examples**

### **Example 1: Temperature Converter**

```python
def celsius_to_fahrenheit(c):
    return (c * 9/5) + 32

print(celsius_to_fahrenheit(30))  # 86.0
```

---

### **Example 2: Even Number Checker**

```python
def is_even(num):
    return num % 2 == 0

print(is_even(10))  # True
```

---

### **Example 3: Nested Function Example**

```python
def power(base):
    def exponent(n):
        return base ** n
    return exponent

cube = power(3)
print(cube(4))  # 81
```

---

# **9. Best Practices**

✅ Keep functions **short and focused**
✅ Use **meaningful names** (`calculate_total`, not `do_it`)
✅ Always use **docstrings** for clarity
✅ Return results instead of printing (more reusable)
✅ Avoid global variables — pass values as parameters
✅ Use default args and type hints for clarity

---

# **10. Quick Summary Table**

| Concept             | Description               | Example                  |
| ------------------- | ------------------------- | ------------------------ |
| Function definition | Reusable code block       | `def greet():`           |
| Parameters          | Input values              | `def add(a, b):`         |
| Return value        | Output from function      | `return a + b`           |
| `*args`             | Variable positional args  | `def total(*n):`         |
| `**kwargs`          | Variable keyword args     | `def info(**d):`         |
| Scope               | Visibility of variable    | Local, Global, Enclosing |
| `global`            | Modify global variable    | `global count`           |
| `nonlocal`          | Modify enclosing variable | `nonlocal x`             |
| Lambda              | Inline function           | `lambda x: x*x`          |

---
