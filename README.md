# Numpy
## What is NumPy?

**NumPy** (short for *Numerical Python*) is the fundamental library for scientific computing in Python. It provides powerful data structures and functions for working with large arrays and matrices of numerical data. NumPy is widely used in data science, machine learning, scientific research, and engineering applications.

At its core, NumPy introduces the **ndarray** (N-dimensional array) object, which allows efficient storage and manipulation of numerical data.

---

## Why NumPy Instead of Python Lists?

While Python’s built-in lists are flexible and easy to use, they have limitations when working with numerical data. NumPy addresses these limitations in several ways:

### 🚀 Performance
- NumPy arrays are much faster than Python lists for numerical computations.
- Operations are implemented in optimized C code.

### 💾 Memory Efficiency
- NumPy uses less memory to store large numerical datasets.
- Data is stored in contiguous memory blocks.

### 🧮 Convenience
- Provides hundreds of built-in mathematical and statistical functions.
- Supports vectorized operations (no need for explicit loops).

### 🔬 Advanced Functionality
- Matrix multiplication
- Linear algebra operations
- Fourier transforms
- Random number generation

---

## Conclusion

NumPy is an essential library for numerical computing in Python. Its speed, memory efficiency, and rich functionality make it the foundation of many popular libraries such as Pandas, Matplotlib, SciPy, and scikit-learn.

Learning NumPy is a must for anyone starting in data science, machine learning, or scientific computing.


# Creating NumPy Arrays from Python Sequences

## Creating Arrays from Python Sequences

The most basic way to create a NumPy array is by converting a Python sequence such as a **list** or a **tuple**.  
The `numpy.array()` function takes a sequence as input and returns a new NumPy array.

---

## Understanding NumPy Arrays

Before creating arrays, it is important to understand what makes NumPy arrays special.

### Array Dimensions

- **1D Array (Vector):**  
  A simple list of numbers  
  Example: `[1, 2, 3, 4]`

- **2D Array (Matrix):**  
  A table of numbers with rows and columns (similar to a spreadsheet)

- **3D Array (Tensor):**  
  A cube of numbers, commonly used for images or 3D data

---

## Key Differences from Python Lists

- **Homogeneous:**  
  All elements must be of the same data type (usually numbers)

- **Fixed Size:**  
  Once created, the size of a NumPy array cannot be changed

- **Efficient:**  
  Much faster than Python lists for mathematical operations

- **Rich Functionality:**  
  Supports vectorized operations (operations on entire arrays at once)

---

## Importing NumPy

NumPy is imported using the standard alias `np`:

```python

# Import NumPy
import numpy as np

# Create a 1D array from a list
a1D = np.array([1, 2, 3, 4])
print("1D Array:")
print(a1D)

# Create a 2D array from a list of lists
a2D = np.array([[1, 2], [3, 4]])
print("\n2D Array:")
print(a2D)

# Create a 3D array from nested lists
a3D = np.array([[[1, 2], [3, 4]], [[5, 6], [7, 8]]])
print("\n3D Array:")
print(a3D)

# Creating an array with a specified data type
complex_array = np.array([1, 2], dtype=complex)
print("\nArray with complex data type:")
print(complex_array)
```
Output
```
1D Array:
[1 2 3 4]

2D Array:
[[1 2]
 [3 4]]

3D Array:
[[[1 2]
  [3 4]]

 [[5 6]
  [7 8]]]
```

## Understanding Data Types (`dtype`)

NumPy arrays have a **fixed data type** for all elements, specified using the `dtype` parameter.  
This differs from Python lists, where each element can have a different type.

### Why Data Types Matter

- **Memory Efficiency:** Different types use different amounts of memory.
- **Performance:** Operations are optimized for specific data types.
- **Precision:** Controls how numbers are stored and calculated.

### Common Data Types

