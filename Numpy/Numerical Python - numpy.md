Below is a **beginner-friendly, clear, structured introduction to NumPy**, perfect for someone starting Python development.

---

# Introduction to NumPy

NumPy (Numerical Python) is a foundational library used for:

* Scientific computing
* Data analysis
* Machine learning
* Array operations
* Mathematical functions
* Vectorized operations (very fast)

It powers libraries like pandas, TensorFlow, PyTorch, and scikit-learn.

---

# Why NumPy?

NumPy arrays are:

* Much faster than Python lists
* Use less memory
* Enable vectorized operations
* Support mathematical operations on entire arrays
* Provide powerful broadcasting
* Integrate with ML tools, FastAPI, data pipelines

Example difference:

Python list:

```python
result = [x * 2 for x in [1, 2, 3]]
```

NumPy array:

```python
import numpy as np

a = np.array([1, 2, 3])
result = a * 2
```

NumPy automatically applies operations to whole arrays.

---

# Installing NumPy

```
pip install numpy
```

Or with Poetry:

```
poetry add numpy
```

---

# Basic NumPy Array Creation

### From a Python list:

```python
import numpy as np

arr = np.array([1, 2, 3, 4])
```

### 2D array:

```python
arr = np.array([[1, 2], [3, 4]])
```

### Custom arrays:

```python
np.zeros((3, 3))    # 3x3 matrix of 0s
np.ones((2, 2))     # 2x2 matrix of 1s
np.full((2, 3), 7)  # 2x3 matrix filled with 7
np.eye(3)           # Identity matrix
```

### Random values:

```python
np.random.rand(3, 3)   # uniform distribution
np.random.randn(3, 3)  # normal distribution
```

---

# Array Properties

```python
a = np.array([[1, 2, 3], [4, 5, 6]])

a.shape      # (2, 3)
a.ndim       # 2 dimensions
a.size       # total elements = 6
a.dtype      # data type, e.g., int64
```

---

# Indexing and Slicing

NumPy indexing looks like Python lists but supports multi-dimensional access.

```python
a = np.array([[10, 20, 30], [40, 50, 60]])

a[0, 1]    # 20
a[:, 1]    # entire column: [20, 50]
a[1, :]    # entire row: [40, 50, 60]
a[0:2, 1:] # slice rows & columns
```

---

# Vectorized Operations

NumPy can apply operations to entire arrays without loops.

```python
a = np.array([1, 2, 3])

a + 10     # [11, 12, 13]
a * 2      # [2, 4, 6]
a ** 2     # [1, 4, 9]
```

Element-wise operations (no looping manually).

---

# Mathematical Functions

NumPy has hundreds of built-in mathematical functions:

```python
np.sum(a)
np.mean(a)
np.min(a)
np.max(a)
np.std(a)
np.sqrt(a)
np.log(a)
```

---

# Matrix Operations

Matrix multiplication:

```python
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6], [7, 8]])

np.dot(a, b)
# or
a @ b
```

Transpose:

```python
a.T
```

---

# Broadcasting

Broadcasting allows NumPy to combine arrays of different shapes.

Example:

```python
a = np.array([1, 2, 3])
b = 10

a + b
# Output: [11, 12, 13]
```

More advanced example:

```python
matrix = np.array([[1, 2, 3],
                   [4, 5, 6]])

vector = np.array([10, 20, 30])

matrix + vector
```

NumPy automatically stretches the vector to match the matrix shape.

---

# Boolean Filtering (Very Important)

```python
a = np.array([1, 2, 3, 4, 5])

a[a > 3]        # [4, 5]
a[a % 2 == 0]   # even numbers
```

---

# Modifying Arrays

Reshape:

```python
a = np.array([1, 2, 3, 4, 5, 6])
a.reshape((2, 3))
```

Concatenate:

```python
np.concatenate([arr1, arr2])
```

Flatten:

```python
a.flatten()
```

---

# Loading and Saving Data

Save as `.npy` file:

```python
np.save("data.npy", arr)
```

Load:

```python
data = np.load("data.npy")
```

Save/load CSV:

```python
np.savetxt("data.csv", arr, delimiter=",")
np.loadtxt("data.csv", delimiter=",")
```

---

# Working With Large Datasets

NumPy is extremely efficient for:

* mathematical operations
* ML pipelines
* vectorized transformations
* data preprocessing

It is much faster than Python loops.

Example:

Python loop:

```python
result = [x * 2 for x in range(1_000_000)]
```

NumPy:

```python
arr = np.arange(1_000_000)
result = arr * 2
```

NumPy is often 20–100x faster.

---

# Summary

You learned:

* What NumPy is
* How to create arrays
* Array properties
* Indexing and slicing
* Vectorized operations
* Mathematical functions
* Matrix operations
* Broadcasting
* Boolean filtering
* Saving and loading data
* Performance advantages

NumPy is essential for:

* Machine learning
* Data engineering
* Data science
* Mathematical computing
* Image processing

If you're planning to use pandas or machine learning later, learning NumPy is a must.

---

