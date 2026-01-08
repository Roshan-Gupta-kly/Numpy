# Broadcasting
## Broadcasting a Scalar to an Array
The simplest form of broadcasting occurs when you perform an operation between an array and a single number (a scalar). NumPy automatically "stretches" or "broadcasts" the scalar to match the shape of the array.

```python
import numpy as np

# Create a 1D array
a = np.array([1.0, 2.0, 3.0])

# Define a scalar
b = 2.0

# Multiply the array by the scalar
# The scalar 'b' is broadcast to the shape of 'a'
result = a * b

print("Array 'a':", a)
print("Scalar 'b':", b)
print("Result of a * b:", result)
```

output
```
Array 'a': [1. 2. 3.]  
Scalar 'b': 2.0
Result of a * b: [2. 4. 6.]
```
## Broadcasting Two Arrays with Compatible Shapes
Broadcasting also works between two arrays if their shapes are compatible. The general rule for compatibility is: when comparing the dimensions of two arrays from right to left, each pair of dimensions must either be equal or one of them must be 1.

```python
import numpy as np

# Create a 2D array (shape: 2, 3)
a = np.array([[1.0, 2.0, 3.0],
              [4.0, 5.0, 6.0]])

# Create a 1D array (shape: 3,)
b = np.array([10.0, 20.0, 30.0])

# Add the two arrays
# 'b' is broadcast to shape (2, 3) to match 'a'
# It becomes [[10. 20. 30.], [10. 20. 30.]] internally
result = a + b

print("Array 'a' (shape {}):\n{}".format(a.shape, a))
print("Array 'b' (shape {}): {}".format(b.shape, b))
print("Result of a + b:\n", result)
```

output
```
Array 'a' (shape (2, 3)):
[[1. 2. 3.]
 [4. 5. 6.]]
Array 'b' (shape (3,)): [10. 20. 30.]
Result of a + b:
 [[11. 22. 33.]
 [14. 25. 36.]]
```
## Understanding Incompatible Shapes
Broadcasting will fail if the arrays' shapes are not compatible according to the rules. This results in a `ValueError`. Understanding when this happens is crucial for debugging.

Let's try an operation with incompatible shapes. Here, we will attempt to add an array of shape `(2, 3)` with an array of shape `(2,)`. NumPy compares the trailing dimensions `(3 and 2)`, finds they are not equal, and neither is `1`. This will cause an `error`.

```python
import numpy as np

# Create a 2D array (shape: 2, 3)
a = np.array([[1.0, 2.0, 3.0],
              [4.0, 5.0, 6.0]])

# Create an incompatible 1D array (shape: 2,)
b = np.array([1.0, 2.0])

print("Array 'a' (shape {}):\n{}".format(a.shape, a))
print("Array 'b' (shape {}): {}".format(b.shape, b))

# This will raise a ValueError
try:
    result = a + b
except ValueError as e:
    print("\nError:", e)
```

output
```
Array 'a' (shape (2, 3)):
[[1. 2. 3.]
 [4. 5. 6.]]
Array 'b' (shape (2,)): [1. 2.]

Error: operands could not be broadcast together with shapes (2,3) (2,)
```

## Practical Example - Vector Quantization
Let's apply broadcasting to a practical problem. Vector Quantization (VQ) is a technique used in data compression and classification. A key step is to find the closest "code" vector from a "codebook" to a given "observation" vector. Broadcasting makes this calculation efficient.

Imagine we have an observation (e.g., an athlete's weight and height) and a codebook of different athlete types. We want to find which type our observation is closest to.

```python
import numpy as np

# An observation vector (e.g., weight, height)
observation = np.array([111.0, 188.0])

# A codebook of vectors
codes = np.array([[102.0, 203.0],
                  [132.0, 193.0],
                  [45.0, 155.0],
                  [57.0, 173.0]])

# Use broadcasting to subtract the observation from all codes at once
# observation (2,) is broadcast to (4, 2)
diff = codes - observation

# Calculate the squared Euclidean distance
dist_sq = np.sum(diff**2, axis=-1)

# Find the index of the minimum distance
closest_index = np.argmin(dist_sq)

# Get the closest code from the codebook
closest_code = codes[closest_index]

print("Observation:", observation)
print("Codebook:\n", codes)
print("Distances squared:", dist_sq)
print("Closest code index:", closest_index)
print("Closest code:", closest_code)
```

output
```
Observation: [111. 188.]
Codebook:
 [[102. 203.]
 [132. 193.]
 [ 45. 155.]
 [ 57. 173.]]
Distances squared: [ 306.  466. 5445. 3141.]
Closest code index: 0
Closest code: [102. 203.]
```
