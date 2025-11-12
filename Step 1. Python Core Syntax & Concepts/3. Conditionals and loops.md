now let’s cover **Conditionals and Loops** in Python, step-by-step and in depth.
These are control structures that define **how your program makes decisions** and **repeats actions**, which are fundamental to any backend logic you’ll later write in FastAPI or database code.

---

# **1. Conditionals (Decision Making in Python)**

### **Concept**

Conditionals allow your code to **execute different blocks** based on whether a condition is `True` or `False`.

---

## **1.1 The `if` Statement**

```python
age = 18

if age >= 18:
    print("You are eligible to vote.")
```

✅ **Explanation:**

* `if` evaluates a condition (`age >= 18`).
* If it’s `True`, the indented block runs.
* Python uses **indentation (4 spaces)** instead of curly braces `{}`.

---

## **1.2 The `if-else` Statement**

```python
age = 16

if age >= 18:
    print("You are eligible to vote.")
else:
    print("You are not eligible to vote.")
```

✅ **Explanation:**
If the condition is false, the `else` block runs.

---

## **1.3 The `if-elif-else` Ladder**

Use `elif` (“else if”) to test multiple conditions.

```python
marks = 75

if marks >= 90:
    print("Grade: A")
elif marks >= 75:
    print("Grade: B")
elif marks >= 60:
    print("Grade: C")
else:
    print("Grade: D")
```

✅ **Explanation:**
Python checks conditions **in order** until one matches, then skips the rest.

---

## **1.4 Nested `if` Statements**

You can place one `if` inside another.

```python
age = 25
citizen = True

if age >= 18:
    if citizen:
        print("Eligible voter")
    else:
        print("Not a citizen")
```

✅ Use nested conditionals carefully; if they get too deep, use logical operators instead.

---

## **1.5 Conditional Expressions (Ternary Operator)**

A compact one-line way to write simple `if-else`.

```python
status = "adult" if age >= 18 else "minor"
```

✅ **Example use case:**

```python
access = "Granted" if user_logged_in else "Denied"
```

---

## **1.6 Logical Operators in Conditions**

| Operator | Description             | Example            | Result |
| -------- | ----------------------- | ------------------ | ------ |
| `and`    | True if both are True   | `x > 0 and x < 10` | True   |
| `or`     | True if any one is True | `x < 0 or x > 10`  | False  |
| `not`    | Negates the result      | `not True`         | False  |

---

## **1.7 Membership & Identity in Conditions**

```python
fruit = "apple"
basket = ["apple", "banana", "cherry"]

if fruit in basket:
    print("Fruit available")
```

```python
a = [1, 2, 3]
b = a
if a is b:
    print("Same object in memory")
```

---

# **2. Loops (Repetition in Python)**

Loops help you **repeat** code blocks multiple times without writing them again.

---

## **2.1 The `for` Loop**

Used for iterating over **sequences** (like lists, tuples, strings, or ranges).

### **Syntax:**

```python
for variable in sequence:
    # code block
```

### **Example 1:**

```python
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

✅ Each iteration assigns one item to `fruit`.

---

### **Example 2: Using `range()`**

```python
for i in range(5):
    print(i)
```

**Output:**

```
0
1
2
3
4
```

✅ `range(5)` generates numbers 0–4.
You can also specify start and step:

```python
for i in range(2, 10, 2):
    print(i)  # 2, 4, 6, 8
```

---

### **Example 3: Looping with Index**

Use `enumerate()` to get both index and value.

```python
for index, fruit in enumerate(fruits):
    print(index, fruit)
```

---

## **2.2 Nested Loops**

```python
for i in range(3):
    for j in range(2):
        print(i, j)
```

✅ Common in matrix or multi-level data handling.

---

## **2.3 Loop Control Statements**

### **`break`**

Stops the loop immediately.

```python
for num in range(10):
    if num == 5:
        break
    print(num)
```

---

### **`continue`**

Skips the rest of the loop for the current iteration.

```python
for num in range(5):
    if num == 2:
        continue
    print(num)
```

---

### **`else` with Loops**

An `else` block runs only if the loop completes **without a `break`**.

```python
for i in range(3):
    print(i)
else:
    print("Loop finished without break")
```

---

## **2.4 The `while` Loop**

Repeats a block **while a condition is True**.

```python
count = 0
while count < 5:
    print("Count:", count)
    count += 1
```

✅ **Be careful!** Always ensure your condition eventually becomes False to avoid infinite loops.

---

### **`while` with `break` and `continue`**

```python
num = 0
while True:
    num += 1
    if num == 3:
        continue
    if num == 5:
        break
    print(num)
```

---

## **2.5 Infinite Loops**

Use intentionally when you need continuous execution (like servers or background jobs), but always include a safe exit.

```python
while True:
    cmd = input("Type 'exit' to quit: ")
    if cmd == "exit":
        break
```

---

## **2.6 Looping Over Different Data Types**

### **List**

```python
for item in [1, 2, 3]:
    print(item)
```

### **Tuple**

```python
for x in (10, 20, 30):
    print(x)
```

### **Dictionary**

```python
person = {"name": "Nitin", "age": 30}
for key, value in person.items():
    print(key, value)
```

### **Set**

```python
for val in {10, 20, 30}:
    print(val)
```

### **String**

```python
for ch in "Python":
    print(ch)
```

---

# **3. Real-Life Examples**

### **Example 1: Counting Even Numbers**

```python
numbers = [1, 2, 3, 4, 5, 6]
even_count = 0

for n in numbers:
    if n % 2 == 0:
        even_count += 1

print("Total even numbers:", even_count)
```

---

### **Example 2: Nested Dictionary Loop**

```python
users = {
    "u1": {"name": "Nitin", "role": "admin"},
    "u2": {"name": "Arnav", "role": "dev"}
}

for uid, info in users.items():
    print(uid, info["name"], info["role"])
```

---

### **Example 3: While Loop for Login Attempt**

```python
password = "python123"
attempt = ""

while attempt != password:
    attempt = input("Enter password: ")
    if attempt == password:
        print("Access granted")
    else:
        print("Try again!")
```

---

# **4. Summary**

| Concept                | Description             | Example                |
| ---------------------- | ----------------------- | ---------------------- |
| `if` / `elif` / `else` | Conditional branching   | Check user input       |
| `for`                  | Iterate over sequence   | Loop through list      |
| `while`                | Repeat while True       | Countdown loop         |
| `break`                | Exit loop early         | Stop at condition      |
| `continue`             | Skip current iteration  | Skip invalid data      |
| `else` (with loops)    | Runs if loop not broken | Loop completed cleanly |

---
