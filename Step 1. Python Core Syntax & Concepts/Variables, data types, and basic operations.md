let’s go deep into **Python variables, data types, and basic operations**, explained thoroughly and clearly so that even as a beginner, you’ll build a strong foundation for your future Python work.

---

## **1. Variables in Python**

### **Definition**

A *variable* in Python is a name that refers to a value stored in memory. You can think of it as a labeled container that holds data.

Unlike PHP or C, Python is **dynamically typed**, which means you don’t need to declare a variable’s type explicitly — Python figures it out at runtime.

```python
x = 10          # integer
name = "Nitin"  # string
pi = 3.14159    # float
```

### **Key Points**

* You can reassign variables to different data types.
* Variable names must start with a letter or underscore and can’t contain spaces.
* Python uses *snake_case* for variable naming by convention.

```python
user_age = 25
_user_id = "A123"
```

---

## **2. Variable Assignment and Memory Model**

Python variables are **references** to objects in memory, not direct containers of values.

When you write:

```python
a = 5
b = a
```

Both `a` and `b` refer to the *same* object (`5`).
If the object is **immutable** (like integers, strings, tuples), reassigning one won’t affect the other.
If it’s **mutable** (like lists or dictionaries), changes via one variable can affect the other reference.

### Example:

```python
list1 = [1, 2, 3]
list2 = list1
list2.append(4)

print(list1)  # [1, 2, 3, 4]
```

Both variables point to the same list in memory.

---

## **3. Data Types in Python**

Python has several **built-in data types**, which can be broadly grouped as:

| Category | Type                               | Example                         |
| -------- | ---------------------------------- | ------------------------------- |
| Numeric  | `int`, `float`, `complex`          | 42, 3.14, 2 + 5j                |
| Sequence | `str`, `list`, `tuple`, `range`    | "abc", [1,2], (1,2,3), range(5) |
| Mapping  | `dict`                             | {"key": "value"}                |
| Set      | `set`, `frozenset`                 | {1,2,3}, frozenset({1,2})       |
| Boolean  | `bool`                             | True, False                     |
| Binary   | `bytes`, `bytearray`, `memoryview` | b"hello", bytearray(5)          |
| None     | `NoneType`                         | None                            |

---

### **a. Numeric Types**

#### `int` — Integer

Used for whole numbers.

```python
age = 30
```

#### `float` — Floating-point

Decimal or real numbers.

```python
price = 99.99
```

#### `complex` — Complex numbers

Used in scientific applications.

```python
z = 3 + 4j
```

---

### **b. Sequence Types**

#### `str` — String

Strings are immutable.

```python
greeting = "Hello World"
print(greeting[0])  # 'H'
```

#### `list` — Ordered, mutable

```python
nums = [1, 2, 3]
nums.append(4)
```

#### `tuple` — Ordered, immutable

```python
colors = ('red', 'green', 'blue')
```

#### `range`

Used in loops.

```python
for i in range(3):
    print(i)
```

---

### **c. Mapping Type**

#### `dict` — Key-value pairs

```python
user = {"name": "Nitin", "age": 30}
print(user["name"])  # 'Nitin'
```

---

### **d. Set Types**

#### `set` — Unordered, unique elements

```python
fruits = {"apple", "banana", "apple"}
print(fruits)  # {'apple', 'banana'}
```

#### `frozenset` — Immutable version of set

---

### **e. Boolean Type**

Used for logical conditions.

```python
is_active = True
is_admin = False
```

---

### **f. None Type**

Represents “no value”.

```python
data = None
```

---

## **4. Basic Operations in Python**

### **Arithmetic Operators**

| Operator | Description    | Example   | Output |
| -------- | -------------- | --------- | ------ |
| `+`      | Addition       | `3 + 2`   | 5      |
| `-`      | Subtraction    | `5 - 2`   | 3      |
| `*`      | Multiplication | `3 * 4`   | 12     |
| `/`      | Division       | `10 / 3`  | 3.333  |
| `//`     | Floor Division | `10 // 3` | 3      |
| `%`      | Modulus        | `10 % 3`  | 1      |
| `**`     | Exponentiation | `2 ** 3`  | 8      |

---

### **Comparison Operators**

Return `True` or `False`.

| Operator | Meaning          | Example  |
| -------- | ---------------- | -------- |
| `==`     | Equal to         | `a == b` |
| `!=`     | Not equal        | `a != b` |
| `>`      | Greater than     | `a > b`  |
| `<`      | Less than        | `a < b`  |
| `>=`     | Greater or equal | `a >= b` |
| `<=`     | Less or equal    | `a <= b` |

---

### **Logical Operators**

| Operator | Example            | Meaning                                |
| -------- | ------------------ | -------------------------------------- |
| `and`    | `a > 10 and b < 5` | True if both conditions are True       |
| `or`     | `a > 10 or b < 5`  | True if at least one condition is True |
| `not`    | `not a > 10`       | Negates the result                     |

---

### **Assignment Operators**

Shortcut for arithmetic + assignment.

```python
x = 10
x += 2   # same as x = x + 2
x *= 3   # same as x = x * 3
```

---

### **Membership Operators**

| Operator | Example              | Meaning |
| -------- | -------------------- | ------- |
| `in`     | `'a' in 'apple'`     | True    |
| `not in` | `'x' not in 'apple'` | True    |

---

### **Identity Operators**

Compare object *identity*, not equality.

| Operator | Example      | Meaning                   |
| -------- | ------------ | ------------------------- |
| `is`     | `a is b`     | True if same object       |
| `is not` | `a is not b` | True if different objects |

---

## **5. Type Conversion (Casting)**

You can convert between data types using constructor functions.

```python
x = 5
print(float(x))   # 5.0

y = "10"
print(int(y))     # 10
```

For complex conversions:

```python
num = "123"
converted = int(num)
```

---

## **6. Type Checking**

Use `type()` to inspect an object’s type.

```python
name = "Nitin"
print(type(name))  # <class 'str'>
```

Use `isinstance()` for safer checks:

```python
print(isinstance(3.14, float))  # True
```

---

## **7. Constants**

Python doesn’t enforce constants, but conventionally, constants are defined in uppercase:

```python
PI = 3.14159
MAX_USERS = 100
```

---

## **8. Summary Mindmap**

**Variables →** Names referencing memory objects
**Data Types →** int, float, str, list, dict, tuple, set, bool, None
**Operations →** Arithmetic, logical, comparison, assignment, membership, identity

---
