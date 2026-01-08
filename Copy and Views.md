## The Difference Between a Copy and a View
In NumPy, a `copy` is an entirely new array with its own data, while a `view` is a new way of looking at the same data. Modifying a `view` will affect the original array, but modifying a `copy` will not.

Let's see this in practice. We will create an array, then make a view and a copy of it. We will then modify both and observe the effect on the original array.

```python
import numpy as np

# --- Part 1: Modifying a View ---
print("--- Modifying a View ---")
# Create an original array
original_array_view = np.array([1, 2, 3, 4, 5])
print(f"Original array: {original_array_view}")

# Create a view of the array
view_array = original_array_view.view()
# Modify the first element of the view
view_array[0] = 99
print(f"View after modification: {view_array}")
print(f"Original array after modifying the view: {original_array_view}\n")


# --- Part 2: Modifying a Copy ---
print("--- Modifying a Copy ---")
# Create another original array
original_array_copy = np.array([10, 20, 30, 40, 50])
print(f"Original array: {original_array_copy}")

# Create a copy of the array
copy_array = original_array_copy.copy()
# Modify the first element of the copy
```

output
```
--- Modifying a View ---
Original array: [1 2 3 4 5]
View after modification: [99  2  3  4  5]
Original array after modifying the view: [99  2  3  4  5]

--- Modifying a Copy ---
Original array: [10 20 30 40 50]
Copy after modification: [999  20  30  40  50]
Original array after modifying the copy: [10 20 30 40 50]
```

## Slicing an Array - Creating a View
A very common operation in NumPy is slicing, which is used to select a range of elements from an array. Basic slicing always creates a `view` of the original array. This is a key feature for memory efficiency, but you must be aware that modifying the slice will alter the original data.

```python
import numpy as np

# Create an array from 0 to 9
original_array = np.arange(10)
print(f"Original array: {original_array}")

# Create a slice of the array (elements from index 2 to 4)
array_slice = original_array[2:5]
print(f"Slice of the array: {array_slice}")

# Modify the first element of the slice
print("Modifying the first element of the slice to 100...")
array_slice[0] = 100

# Print the original array again to see the change
print(f"Original array after modification: {original_array}")
```

output
```
Original array: [0 1 2 3 4 5 6 7 8 9]
Slice of the array: [2 3 4]
Modifying the first element of the slice to 100...
Original array after modification: [  0   1 100   3   4   5   6   7   8   9]
```

## Advanced Indexing - Creating a Copy
While basic slicing creates views, `advanced indexing` always creates a `copy`. Advanced indexing involves passing a list, tuple, or another array of indices to select elements. Since the selected elements may not be in a contiguous block of memory, NumPy creates a new array (a copy) to hold them.

```python
import numpy as np

# Create an array from 0 to 9
original_array = np.arange(10)
print(f"Original array: {original_array}")

# Use advanced indexing to select elements at indices 1, 3, and 5
indexed_array = original_array[[1, 3, 5]]
print(f"Indexed array: {indexed_array}")

# Modify the first element of the new array
print("Modifying the first element of the indexed array to 100...")
indexed_array[0] = 100

# Print the original array again to see if it changed
print(f"Original array after modification: {original_array}")
```

output
```
Original array: [0 1 2 3 4 5 6 7 8 9]
Indexed array: [1 3 5]
Modifying the first element of the indexed array to 100...
Original array after modification: [0 1 2 3 4 5 6 7 8 9]
```
This time, the original array remains unchanged. The `indexed_array` was a copy, so modifications to it did not affect `original_array`.

## Identifying Copies and Views with .base
Sometimes it's not obvious whether an operation returned a `view` or a `copy`. NumPy provides a reliable way to check: the `.base` attribute of an array.

- If an array is a `view`, its .base attribute will point to the original array object it belongs to.
- If an array is a `copy`, its .base attribute will be None.

```python
import numpy as np

# Create an original array
original_array = np.arange(10)
print(f"Original array: {original_array}\n")

# Create a view using slicing
view_slice = original_array[2:5]
print(f"Slice (view): {view_slice}")
# Check if the slice is a view of the original array
print(f"Is the slice a view? {view_slice.base is original_array}\n")

# Create a copy using advanced indexing
copy_indexed = original_array[[1, 3, 5]]
print(f"Indexed (copy): {copy_indexed}")
# Check if the indexed array is a copy
print(f"Is the indexed array a copy? {copy_indexed.base is None}")
```

output
```
Original array: [0 1 2 3 4 5 6 7 8 9]

Slice (view): [2 3 4]
Is the slice a view? True

Indexed (copy): [1 3 5]
Is the indexed array a copy? True
```
