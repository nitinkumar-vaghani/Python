let’s go deep into **Lists, Tuples, Sets, and Dictionaries** — the four *core collection data types* in Python.

These are the backbone of Python’s data handling, and you’ll use them constantly in APIs, data processing, and database work (including FastAPI and Snowflake integrations).

---

## **1. Lists**

### **Definition**

A **list** is an **ordered, mutable (changeable)** collection that can hold mixed data types.

```python
fruits = ["apple", "banana", "cherry"]
```

Lists are like arrays in PHP, but with *zero-based indexing* and *more flexibility*.

---

### **Characteristics**

| Property              | Description                         |
| --------------------- | ----------------------------------- |
| **Ordered**           | Items maintain insertion order      |
| **Mutable**           | You can modify items after creation |
| **Allows duplicates** | Yes                                 |
| **Heterogeneous**     | Can contain different data types    |

---

### **Creating Lists**

```python
numbers = [1, 2, 3, 4]
mixed = [1, "apple", True, 3.14]
empty = []
nested = [[1, 2], [3, 4]]
```

---

### **Accessing Elements**

```python
fruits = ["apple", "banana", "cherry"]
print(fruits[0])   # apple
print(fruits[-1])  # cherry (negative index starts from end)
```

---

### **Modifying Lists**

```python
fruits[1] = "blueberry"
fruits.append("orange")          # Add to end
fruits.insert(1, "mango")        # Add at position
fruits.remove("apple")           # Remove by value
removed = fruits.pop()           # Remove last item
del fruits[0]                    # Delete by index
fruits.clear()                   # Empty the list
```

---

### **List Slicing**

You can extract parts of a list:

```python
nums = [0, 1, 2, 3, 4, 5]
print(nums[1:4])    # [1, 2, 3]
print(nums[:3])     # [0, 1, 2]
print(nums[::2])    # [0, 2, 4]
```

---

### **List Operations**

```python
a = [1, 2, 3]
b = [4, 5]

print(a + b)     # Concatenation -> [1, 2, 3, 4, 5]
print(a * 2)     # Repeat -> [1, 2, 3, 1, 2, 3]
print(2 in a)    # Membership -> True
```

---

### **List Comprehensions**

A concise way to create lists.

```python
squares = [x**2 for x in range(5)]
# [0, 1, 4, 9, 16]
```

---

## **2. Tuples**

### **Definition**

A **tuple** is an **ordered, immutable** sequence of items.

```python
colors = ("red", "green", "blue")
```

---

### **Characteristics**

| Property              | Description                      |
| --------------------- | -------------------------------- |
| **Ordered**           | Yes                              |
| **Immutable**         | Cannot be changed after creation |
| **Allows duplicates** | Yes                              |
| **Heterogeneous**     | Yes                              |

---

### **Creating Tuples**

```python
t1 = (1, 2, 3)
t2 = ("a", 1, True)
t3 = ()                # Empty tuple
t4 = (5,)              # Single-element tuple needs comma
```

---

### **Accessing Elements**

```python
colors = ("red", "green", "blue")
print(colors[0])   # red
```

---

### **Tuple Packing and Unpacking**

```python
person = ("Nitin", 30, "India")
name, age, country = person
print(name)  # Nitin
```

---

### **Use Cases**

* When data should **not change** (e.g., configuration, coordinates)
* Faster than lists (due to immutability)
* Used as dictionary keys (since they are hashable)

---

## **3. Sets**

### **Definition**

A **set** is an **unordered, mutable** collection of **unique** elements.

```python
fruits = {"apple", "banana", "apple"}
print(fruits)  # {'apple', 'banana'}
```

---

### **Characteristics**

| Property          | Description                          |
| ----------------- | ------------------------------------ |
| **Unordered**     | No guaranteed order                  |
| **Mutable**       | You can add/remove elements          |
| **No duplicates** | Automatically removes duplicates     |
| **Unindexed**     | Elements accessed via iteration only |

---

### **Creating Sets**

```python
nums = {1, 2, 3}
empty_set = set()   # {} creates a dictionary, not a set
```

---

### **Modifying Sets**

```python
nums = {1, 2, 3}
nums.add(4)
nums.update([5, 6])
nums.remove(2)
nums.discard(10)    # No error if element missing
nums.clear()
```

---

### **Set Operations**

Sets support mathematical operations:

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)   # Union -> {1, 2, 3, 4, 5}
print(a & b)   # Intersection -> {3}
print(a - b)   # Difference -> {1, 2}
print(a ^ b)   # Symmetric difference -> {1, 2, 4, 5}
```

---

### **Frozen Sets**

An immutable version of a set.

```python
frozen = frozenset([1, 2, 3])
```

---

## **4. Dictionaries**

### **Definition**

A **dictionary** is an **unordered, mutable** collection of **key–value pairs**.

```python
user = {
    "name": "Nitin",
    "age": 30,
    "country": "India"
}
```

---

### **Characteristics**

| Property                                          | Description                    |
| ------------------------------------------------- | ------------------------------ |
| **Unordered (Python 3.6+: ordered by insertion)** | Maintains insertion order      |
| **Mutable**                                       | Yes                            |
| **Unique keys**                                   | Required                       |
| **Keys must be immutable**                        | e.g., strings, numbers, tuples |

---

### **Accessing Values**

```python
print(user["name"])          # Nitin
print(user.get("age"))       # 30
print(user.get("email", "N/A"))  # Default if missing
```

---

### **Adding & Updating**

```python
user["email"] = "nitin@example.com"
user.update({"country": "USA"})
```

---

### **Removing Items**

```python
user.pop("age")     # Remove by key
del user["name"]
user.clear()        # Empty dictionary
```

---

### **Iterating**

```python
for key, value in user.items():
    print(key, value)

for k in user.keys():
    print(k)

for v in user.values():
    print(v)
```

---

### **Nested Dictionaries**

```python
users = {
    "u1": {"name": "Nitin", "role": "admin"},
    "u2": {"name": "Arnav", "role": "developer"}
}
print(users["u1"]["role"])  # admin
```

---

### **Dictionary Comprehensions**

Like list comprehensions:

```python
squares = {x: x**2 for x in range(5)}
# {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}
```

---

## **Summary Comparison**

| Feature        | List                | Tuple      | Set          | Dictionary            |
| -------------- | ------------------- | ---------- | ------------ | --------------------- |
| **Ordered**    | Yes                 | Yes        | No           | Yes (insertion order) |
| **Mutable**    | Yes                 | No         | Yes          | Yes                   |
| **Duplicates** | Allowed             | Allowed    | Not allowed  | Keys: no, Values: yes |
| **Indexed**    | Yes                 | Yes        | No           | By key                |
| **Syntax**     | `[ ]`               | `( )`      | `{ }`        | `{key: value}`        |
| **Use Case**   | Dynamic collections | Fixed data | Unique items | Key-value mapping     |

---

## **Quick Practice Examples**

```python
# List
nums = [1, 2, 3]
nums.append(4)

# Tuple
coordinates = (10.5, 20.3)

# Set
unique_ids = {101, 102, 103}
unique_ids.add(104)

# Dictionary
employee = {"id": 1, "name": "Nitin", "role": "Lead"}
employee["role"] = "Architect"
```

---
