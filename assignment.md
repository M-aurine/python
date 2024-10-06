# Python 101: Assignment

1. What is garbage collection in the context of Python, and why is it important? Can you explain how memory management is handled in Python?

In Python, **garbage collection** is the process of automatically deallocating memory by removing objects that are no longer in use. Python primarily uses **reference counting** and a **cyclic garbage collector** to manage memory.

- **Reference counting**: Every object in Python has a reference count. When the count drops to zero, Python knows that the object is no longer needed and can free the memory.
- **Cyclic garbage collector**: Handles objects that reference each other (circular references), which cannot be resolved by reference counting alone.

Garbage collection is important because it helps prevent memory leaks and ensures that memory is efficiently used.

import gc  # Python's garbage collection module

# Force garbage collection
gc.collect()


2. What are the key differences between NumPy arrays and Python lists, and can you explain the advantages of using NumPy arrays in numerical computations?  

The key differences between **NumPy arrays** and **Python lists** include:

- **Data Type**: NumPy arrays require all elements to be of the same data type, whereas Python lists can contain mixed data types.
- **Performance**: NumPy arrays are much faster than Python lists because they are implemented in C and use contiguous memory blocks, which optimize numerical computations.
- **Operations**: NumPy arrays support element-wise operations, broadcasting, and are highly efficient in vectorized operations, whereas Python lists require loops for such tasks.

### Advantages of NumPy Arrays:
- **Faster Computations**: NumPy performs operations faster due to its optimized C implementation.
- **Memory Efficiency**: NumPy uses less memory as all elements are of the same data type.

### Example:

import numpy as np

# Create a NumPy array
np_array = np.array([1, 2, 3, 4])

# Create a Python list
py_list = [1, 2, 3, 4]

# Element-wise multiplication with NumPy (faster)
np_array = np_array * 2

# List comprehension for element-wise multiplication with Python list (slower)
py_list = [x * 2 for x in py_list]

print(np_array)  # Output: [2, 4, 6, 8]
print(py_list)   # Output: [2, 4, 6, 8]


3. How does list comprehension work in Python, and can you provide an example of using it to generate a list of squared values or filter a list based on a condition?
List comprehension is a concise way to create lists by iterating over an iterable and optionally applying conditions.

**Example 1:** Generate a list of squared values

squares = [x**2 for x in range(1, 6)]
print(squares)  # Output: [1, 4, 9, 16, 25]

**Example 2:** Filter a list based on a condition  

# Filter to only include even numbers
even_numbers = [x for x in range(10) if x % 2 == 0]
print(even_numbers)  # Output: [0, 2, 4, 6, 8]

4. Can you explain the concepts of shallow and deep copying in Python, including when each is appropriate, and how deep copying is implemented?
In Python, copying refers to creating a new object that is identical to an existing one. There are two types of copying:  

**Shallow Copy:** Copies the object but not the elements within it. If the original object contains nested objects (like lists inside a list), shallow copy only copies references to those nested objects.  
**Appropriate:** When you don't need to modify the nested objects.  

**Deep Copy:** Recursively copies the object and all nested objects, creating independent copies of every element.  
**Appropriate:** When you need to modify nested objects without affecting the original object.  
Example:

import copy

# Original list with nested lists
list1 = [[1, 2], [3, 4]]

# Shallow copy
shallow_copy = copy.copy(list1)
shallow_copy[0][0] = 99
print(list1)  # Output: [[99, 2], [3, 4]]  (original list affected)

# Deep copy
deep_copy = copy.deepcopy(list1)
deep_copy[0][0] = 1
print(list1)  # Output: [[99, 2], [3, 4]]  (original list unaffected)

5. Explain with examples the difference between lists and tuples.
The main difference between lists and tuples in Python is that:

**Lists** are mutable, meaning their elements can be changed after creation.  
**Tuples** are immutable, meaning once a tuple is created, its elements cannot be modified.  

**Example of a List (Mutable):**  
my_list = [1, 2, 3]
my_list[0] = 4  # This is allowed
print(my_list)  # Output: [4, 2, 3]

**Example of a Tuple (Immutable):** 
my_tuple = (1, 2, 3)
# my_tuple[0] = 4  # This would raise an error
print(my_tuple)  # Output: (1, 2, 3)

**Use Cases:**
Lists: Used when you need a collection that can be modified (e.g., adding, removing, or changing elements).  
Tuples: Used when you need an immutable collection of items (e.g., fixed data like coordinates).