| Data Type | Description |
|-----------|-------------|
| `int32` / `int64` | Integer numbers (32 or 64 bits) |
| `float32` / `float64` | Decimal numbers (32 or 64 bits) |
| `complex` | Complex numbers |
| `bool` | True/False values |

### Specifying a Data Type

You can explicitly define the data type when creating an array:

```python
import numpy as np

# Integer array
int_array = np.array([1, 2, 3], dtype=np.int32)
print("Integer array:", int_array, "dtype:", int_array.dtype)

# Float array
float_array = np.array([1.0, 2.0, 3.0], dtype=np.float64)
print("Float array:", float_array, "dtype:", float_array.dtype)

# Complex array
complex_array = np.array([1, 2], dtype=complex)
print("Complex array:", complex_array, "dtype:", complex_array.dtype)

# Boolean array
bool_array = np.array([True, False, True], dtype=bool)
print("Boolean array:", bool_array, "dtype:", bool_array.dtype)
```
`Note`: If you don’t specify a `dtype`, NumPy automatically chooses the most suitable type based on the input data.

## Using Intrinsic Array Creation Functions
NumPy provides several built-in functions to create arrays from scratch without needing a Python sequence. These functions are optimized for specific use cases and are much faster than manually creating arrays from lists.

## Why Use These Functions?
Instead of writing np.array([0, 0, 0, 0, 0]), you can simply use np.zeros(5). These functions are:

- **Faster:** Optimized C code under the hood
- **More readable:** Intent is clear from the function name
- **Memory efficient:** Direct memory allocation
- **Convenient:** No need to manually specify each element


```python
import numpy as np

# Create an array with a range of elements
# np.arange(start, stop, step) - similar to Python's range()
# Use case: Creating sequences for loops, generating indices
arr_range = np.arange(0, 10, 2)  # [0, 2, 4, 6, 8]
print("Array from arange:")
print(arr_range)

# Create an array with a specific number of elements between two points
# np.linspace(start, stop, num_elements) - evenly spaced points
# Use case: Creating points for plotting, sampling data
arr_linspace = np.linspace(0, 10, 5)  # 5 points from 0 to 10
print("\nArray from linspace:")
print(arr_linspace)

# Create an array filled with zeros
# np.zeros((rows, columns)) - initialize arrays for calculations
# Use case: Pre-allocating arrays before filling with computed values
arr_zeros = np.zeros((2, 3))  # 2x3 array of zeros
print("\nArray of zeros:")
print(arr_zeros)

# Create an array filled with ones
# np.ones((rows, columns)) - initialize with ones
# Use case: Creating masks, scaling factors, or starting points for algorithms
arr_ones = np.ones((3, 2))  # 3x2 array of ones
print("\nArray of ones:")
print(arr_ones)

# Create an identity matrix
# np.eye(size) - square matrix with 1s on diagonal, 0s elsewhere
# Use case: Linear algebra, resetting transformations, matrix multiplication
identity_matrix = np.eye(3)  # 3x3 identity matrix
print("\nIdentity matrix:")
print(identity_matrix)
```
Output
```
Array from arange:
[0 2 4 6 8]

Array from linspace:
[ 0.   2.5  5.   7.5 10. ]

Array of zeros:
[[0. 0. 0.]
 [0. 0. 0.]]

Array of ones:
[[1. 1.]
 [1. 1.]
 [1. 1.]]

Identity matrix:
[[1. 0. 0.]
 [0. 1. 0.]
 [0. 0. 1.]]
```

## Manipulating Existing Arrays
You can also create new arrays by modifying, combining, or splitting existing ones. This section covers two important concepts: views vs. copies and array concatenation.

## Views vs. Copies: Understanding Memory Sharing
This is one of the most important concepts in NumPy that often confuses beginners.

### What is a View?
A view is a different way of looking at the same data in memory. When you create a view (like through slicing), you're not creating a new array - you're just creating a new reference to the existing data.

### What is a Copy?
A copy creates a completely new array in memory with its own data. Changes to a copy don't affect the original array, and vice versa.

