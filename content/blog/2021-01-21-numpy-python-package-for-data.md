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

### Creation of NumPy Arrays

#### Numpy Array creation

- N-dimensional arrays or ndarray can be created in multiple ways in numpy.
- Now let us focus on creating ndarray,
  - From Python built-in datatypes : ```lists``` or ```tuples```
  - Using Numpy array creation methods like ```ones```, ```ones_like```, ```zeros```, ```zeros_like```
  - Using Numpy numeric sequence generators.
  - Using Numpy ```random``` module.
  - By reading data from a file.

#### ndarrays from Lists

- Data available in lists, or tuples can be converted into numpy arrays using ```array``` method
- Creating a 3-Dimensional array from a list of list of lists is shown in Example 1.

```Python
import numpy as np
a = [[[4.1, 2.5], [1.1, 2.3], [9.1, 2.5]], 
     [[8.6, 9.9],[3.6, 4.3], [6.6, 0.3]]]

x = np.array(a, dtype='float64')

type(x), x.ndim, x.shape
```

Output:

```Output
(numpy.ndarray, 3, (2, 3, 2))
```

#### Array Creation Methods

Numpy allows creation of arrays with default values like ```0```, ```1```, or another value.

```Python
# Example 1: Using zeros method
x = np.zeros(shape=(2,4))
print(x)
```

Output

```Console
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]]
```

```Python
# Example 2 : Using full method
y = np.full(shape=(2,3), fill_value=10.5)
print(y)
```

Output

```Console
[[10.5 10.5 10.5]
 [10.5 10.5 10.5]]
```

#### Numeric Sequence Generators

Two major methods used in numpy for generating number sequences are,

- ```arange``` : Numbers created based on step value.
  - Syntax - numpy.arange([start, ]stop, [step, ]dtype=None)

- ```linspace``` : Numbers created based on size value.
  - Syntax - numpy.linspace(start, stop, #num inbetween, endpoint=True, retstep=False, dtype=None)

```Python
# Example 1
x = np.arange(3, 15, 2.5) # 2.5 is step
print(x)
```

Output

```Console
[ 3.   5.5  8.  10.5 13. ]
```

```Python
# Example 2
y = np.linspace(3, 15, 5) # 5 is size of array 'y'
print(y)
```

Output

```Console
[ 3.  6.  9. 12. 15.]
```

#### Random Numbers Generator

- ```random``` module of numpy is used to generate various random sequences.

```Python
# Example 1
np.random.seed(100) # setting seed
x = np.random.rand(2) # 2 random numbers between 0 and 1

print(x)
```

Output

```Console
[0.54340494 0.27836939]
```

```Python
# Example 2
np.random.seed(100) # setting seed
y = np.random.randint(10, 50, 3) # 3 random integers between 10 and 50

print(y)
```

Output

```Console
[18 34 13]
```

#### Simulating Normal Distribution

- ```randn``` is used to simulate standard normal distribution.

```Python
# Example 1
np.random.seed(100)
x = np.random.randn(3) # Standard normal distribution

print(x)
```

Output

```Console
[-1.74976547  0.3426804   1.1530358 ]
```

```Python
# Example 2
np.random.seed(100)
x = 10 + 2*np.random.randn(3) # normal distribution with mean 10 and sd 2

print(x)
```

Output

```Console
[ 6.50046905 10.68536081 12.30607161]
```

#### Reading Data from a file

- ```loadtxt``` is used to read data from a text file or any input data stream.

```Python
from io import StringIO
import numpy as np

x = StringIO('''88.25 93.45 72.60 90.90
72.3 78.85 92.15 65.75
90.5 92.45 89.25 94.50
''')

d = np.loadtxt(x,delimiter=' ')

print(d)

print(d.ndim, d.shape)
```

Output

```Console
[[88.25 93.45 72.6  90.9 ]
 [72.3  78.85 92.15 65.75]
 [90.5  92.45 89.25 94.5 ]]
2 (3, 4)
```

### Array Shape Manipulation

#### Reshaping ndarrays

Shape of an array can be changed using ```reshape```.

```Python
import numpy as np
np.random.seed(100)

x = np.random.randint(10, 100, 8)
print(x, end='\n\n')

y = x.reshape(2,4)
print(y, end='\n\n')

z = x.reshape(2,2,2)
print(z, '\n\n')
```

Output

```Console
[18 34 77 97 89 58 20 62]

[[18 34 77 97]
 [89 58 20 62]]

[[[18 34]
  [77 97]]

 [[89 58]
  [20 62]]] 
```

#### Stacking arrays vertically

- Two or more arrays can be joined vertically using the generic ```vstack``` method.

```Python
import numpy as np
x = np.array([[-1, 1], [-3, 3]])
y = np.array([[-2, 2], [-4, 4]])
np.vstack((x,y))
```

Output

```Console
array([[-1,  1],
       [-3,  3],
       [-2,  2],
       [-4,  4]])
```

#### Stacking arrays horizontally

- Two or more arrays can be joined horizontally using the generic ```hstack``` method.

```Python
import numpy as np
x = np.array([[-1, 1], [-3, 3]])
y = np.array([[-2, 2], [-4, 4]])
z = np.array([[-5, 5], [-6, 6]])
np.hstack((x,y,z))
```

Output

```Console
array([[-1,  1, -2,  2, -5,  5],
       [-3,  3, -4,  4, -6,  6]])
```

#### Splitting arrays vertically

- Arrays can be split vertically using the generic ```vsplit``` method.
- It is also possible to split at specific row numbers using ```vsplit```.

```Python
import numpy as np
x = np.arange(30).reshape(6, 5)

res = np.vsplit(x, 2)

print(res[0], end='\n\n')

print(res[1])
```

Output

```Console
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]]

[[15 16 17 18 19]
 [20 21 22 23 24]
 [25 26 27 28 29]]
```

```Python
import numpy as np
x = np.arange(30).reshape(6, 5)
res = np.vsplit(x, (2, 5))

print(res[0], end='\n\n')
print(res[1], end='\n\n')
print(res[2])
```

Output

```Console
[[0 1 2 3 4]
 [5 6 7 8 9]]

[[10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]

[[25 26 27 28 29]]
```

#### Splitting arrays Horizontally

- Arrays can be split horizontally using the generic ```hsplit``` method.

```Python
import numpy as np
x = np.arange(10).reshape(2, 5)
res = np.hsplit(x, (2,4))

print(res[0], end='\n\n')
print(res[1], end='\n\n')
print(res[2])
```

Output

```Console
[[0 1]
 [5 6]]

[[2 3]
 [7 8]]

[[4]
 [9]]
```





