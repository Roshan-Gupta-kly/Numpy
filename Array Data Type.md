# Checking Array's Data Type
when you create a NumPy array, NumPy automatically infers the most suitable data type for its elements. It can be checked using `dtype` attribute. It tells what type of data the array consist(like int, float,etc). and how much memory each element uses.

```python
# Create a NumPy array from a list of integers
# np.array() converts a Python list into a NumPy array
arr_int = np.array([1, 2, 3, 4, 5])

# Print the data type of the array
# .dtype shows the data type of array elements
print("Data type of arr_int:", arr_int.dtype)
```
output
```
Data type of arr_int: int64
```
You will see the data type of array is `int64` which specifies integer values. It gives the type based on your system architecture.

## Specifying a Data Type On Creation
Since `NumPy` automatically infers the data type which is useful. But sometime we need to explicitly define an array's data type for memory efficiency or to meet specific computation.

### Different data types use different amounts of memory:
- `int32` uses 4 bytes per element
- `int64` uses 8 bytes per element
- `float32` uses 4 bytes per element
- `float64` uses 8 bytes per element
For large arrays, choosing the right data type can save significant memory and potentially improve performance.

```python
# Create an array and specify the data type as float32
# The dtype parameter tells NumPy to store each number as a 32-bit float
arr_float = np.array([1.0, 2.5, 3.8], dtype=np.float32)

# Print the data type and the array
print("Data type of arr_float:", arr_float.dtype)
print("Array arr_float:", arr_float)
```
output
```
Data type of arr_float: float32
Array arr_float: [1.  2.5 3.8]
```
The output will show that the array has been created with the `float32` data type you specified.

You can use various data type strings or NumPy objects, such as `'f4'` for `float32`, `'i8'` for `int64`, or `np.bool_` for `boolean`.

## Converting an Array's Data Type
to convert the data type of exsiting array the `.astype()` method is used. This method doesnot change the original array instead it returns a new array with the specified data type.

Type conversion is useful when you need to:
- Perform operations that require a specific data type
- Reduce memory usage by converting to smaller types
- Prepare data for functions that except certain types

```python
# Create an integer array
# np.arange(5) creates an array with numbers from 0 to 4 (5 elements total)
original_arr = np.arange(5)
print("Original array:", original_arr)
print("Original dtype:", original_arr.dtype)

# Convert the array to float64
# .astype() creates a new array with the specified data type
converted_arr = original_arr.astype(np.float64)
print("Converted array:", converted_arr)
print("Converted dtype:", converted_arr.dtype)
```

output
```
Original array: [0 1 2 3 4]
Original dtype: int64
Converted array: [0. 1. 2. 3. 4.]
Converted dtype: float64
```
The output demonstrates that `original_arr` remains an integer array, while `converted_arr` is a new array with a `float64` data type.
This is a safe way to perform type conversions without losing your original data.

### Working With Other Data Types
NumPy supports a wide range of data types beyond just integers and floats, including booleans and complex numbers. Understanding how NumPy handles these can be very useful.

Boolean arrays are particularly useful for:

- Filtering data (selecting elements that meet certain conditions)
- Logical operations
- Masking arrays
For example, you can create an array of boolean values that represent True/False conditions.

```python
# Create a boolean array
# np.bool_ is NumPy's boolean data type (stores True/False values)
arr_bool = np.array([True, False, True], dtype=np.bool_)

print("Boolean array:", arr_bool)
print("Boolean array dtype:", arr_bool.dtype)
```

output
```
Boolean array: [ True False  True]
Boolean array dtype: bool
```
You can also check if a data type belongs to a general category (like integer or floating-point) using the np.issubdtype() function. This is helpful for writing functions that can handle multiple numeric types.
