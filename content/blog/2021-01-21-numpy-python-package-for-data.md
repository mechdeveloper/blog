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

### Obtaining the slice = 'Jupyter Notebooks'

```Python
s[11:28] # Returns substring ranging from 11th index to 27th index
```

Output:

```Console
'Jupyter Notebooks'
```

### Determining no. of vovels in 's'

```Python
vowels = ['a', 'e', 'i', 'o', 'u', #Press Enter to write in next line
          'A', 'E', 'I', 'O', 'U']
sum(1 for char in s if char in vowels)
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

### Basic Operations on NumPy Arrays

#### Basic Operations with Scalars

- Operations in Numpy are carried out element wise.
- Hence the expression ```x + 10```, increases every element of array ```x``` by ```10```.

```Python
import numpy as np
x = np.arange(6).reshape(2,3)
print(x, end='\n\n')
print(x + 10, end='\n\n')
print(x * 3, end='\n\n')
print(x % 2)
```

Output

```Console
[[0 1 2]
 [3 4 5]]

[[10 11 12]
 [13 14 15]]

[[ 0  3  6]
 [ 9 12 15]]

[[0 1 0]
 [1 0 1]]
```

#### Basic Operations between Arrays

- Operations between arrays also happen element wise.

```Python
import numpy as np
x = np.array([[-1, 1], [-2, 2]])
y = np.array([[4, -4], [5, -5]])

print(x, end='\n\n')
print(y, end='\n\n')
print(x + y, end='\n\n')
print(x * y)
```

Output

```Console
[[-1  1]
 [-2  2]]

[[ 4 -4]
 [ 5 -5]]

[[ 3 -3]
 [ 3 -3]]

[[ -4  -4]
 [-10 -10]]
```

- It is also possible to perform operations on arrays with varying size and shape.
- This is due ```Broadcasting``` feature exhibited by numpy arrays.

```Python
import numpy as np
x = np.array([[-1, 1], [-2, 2]])
y = np.array([-10, 10])
print(x, end='\n\n')
print(y, end='\n\n')
print(x * y)
```

Output:

```Console
[[-1  1]
 [-2  2]]

[-10  10]

[[10 10]
 [20 20]]
```

#### Broadcasting in NumPy

- Element wise operations between arrays are possible only when they have the same shape or compatible for Broadcasting.
- Steps followed to verify the feasibility of Broadcasting between arrays are:
  1. Initially, compare the dimensions of all arrays.
  2. If dimensions do not match, prepend ```1's``` to shape of a smaller array so that it matches dimensions of a larger array.
  3. Start comparing array shapes from the last dimension and move backward.
  4. If the shape of both arrays are equal or either of it has a shape of ```1```, continue the comparison.
  5. Else at any dimension, if step 4 fails, broadcasting between arrays is not feasible.
- Finally, the resulted broadcasting array shape would be maximum of two compared shapes in each dimension.

#### Feasibility of Broadcasting

- Below examples show feasibility of broadcasting between two arrays, having shape s1 and s2 respectively.

```txt
Given: s1 = (4, 3); s2 = (3,)
Step 1 and 2: s1 = (4, 3); s2 = (1, 3)
Step 3 and 4: pass in 2 dimensions
Result : Broadcasting feasible;
         resulted array shape - (4,3) 
```

```txt
Given: s1 = (5,); s2 = (5,4,3)
Step 1 and 2: s1 = (1, 1, 5); s2 = (5, 4, 3)
Step 3 and 4: fail in last dimension. ( 5 != 3)
Result : Broadcasting not feasible. 
```

#### NumPy Universal Functions

