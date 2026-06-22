# Source: https://coursify.hasanraiyan.me/research/numpy-for-beginners-a-comprehensive-introduction

NumPy for Beginners: A Comprehensive Introduction

# 

NumPy for Beginners: A Comprehensive Introduction

Verified Sources

Jun 16, 2026

## AI Summary

[NumPy](https://numpy.org) (Numerical Python) is the foundational library for numerical computing in Python. It provides support for large, multi-dimensional arrays and matrices, along with a vast collection of mathematical functions to operate on them. NumPy is the backbone of the scientific Python ecosystem, serving as the core data structure for libraries like Pandas, SciPy, Scikit-learn, TensorFlow, and PyTorch .

At the heart of NumPy is the ndarray, a high-performance data structure that stores elements of the same type in contiguous memory blocks. This design makes NumPy arrays significantly faster and more memory-efficient than Python lists, which store references to scattered objects .

**Why NumPy over Python lists?**

| Feature | Python List | NumPy Array |
| --- | --- | --- |
| Element type | Heterogeneous | Homogeneous |
| Memory | Scattered references | Contiguous block |
| Speed | Slow (per-element loop) | Fast (vectorized C backend) |
| Broadcasting | Not supported | Supported |
| Vectorized math | Requires loops | Built-in |

NumPy's performance advantage comes from its C-based implementation. When you perform an operation on a NumPy array, the looping happens in compiled C code — not in interpreted Python — yielding speedups of 10–100× for numerical operations .

## Footnotes

1. [NumPy: the absolute basics for beginners](https://numpy.org/doc/stable/user/absolute_beginners.html) - Official NumPy beginner documentation covering array creation, operations, and indexing. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
2. [Advantages of Using NumPy Arrays Over Python Lists](https://medium.com/@work.hansdarmawan001/advantages-of-using-numpy-arrays-over-python-lists-for-numerical-computation-7e3973645d98) - Comparison of NumPy arrays vs Python lists covering speed, memory, and functionality. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-2) [↩2](https://coursify.hasanraiyan.me/#user-content-fnref-2-2)
 

#### Python NumPy Tutorial for Beginners

### Core Concepts: The ndarray

Every NumPy array is an instance of `ndarray`. Key attributes you should know:

- **`ndim`** — number of dimensions (axes)
- **`shape`** — tuple of integers indicating size along each axis
- **`size`** — total number of elements (size\=∏shapei\\text{size} = \\prod \\text{shape}\_isize\=∏shapei​)
- **`dtype`** — data type of elements (e.g., `int64`, `float64`)

total\_elements\=∏i\=0ndim−1shape\[i\]\\text{total\\\_elements} = \\prod\_{i=0}^{\\text{ndim}-1} \\text{shape}\[i\]total\_elements\=∏i\=0ndim−1​shape\[i\]

`1import numpy as np 2 3a = np.array([[1, 2, 3], [4, 5, 6]]) 4print(a.ndim)    # 2 5print(a.shape)   # (2, 3) 6print(a.size)    # 6 7print(a.dtype)   # int64`

### 

NumPy Development History

#### Numeric (Predecessor)

1995

Jim Hugunin created Numeric, the first array computing package for Python, laying the groundwork for scientific computing."

#### Numarray Created

2001

A competing array package called numarray was developed, offering improved features but fragmenting the community."

#### NumPy Born

2005

Travis Oliphant unified Numeric and numarray into NumPy 1.0, combining the best of both packages into a single library."

#### Ecosystem Grows

2010

Scipy, Pandas, and Matplotlib adopt NumPy arrays as their core data structure, establishing the SciPy stack."

#### NumPy 1.20+

2020

Type hints, SIMD optimizations, and improved C API. NumPy becomes essential infrastructure for AI/ML boom."

#### NumPy 2.0

2024

Major release with new API changes, improved string operations, and enhanced performance via BLAS/LAPACK integration."

### Creating Arrays

NumPy provides many convenience functions for creating arrays :

`1import numpy as np 2 3# From a Python list 4a = np.array([1, 2, 3, 4])               # 1D array 5b = np.array([[1, 2], [3, 4]])            # 2D array 6 7# Built-in creation functions 8zeros = np.zeros((3, 4))                  # 3×4 array of 0.0 9ones  = np.ones((2, 3))                   # 2×3 array of 1.0 10full  = np.full((2, 2), 7)                # 2×2 array of 7 11eye   = np.eye(3)                         # 3×3 identity matrix 12 13# Range-based creation 14arange = np.arange(0, 10, 2)             # [0, 2, 4, 6, 8] 15linspace = np.linspace(0, 1, 5)          # [0.0, 0.25, 0.5, 0.75, 1.0] 16 17# Random creation 18rand = np.random.rand(2, 3)              # 2×3 array, uniform [0, 1) 19randint = np.random.randint(0, 10, size=5)  # 5 random ints in [0, 10)`

You can also explicitly set the `dtype` to control memory usage:

`1a = np.array([1, 2, 3], dtype=np.float32)  # 32-bit float 2b = np.array([1, 2, 3], dtype=np.int8)     # 8-bit integer`

## Footnotes

1. [NumPy: the absolute basics for beginners](https://numpy.org/doc/stable/user/absolute_beginners.html) - Official NumPy beginner documentation covering array creation, operations, and indexing. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

### Installing and Setting Up NumPy

1. 1
 
 Step 1
 
 Install Python
 
 Ensure Python 3.9+ is installed on your system. Verify with `python --version` in your terminal.
 
2. 2
 
 Step 2
 
 Install NumPy
 
 Use pip to install NumPy:
 
 `1pip install numpy`
 
 Or with conda:
 
 `1conda install numpy`
 
3. 3
 
 Step 3
 
 Verify Installation
 
 Open a Python REPL and run:
 
 `1import numpy as np 2print(np.__version__)`
 
 You should see the version number printed, confirming a successful installation.
 
4. 4
 
 Step 4
 
 Import NumPy in Your Code
 
 Always use the standard import convention:
 
 `1import numpy as np`
 
 This convention is used universally in the scientific Python community and in official documentation .
 
 ## Footnotes
 
 1. [NumPy: the absolute basics for beginners](https://numpy.org/doc/stable/user/absolute_beginners.html) - Official NumPy beginner documentation covering array creation, operations, and indexing. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 
 

### Array Indexing and Slicing

NumPy extends Python's indexing syntax to support multi-dimensional access. Understanding the difference between a view and a copy is critical .

**Basic indexing and slicing** uses the `start:stop:step` syntax in each dimension:

`1a = np.array([[1, 2, 3, 4], 2              [5, 6, 7, 8], 3              [9, 10, 11, 12]]) 4 5# Single element 6a[0, 1]          # 2 7 8# Entire row 9a[1, :]          # array([5, 6, 7, 8]) 10 11# Entire column 12a[:, 2]          # array([3, 7, 11]) 13 14# Sub-array (slice) 15a[0:2, 1:3]      # array([[2, 3], [6, 7]]) 16 17# Step slicing 18a[::2, ::2]      # array([[1, 3], [9, 11]])`

**Boolean indexing** filters elements using a condition:

`1a = np.array([10, 40, 80, 50, 100]) 2a[a > 50]        # array([80, 100])`

**Fancy indexing** (also called integer array indexing) lets you select arbitrary elements :

`1a = np.array([10, 20, 30, 40, 50]) 2indices = np.array([0, 3, 4]) 3a[indices]       # array([10, 40, 50])`

## Footnotes

1. [Basic Slicing and Advanced Indexing in NumPy](https://www.geeksforgeeks.org/python/numpy-slicing-and-indexing) - Detailed guide on slicing, boolean, and fancy indexing with view vs copy behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 
2. [Indexing on ndarrays — NumPy v2.4 Manual](https://numpy.org/doc/stable/user/basics.indexing.html) - Official documentation on NumPy indexing including advanced and broadcast indexing. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-4)
 

#### Views vs. Copies

Slicing returns a **view** — modifying the view modifies the original array! Use `.copy()` to create an independent copy when needed:

`1b = a[0:2].copy()  # Safe: changes to b won't affect a`

Failing to understand this distinction is one of the most common sources of bugs for NumPy beginners .

## Footnotes

1. [Basic Slicing and Advanced Indexing in NumPy](https://www.geeksforgeeks.org/python/numpy-slicing-and-indexing) - Detailed guide on slicing, boolean, and fancy indexing with view vs copy behavior. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-3)
 

more...

1D Array

2D Array3D Array

`1a = np.array([10, 20, 30, 40, 50]) 2 3# Access 4a[0]        # 10 5a[-1]       # 50 6 7# Slice 8a[1:4]      # array([20, 30, 40]) 9a[::2]      # array([10, 30, 50]) 10a[::-1]     # array([50, 40, 30, 20, 10])`

### Broadcasting

Broadcasting is one of NumPy's most powerful features. It allows you to perform arithmetic operations between arrays of different shapes without explicitly replicating data .

**Broadcasting rules:**

1. If arrays have different numbers of dimensions, the smaller shape is left-padded with 1s.
2. If the shape along any dimension doesn't match, the dimension with size 1 is stretched.
3. If dimensions are incompatible (neither is 1), an error is raised.

Result shapei\=max⁡(Ai,  Bi)where  Ai\=1  or  Bi\=1  or  Ai\=Bi\\text{Result shape}\_i = \\max(A\_i,\\; B\_i) \\quad \\text{where}\\; A\_i = 1 \\;\\text{or}\\; B\_i = 1 \\;\\text{or}\\; A\_i = B\_iResult shapei​\=max(Ai​,Bi​)whereAi​\=1orBi​\=1orAi​\=Bi​

| Array A Shape | Array B Shape | Result Shape | Compatible? |
| --- | --- | --- | --- |
| (5, 4) | (1,) | (5, 4) | ✅ |
| (5, 4) | (4,) | (5, 4) | ✅ |
| (15, 3, 5) | (15, 1, 5) | (15, 3, 5) | ✅ |
| (3, 4) | (3,) | — | ❌ |

`1# Scalar broadcast 2data = np.array([1.0, 2.0, 3.0]) 3data * 1.6       # array([1.6, 3.2, 4.8]) 4 5# 2D + 1D broadcast 6a = np.array([[0.0, 10.0, 20.0, 30.0]])  # shape (1, 4) 7b = np.array([1.0, 2.0, 3.0])            # shape (3,) 8a.T + b  # shape (4, 3) — via newaxis trick 9 10# The newaxis trick 11a = np.array([0.0, 10.0, 20.0, 30.0])    # shape (4,) 12b = np.array([1.0, 2.0, 3.0])            # shape (3,) 13a[:, np.newaxis] + b                     # shape (4, 3)`

## Footnotes

1. [Broadcasting — NumPy v2.4 Manual](https://numpy.org/doc/stable/user/basics.broadcasting.html) - Official NumPy broadcasting rules with examples and practical use cases. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

#### Broadcasting Performance Tip

Broadcasting avoids creating large intermediate arrays in memory. Instead of explicitly replicating data with `np.tile()` or `np.repeat()`, let broadcasting do the work. This can reduce memory usage by orders of magnitude for large datasets .

## Footnotes

1. [Broadcasting — NumPy v2.4 Manual](https://numpy.org/doc/stable/user/basics.broadcasting.html) - Official NumPy broadcasting rules with examples and practical use cases. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-5)
 

more...

### Mathematical and Statistical Operations

NumPy provides ufuncs for fast element-wise computation . These include:

**Arithmetic operations** (element-wise):

`1a = np.array([20, 30, 40, 50]) 2b = np.arange(4)               # [0, 1, 2, 3] 3 4a - b          # array([20, 29, 38, 47]) 5b ** 2         # array([0, 1, 4, 9]) 610 * np.sin(a) # element-wise trig 7a < 35         # array([True, True, False, False])`

**Matrix operations** (not element-wise):

`1A = np.array([[1, 1], [0, 1]]) 2B = np.array([[2, 0], [3, 4]]) 3 4A * B         # element-wise product 5A @ B         # matrix product (Python 3.5+) 6A.dot(B)      # matrix product (alternative syntax)`

**Aggregation along axes:**

`1b = np.arange(12).reshape(3, 4) 2# array([[ 0,  1,  2,  3], 3#        [ 4,  5,  6,  7], 4#        [ 8,  9, 10, 11]]) 5 6b.sum(axis=0)      # sum of each column: array([12, 15, 18, 21]) 7b.min(axis=1)      # min of each row:    array([0, 4, 8]) 8b.cumsum(axis=1)   # cumulative sum along rows 9b.mean()           # 5.5 10b.std()            # 3.452...`

## Footnotes

1. [NumPy quickstart — NumPy v2.4 Manual](https://numpy.org/doc/stable/user/quickstart.html) - Official quickstart covering basic operations, universal functions, and indexing. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-6)
 

### 

NumPy vs Python List: Operation Speed Comparison

Execution time for adding 1,000,000 elements (lower is better)

### Reshaping and Array Manipulation

One of the most common tasks is reshaping — reorganizing the same data into a different shape :

`1a = np.arange(12)               # shape (12,) 2b = a.reshape(3, 4)             # shape (3, 4)  — view 3c = a.reshape(2, 2, 3)          # shape (2, 2, 3) — view 4 5# Flattening 6d = b.ravel()                    # shape (12,) — view if possible 7e = b.flatten()                  # shape (12,) — always a copy 8 9# Transposing 10f = b.T                          # shape (4, 3) 11 12# Stacking arrays 13v = np.vstack([b, b])           # vertical stack: shape (6, 4) 14h = np.hstack([b, b])           # horizontal stack: shape (3, 8)`

```
Key rule for reshaping: the total number of elements must remain the same, i.e., $\prod \text{new\_shape} = \text{original\_size}$.
```

## Footnotes

1. [NumPy: the absolute basics for beginners](https://numpy.org/doc/stable/user/absolute_beginners.html) - Official NumPy beginner documentation covering array creation, operations, and indexing. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-1)
 

### Linear Algebra with NumPy

NumPy's `linalg` module provides essential linear algebra operations. These functions rely on optimized BLAS and LAPACK libraries for high performance :

`1import numpy as np 2 3A = np.array([[1, 2], [3, 4]]) 4B = np.array([[5, 6], [7, 8]]) 5 6# Matrix multiplication 7C = A @ B                       # or np.dot(A, B) 8 9# Determinant 10det = np.linalg.det(A)          # -2.0 11 12# Inverse 13A_inv = np.linalg.inv(A) 14 15# Eigenvalues and eigenvectors 16eigenvalues, eigenvectors = np.linalg.eig(A) 17 18# Solving linear systems Ax = b 19b = np.array([1, 2]) 20x = np.linalg.solve(A, b) 21 22# Singular Value Decomposition 23U, S, Vt = np.linalg.svd(A)`

## Footnotes

1. [Linear algebra — NumPy v2.4 Manual](https://numpy.org/doc/2.4/reference/routines.linalg.html) - Official reference for NumPy linear algebra routines backed by BLAS/LAPACK. [↩](https://coursify.hasanraiyan.me/#user-content-fnref-7)
 

### Common NumPy Questions

What is the difference between np.array() and np.asarray()?

When should I use np.copy() vs. slicing?

What does axis=0 vs axis=1 mean in aggregation?

How do I handle incompatible shapes in broadcasting?

Is NumPy faster than pure Python for all operations?

#### In-place Operations Can Be Dangerous

Operators like `+=` and `*=` modify **in place** without creating a new array. This can cause unexpected behavior with views:

`1a = np.array([1, 2, 3, 4]) 2b = a[0:2]  # b is a VIEW of a 3b += 10     # a is now [11, 12, 3, 4]!`

Always use `.copy()` if you need independence.

more...

### Broadcasting Dimensions — Visual Summary

Understanding how NumPy stretches dimensions is essential. Here is a step-by-step walkthrough of broadcasting a `(4, 1)` array with a `(1, 3)` array to produce a `(4, 3)` result:

### Building a NumPy Workflow from Scratch

1. 1
 
 Step 1
 
 Import NumPy
 
 Start every script with:
 
 `1import numpy as np`
 
2. 2
 
 Step 2
 
 Create or Load Data
 
 Create arrays from lists or built-in functions:
 
 `1data = np.array([[1, 2], [3, 4], [5, 6]]) 2zeros = np.zeros((10, 3))`
 
3. 3
 
 Step 3
 
 Inspect the Array
 
 Always verify shape and dtype before operating:
 
 `1print(data.shape)  # (3, 2) 2print(data.dtype)  # int64 3print(data.ndim)   # 2`
 
4. 4
 
 Step 4
 
 Perform Operations
 
 Use vectorized operations instead of loops:
 
 `1means = data.mean(axis=0)     # column means 2normalized = data - means      # broadcasting!`
 
5. 5
 
 Step 5
 
 Reshape and Export
 
 Reshape for downstream tools and save results:
 
 `1flattened = normalized.flatten() 2np.save('output.npy', normalized)`
 

### Knowledge Check

Question 1 of 5

Q1Single choice

What is the result of `np.array([1, 2, 3]) + np.array([4, 5, 6])`?

np.array(\[5, 7, 9\])

np.array(\[\[5, 7, 9\]\])

np.array(\[4, 10, 18\])

np.array(\[1, 2, 3, 4, 5, 6\])

BackNext

## Explore Related Topics

[1\\ \\ Machine Learning Basics\\ \\ Machine learning is an AI subfield that creates models to learn patterns from data and generalize to unseen examples, following a pipeline from data collection to deployment.\\ \\ - Three main paradigms: supervised (labeled data), unsupervised (structure discovery), and reinforcement learning (trial‑and‑error with rewards). - High‑quality data, feature engineering, and proper train/validation/test splits are essential for performance. - Overfitting (high training accuracy, poor validation) and underfitting (low performance) are identified via loss curves and bias‑variance trade‑off. - Start with simple baseline algorithms (linear/logistic regression, trees, forests) before advancing to complex models.](https://coursify.hasanraiyan.me/research/machine-learning-basics) [2\\ \\ The Comprehensive Data Scientist Roadmap: From Foundations to Specialization\\ \\ Data science sits at the intersection of mathematics, computer science, and domain expertise. A modern Data Scientist must navigate a complex ecosystem of tools, algorithms, and business strategies to transform raw data into actionable intelligence. This roadmap provides a structured, rigorous pathw](https://coursify.hasanraiyan.me/research/the-comprehensive-data-scientist-roadmap-from-foundations-to-specialization) [3\\ \\ Learn Python in 30 Days\\ \\ Python is one of the most versatile and in-demand programming languages in the world. Created by Guido van Rossum and first released on February 20, 1991, Python has grown from a hobby project to the 1 programming language on the TIOBE Index as of 2024 . With over 18.2 million active developers worl](https://coursify.hasanraiyan.me/research/learn-python-in-30-days)

[![Coursify logo](https://coursify.hasanraiyan.me/_next/image?url=%2Fimages%2Fapps%2Fcoursify.png&w=48&q=75)Browse all research articles](https://coursify.hasanraiyan.me/research)