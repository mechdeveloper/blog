---
title: NumPy | Python Package for Data
date: 2021-01-21T19:33:04.989Z
description: "Code snippets for NumPy library in Python "
---
# NumPy

- An essential library used for __scientific computing__ in Python.
- Holds data in __N-dimensional array__ (`ndarray`) objects, which can store data in multiple dimensions.
- Supports performing __efficient array operations__ through Broadcasting feature

## Basic String Operations

### Defining the string 's'

```Python
s = 'Welcome to Jupyter Notebooks!!!'
```

### Displaying the string 's'

```Python
s
```

Output:

```Console
'Welcome to Jupyter Notebooks!!!'
```

### Length of 's'

```Python
len(s)
```

Output:

```Console
31
```

### Obtaining the slice = 'Jupyeter Notebooks'

```Python
s[11:28] # Returns substring ranging from 11th index to 27th index
```

Output:

```Console
'Jupyter Notebooks'
```

### Determining no. of vovels in 's'

```Python
vovels = ['a', 'e', 'i', 'o', 'u', #Press Enter to write in next line
          'A', 'E', 'I', 'O', 'U']
sum(1 for char in s if char in vovels)
```

Output:

```Console
10
```

### Filtering words starting with either 'J' or 'N'

```Python
char_set = ('J', 'N') # Press Enter to write code in next line
[word for word in s.split() if word.startswith(char_set)]
```

Output:

```Console
['Jupyter', 'Notebooks!!!']
```

## Introduction to Numpy

- NumPy is a Python library, which supports efficient handling of various numerical operations on arrays __holding numeric data__.
- These arrays are known as `N-dimensional arrays` or `ndarrays`.
- Ndarrays are capable of holding data elements in __multiple dimensions__.
- Each data element of a ndarray is of __fixed size__.
- All elements of a ndarray are of __same data type__.

### N-dimensional array

- N-dimensional array is an object, capable of holding data elements of same type and of a fixed size in multiple dimensions.
- Creation of a 1-D array of five elements, from a list is shown in Example 1.
- Creation of a 2-D array from a list of lists is shown in Example 2.

#### Creation of 1-D array of five elements, from a list

```Python
# Example 1 
import numpy as np
x = np.array([5, 8, 9, 10, 11]) # using 'array' method
print(x)
type(x)   # Displays type of array 'x'
```

Output:

```Console
[ 5  8  9 10 11]
numpy.ndarray
```

#### Creation of 2-D array from a list of lists

```Python
# Example 2
y = np.array([[6, 9, 5], 
              [10, 82, 34]])  
print(y)
```

Output:

```Console
[[ 6  9  5]
 [10 82 34]]
```

### ndarray Attributes

Some of the important attributes of a **ndarray** are

- ndim : Returns number of dimensions.
- shape: Returns Shape in tuple.
- size : Total number of elements.
- dtype : Type of each element.
- itemsize : Size of each element in Bytes.
- nbytes : Total bytes consumed by all elements.

```Python
print("ndarray ndim Returns number of dimensions:", y.ndim)
print("ndarray shape Returns Shape in tuple:", y.shape)
print("ndarray size Returns Total number of elements:", y.size)
print("ndarray dtype Returns Type of each element:", y.dtype)
print("ndarray itemsize Returns Size of each element in Bytes:", y.itemsize)
print("ndarray nbytes Returns Total bytes consumed by all elements:", y.nbytes)
```

Output:

```Console
ndarray ndim Returns number of dimensions: 2
ndarray shape Returns Shape in tuple: (2, 3)
ndarray size Returns Total number of elements: 6
ndarray dtype Returns Type of each element: int32
ndarray itemsize Returns Size of each element in Bytes: 4
ndarray nbytes Returns Total bytes consumed by all elements: 24
```

### Numpy dtypes

- ```Numpy``` supports various data types based on number of bytes required by the data elements.
- Data type can be explicitly specified with ```dtype``` argument.
- A ndarray, holding float values is defined in Example 4.

```Python
# Example 4
y = np.array([[6, 9, 5],
              [10, 82, 34]], 
             dtype='float64')  
print(y)
print(y.dtype)
```

Output:

```Console
[[ 6.  9.  5.]
 [10. 82. 34.]]
float64
```