- Numpy provides a lot of mathematical functions, in the form of ```Universal functions```.
- To know more on Universal functions, refer [this link](https://numpy.org/doc/stable/reference/ufuncs.html).

```Python
import numpy as np
x = np.array([[0,1], [2,3]])
print(x, end='\n\n')
print(np.square(x), end='\n\n')
print(np.sin(x))
```

Output

```Console
[[0 1]
 [2 3]]

[[0 1]
 [4 9]]

[[0.         0.84147098]
 [0.90929743 0.14112001]]
```

#### NumPy Array Methods

- Many of the universal functions are available as methods of ```ndarray``` class.
- By default ```sum``` method adds all array elements.
- It is also possible to apply ```sum``` method on elements of a specific dimension, using ```axis``` argument.

```Python
import numpy as np
x = np.array([[0,1], [2, 3]])
print(x, end='\n\n')
print(x.sum(), end='\n\n')
print(x.sum(axis=0), end='\n\n')
print(x.sum(axis=1))
```

Output

```Console
[[0 1]
 [2 3]]

6

[2 4]

[1 5]
```

### Indexing, Slicing, Iterating NumPy Arrays

#### Indexing, Slicing a 1-D ndarray

- Slicing refers to extracting a portion of existing array.
- This can be achieved with a slice object.
- A slice object is of the form ```start:end:step```. All three are optional.
- Having only a single number inside square brackets refer to start index.

Indexing

- In python Array Index starts at 0 (fist element will have index 0)

Slicing

- ```arr[a:b]``` will slice the value effectively from index ```a``` upto ```b-1```

Note: If we are making slice we are not making a copy from original we are working with actual array elements. To work with copy of an array use ```copy()``` method, For Eg: ```arr2= arr.copy()```

```Python
# Example: Slicing a 1-D array
x = np.array([5, 10, 15, 20, 25, 30, 35])

# 5  10  15  20  25  30  35  # Array Values
# 0   1   2   3   4   5   6  # Array Index

print('Array:', x)
print('Array Length:', len(x)) # Array Length 
print('Array Shape:', x.shape) # Array shape
print('\n')
print('Index 1:', x[1])  # Indexing 
print('Index 6:', x[6])  # Indexing 
print(x[1:6]) # Slicing 
# Note this will give us the value upto index (6-1 = 5)

print(x[1:6:2]) # Slicing Step 2
print(x[1:6:3]) # Slicing Step 3
```

Output

```Console
Array: [ 5 10 15 20 25 30 35]
Array Length: 7
Array Shape: (7,)


Index 1: 10
Index 6: 35
[10 15 20 25 30]
[10 20 30]
[10 25]
```

#### Indexing, Slicing a 2-D ndarray

- Two ```slice objects```, one for each dimension, are required to slice a 2-D array.
- They are separated by a ```comma (,)``` and having only a ```single slice``` object inside square brackets refers to first dimension.
- All elements of a single dimension can be referred with a ```colon (:)```.

```Python
import numpy as np
y = np.array([[0, 1, 2],
              [3, 4, 5]])

# Array Values
# [0,1,2]  - Index 0
# [3,4,5]  - Index 1

print('Array:')
print(y)
print('Array Length:', len(y)) # Array Length 
print('Array Shape:', y.shape) # Array shape
print('\n')

print('Index 0:', y[0]) 
print('Index 1:', y[1]) 

print('Index [0, 0]:', y[0,0]) # Index 0, Sub Index 0 
print('Index [1, 1]:', y[1,1]) # Index 1, Sub Index 1

print('\n')
# Slice 1:2 Row 1 Item 2 = 4, Slice 1:3 Row 1 Item 3 = 5

print('Array:')
print(y)
print('\n')

print('Slice start:end')
print('Slice: [:]')
print(y[:]) 
print('\n')

print('Slice: [0:0]')
print(y[0:0]) 
print('\n')

print('Slice: [0:1]')
print(y[0:1]) 
print('\n')

print('Slice: [0:2]')
print(y[0:2]) 
print('\n')

print('Slice: [0:3]')
print(y[0:3]) 
print('\n')


print('Slice: [1:0]')
print(y[1:0]) 
print('\n')

print('Slice: [1:1]')
print(y[1:1]) 
print('\n')

print('Slice: [1:2]')
print(y[1:2]) 
print('\n')



print('Array:')
print(y)
print('\n')

print('Slice 2-D in a 2-D array:')
print('Slice 2-D in a 2-D array: [start:end, start:end]')
print('Slice [0:1, 0:1]:')
print(y[0:1, 0:1]) 
print('\n')

print('Slice [0:1, 0:2]:')
print(y[0:1, 0:2]) 
print('\n')

print('Slice [0:1, 0:3]:')
print(y[0:1, 0:3]) 
print('\n')


print('Slice [1:2, 1:3]:')
print(y[1:2, 1:3]) 
print('\n')



print('Array:')
print(y)
print('\n')

print('All elements in single dimension are reffered with colon (:) ')
print('Slice [:,0]:') # Column 0
print(y[:, 0]) 
print('\n')

print('Slice [:,1]:') # Returns an array of Column 1 in 2D matrix
print(y[:, 1]) 
print('\n')


print('Slice [:,2]:') # Returns an array of Column 2 in 2D matrix
print(y[:, 2]) 
print('\n')


print('Slice [0,:]:') # Returns an array of Row 1 in 2D matrix
print(y[0, :]) 
print('\n')

print('Slice [1,:]:') # Returns an array of Row 2 in 2D matrix
print(y[1, :]) 
print('\n')
```

Output

```Console
Array:
[[0 1 2]
 [3 4 5]]
Array Length: 2
Array Shape: (2, 3)


Index 0: [0 1 2]
Index 1: [3 4 5]
Index [0, 0]: 0
Index [1, 1]: 4


Array:
[[0 1 2]
 [3 4 5]]


Slice start:end
Slice: [:]
[[0 1 2]
 [3 4 5]]


Slice: [0:0]
[]


Slice: [0:1]
[[0 1 2]]


Slice: [0:2]
[[0 1 2]
 [3 4 5]]


Slice: [0:3]
[[0 1 2]
 [3 4 5]]


Slice: [1:0]
[]


Slice: [1:1]
[]


Slice: [1:2]
[[3 4 5]]


Array:
[[0 1 2]
 [3 4 5]]


Slice 2-D in a 2-D array:
Slice 2-D in a 2-D array: [start:end, start:end]
Slice [0:1, 0:1]:
[[0]]


Slice [0:1, 0:2]:
[[0 1]]


Slice [0:1, 0:3]:
[[0 1 2]]


Slice [1:2, 1:3]:
[[4 5]]


Array:
[[0 1 2]
 [3 4 5]]


All elements in single dimension are reffered with colon (:) 
Slice [:,0]:
[0 3]


Slice [:,1]:
[1 4]


Slice [:,2]:
[2 5]


Slice [0,:]:
[0 1 2]


Slice [1,:]:
[3 4 5]

```

#### Slicing Higher Dimensions ndarrays

- For slicing an ```n``` dimensional ndarray, ```n``` slice objects are required.
- Slice objects are separated by ,
- Having only a single slice object refers to first dimension.

```Python
z = np.array([[[-1, 1], [-2, 2]],
              [[-4, 4], [-5, 5]],
              [[-7, 7], [-9, 9]]])


print('Array:')
print(z)
print('Array Length:', len(z)) # Array Length 
print('Array Shape:', z.shape) # Array shape
print('\n')



print('Indexing:  print elements at 0 1 2 index')
print(z[0]) # print o index element
print(z[1]) # print 1 index element
print(z[2]) # print 2 index element

print('Indexing:  print sub element 0 1 of element at 1 index')
print(z[1, 0]) # print o index element
print(z[1, 1]) # print 1 index element

print('Indexing:  print subelement 0 1 of sub element 1 of element at 1 index')
print(z[1, 1, 0]) # print o index element
print(z[1, 1, 1]) # print 1 index element

print('\n')
print('Slicing:')

print('Slicing: [:]')
print(z[:])
print('\n')

print('Slicing: [start:end]')
print('Slicing: [0:0]')
print(z[0:0])
print('\n')

print('Slicing: [start:end]: Start at index 0: ')
print('Slicing: [0:1]')
print(z[0:1])
print('\n')

print('Slicing: [0:2]')
print(z[0:2])
print('\n')

print('Slicing: [0:3]')
print(z[0:3])
print('\n')

print('Slicing: [start:end]: Start at index 1: ')
print('Slicing: [1:0]')
print(z[1:0])
print('\n')

print('Slicing: [1:1]')
print(z[1:1])
print('\n')

print('Slicing: [1:2]')
print(z[1:2])
print('\n')

print('Slicing: [1:3]')
print(z[1:3])
print('\n')

print('Slicing: [1:]')
print(z[1:])
print('\n')


print('Slicing: [start:end:step]')
print('Slicing: [0:3:2]')
print(z[0:3:2])
print('\n')



print('Array:')
print(z)
print('Array Length:', len(z)) # Array Length 
print('Array Shape:', z.shape) # Array shape
print('\n')



print('Slicing: 3-D')
print('Slicing: [start:end, start:end, start:end]')

print('Slicing: index 1 element in row of index 1: [1,:,1]')
print(z[1,:,1]) # index 1 element in row of index 1

print('Slicing: From all outer rows except the first, select 1st index element (which itself is an array) completely: [1:,1,:]')
print(z[1:,1,:]) # From all outer rows except the first, select 1st index element (which itself is an array) completely.
print('\n')

print('Step1')
print(z[1:])
print('\n')

print('Step2')
print(z[1:,1])
print('\n')

print('Step3')
print(z[1:,1,:])
```

Output

```Console
Array:
[[[-1  1]
  [-2  2]]

 [[-4  4]
  [-5  5]]

 [[-7  7]
  [-9  9]]]
Array Length: 3
Array Shape: (3, 2, 2)


Indexing:  print elements at 0 1 2 index
[[-1  1]
 [-2  2]]
[[-4  4]
 [-5  5]]
[[-7  7]
 [-9  9]]
Indexing:  print sub element 0 1 of element at 1 index
[-4  4]
[-5  5]
Indexing:  print subelement 0 1 of sub element 1 of element at 1 index
-5
5


Slicing:
Slicing: [:]
[[[-1  1]
  [-2  2]]

 [[-4  4]
  [-5  5]]

 [[-7  7]
  [-9  9]]]


Slicing: [start:end]
Slicing: [0:0]
[]


Slicing: [start:end]: Start at index 0: 
Slicing: [0:1]
[[[-1  1]
  [-2  2]]]


Slicing: [0:2]
[[[-1  1]
  [-2  2]]

 [[-4  4]
  [-5  5]]]


Slicing: [0:3]
[[[-1  1]
  [-2  2]]

 [[-4  4]
  [-5  5]]

 [[-7  7]
  [-9  9]]]


Slicing: [start:end]: Start at index 1: 
Slicing: [1:0]
[]


Slicing: [1:1]
[]


Slicing: [1:2]
[[[-4  4]
  [-5  5]]]


Slicing: [1:3]
[[[-4  4]
  [-5  5]]

 [[-7  7]
  [-9  9]]]


Slicing: [1:]
[[[-4  4]
  [-5  5]]

 [[-7  7]
  [-9  9]]]


Slicing: [start:end:step]
Slicing: [0:3:2]
[[[-1  1]
  [-2  2]]

 [[-7  7]
  [-9  9]]]


Array:
[[[-1  1]
  [-2  2]]

 [[-4  4]
  [-5  5]]

 [[-7  7]
  [-9  9]]]
Array Length: 3
Array Shape: (3, 2, 2)


Slicing: 3-D
Slicing: [start:end, start:end, start:end]
Slicing: index 1 element in row of index 1: [1,:,1]
[4 5]
Slicing: From all outer rows except the first, select 1st index element (which itself is an array) completely: [1:,1,:]
[[-5  5]
 [-9  9]]


Step1
[[[-4  4]
  [-5  5]]

 [[-7  7]
  [-9  9]]]


Step2
[[-5  5]
 [-9  9]]


Step3
[[-5  5]
 [-9  9]]
```

#### Iterating using 'for'

- ```for``` loop can be used to iterate over every dimensional element.

```Python
x = np.array([[-1, 1], [-2, 2]])
print('Array:\n', x, '\n')

for row in x:
    print('Row :',row)
```

Output

```Console
Array:
 [[-1  1]
 [-2  2]] 

Row : [-1  1]
Row : [-2  2]
```

#### Iterating using 'nditer'

- ```nditer``` method of numpy creates an iterator, which enable accessing each element one after the other.

```Python
import numpy as np
x = np.array([[0,1], [2, 3]])
print('Array:\n', x, '\n')

for a in np.nditer(x):
    print(a)
```

Output

```Console
Array:
 [[0 1]
 [2 3]] 

0
1
2
3
```

#### Boolean Indexing

- Checking if every element of an array satisfies a condition, results in a Boolean array.
- This Boolean array can be used as index to filter elements that satisfy the condition.

```Python
import numpy as np
x = np.arange(10).reshape(2,5)
print('Array:\n', x, '\n')

condition = x % 2 == 0
print(condition)
print('\n')
print(x[condition])
```

Output

```Console
Array:
 [[0 1 2 3 4]
 [5 6 7 8 9]] 

[[ True False  True False  True]
 [False  True False  True False]]


[0 2 4 6 8]
```