### Why This Matters
- Views are memory efficient: They don't duplicate data
- Views are fast: No copying overhead
- But views can cause unexpected side effects: Modifying a view changes the original data
- Copies are safer: Changes are isolated but use more memory

```python
import numpy as np

# --- Part 1: Views vs. Copies ---
a = np.arange(1, 5)
print("Original array 'a':", a)

# Create a view of the first two elements
b = a[:2]
b[0] = 99 # Modify the view
print("Modified view 'b':", b)
print("Array 'a' after modifying the view:", a) # 'a' is also changed

# Create a copy
c = a[:2].copy()
c[0] = 0 # Modify the copy
print("\nModified copy 'c':", c)
print("Array 'a' after modifying the copy:", a) # 'a' is unchanged

# --- Part 2: Joining Arrays ---
A = np.ones((2, 2))
B = np.eye(2) * 2
C = np.zeros((2, 2))
D = np.diag((-3, -4))

# Join arrays into a block matrix
block_matrix = np.block([
    [A, B],
    [C, D]
])
print("\nBlock matrix:")
print(block_matrix)
```
Output
```
Original array 'a': [1 2 3 4]
Modified view 'b': [99  2]
Array 'a' after modifying the view: [99  2  3  4]

Modified copy 'c': [0 2]
Array 'a' after modifying the copy: [99  2  3  4]

Block matrix:
[[ 1.  1.  2.  0.]
 [ 1.  1.  0.  2.]
 [ 0.  0. -3.  0.]
 [ 0.  0.  0. -4.]]
```

## Reading Arrays from a File
A common task in data analysis is to load data from a file into a NumPy array. NumPy excels at this because it can efficiently read large datasets and automatically convert them into the appropriate numerical formats.

## Why NumPy for File I/O?
- Speed: Much faster than reading line-by-line with Python
- Type inference: Automatically detects appropriate data types
- Memory efficiency: Loads data directly into optimized arrays
- Convenience: Single function call instead of complex parsing
- Common File Formats
- CSV files: Comma-separated values (most common)
- TSV files: Tab-separated values
- Text files: Space or custom delimiter separated
- Binary files: For very large datasets (advanced)
For simple text files like CSV (Comma-Separated Values), NumPy provides the `np.loadtxt()` function.

CSV File
```CSV
col1,col2,col3
1.0,2.5,3.2
4.5,5.0,6.8
7.3,8.1,9.9
```

### Understanding np.loadtxt Parameters
The np.loadtxt() function has several important parameters:

- delimiter=',': Specifies how columns are separated (comma for CSV)
- skiprows=1: Skips the first row (usually headers)
- dtype: Optional - specifies data type (auto-detected if not provided)
- usecols: Optional - specifies which columns to read
- comments: Optional - specifies comment character to ignore lines

We use `delimiter=','` to specify that columns are separated by commas and skiprows=1 to ignore the header row.
```python
import numpy as np

# Load data from the CSV file
try:
    # Relative paths will cause validation to fail, please use absolute paths in the lab
    data = np.loadtxt('/home/labex/project/data.csv', delimiter=',', skiprows=1)
    print("Data loaded from data.csv:")
    print(data)
except IOError:
    print("Error: data.csv not found.")
```

Output
```
Data loaded from data.csv:
[[1.  2.5 3.2]
 [4.5 5.  6.8]
 [7.3 8.1 9.9]]
```
This method is very efficient for loading structured numerical data into arrays for further processing.

## Summary
In this lab, you have learned the fundamental techniques for creating `NumPy arrays`. You practiced creating arrays from Python lists, using intrinsic functions like `np.arange` and `np.zeros`, manipulating existing arrays through `views`, `copies`, and `joining`, and loading data from a text file using `np.loadtxt`.

These skills are the building blocks for nearly all numerical and scientific computing tasks you will perform with Python. With a solid understanding of array creation, you are now ready to explore more advanced array manipulation and mathematical operations in `NumPy`.
