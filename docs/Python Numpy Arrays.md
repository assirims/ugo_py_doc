<!--
---

[TOC]
-->
---

**Foreword**

Code snippets and excerpts from the tutorial. Python 3. From DataCamp.
With Jupyter Notebook and the `In [ ]` `Out [ ]` format.

---

# Invoke Numpy

- Code `import numpy as np` alone.
- Code `%pylab` to invoke Numpy and matplotlib or `%pylab inline` for plotting inside the notebook.
- Following `%pylab`, `import numpy as np` forces to use the prefix `np.` before any Numpy function.


```python
%pylab inline
```

    Populating the interactive namespace from numpy and matplotlib

```python
import numpy as np
```

```python
np.__version__
```

    '1.12.1'


- [Reference](https://docs.scipy.org/doc/numpy/reference/).

# Make Numpy Arrays

If `%pylab` was invoked.


```python
array([1,2,3,4])
```

    array([1, 2, 3, 4])


If `import numpy as np` was invoked alone.


```python
np.array([1,2,3,4])
```

    array([1, 2, 3, 4])


Let's begin.


```python
my_array = np.array([[1, 2, 3, 4], [5, 6, 7, 8]], dtype = np.int64)
my_2d_array = np.array([[1, 2, 3, 4], [5, 6, 7, 8]], dtype = np.int32)
my_3d_array = np.array([[[1, 2, 3, 4], [5, 6, 7, 8]], [[1, 2, 3, 4], [9, 10, 11, 12]]])
```


```python
# Print the array
print(my_array)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Print the 2d array
print(my_2d_array)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Print the 3d array
print(my_3d_array)
```

    [[[ 1  2  3  4]
      [ 5  6  7  8]]
    
     [[ 1  2  3  4]
      [ 9 10 11 12]]]


# A Python Numpy Array


```python
# Print out memory address
print(my_array.data)
print(my_2d_array.data)
```

    <memory at 0x7f85dcedd8b8>
    <memory at 0x7f85dcedd8b8>



```python
# Print out the shape of `my_array`
print(my_array.shape)
print(my_2d_array.shape)
```

    (2, 4)
    (2, 4)



```python
# Print out the data type of `my_array`
# kind of elements that are contained within the array
print(my_array.dtype)
print(my_2d_array.dtype)
```

    int64
    int32



```python
# Print out the stride of `my_array`
# the number of bytes that should be skipped in memory to go to the next element.
print(my_array.strides)
print(my_2d_array.strides)
```

    (32, 8)
    (16, 4)


# Make an "Empty" Numpy Array

Make use of initial placeholders, which can be filled up afterwards.


```python
# Create an array of ones
np.ones((3,4))
```




    array([[ 1.,  1.,  1.,  1.],
           [ 1.,  1.,  1.,  1.],
           [ 1.,  1.,  1.,  1.]])




```python
np.ones(4)
```




    array([ 1.,  1.,  1.,  1.])




```python
np.ones((1,4))
```




    array([[ 1.,  1.,  1.,  1.]])




```python
# Create an array of zeros
np.zeros((2,3,4), dtype=np.int16)
```




    array([[[0, 0, 0, 0],
            [0, 0, 0, 0],
            [0, 0, 0, 0]],
    
           [[0, 0, 0, 0],
            [0, 0, 0, 0],
            [0, 0, 0, 0]]], dtype=int16)




```python
np.zeros(4)
```




    array([ 0.,  0.,  0.,  0.])




```python
np.zeros((1,4))
```




    array([[ 0.,  0.,  0.,  0.]])




```python
# Create an array with random values
np.random.random((2,2))
```




    array([[ 0.28103745,  0.58180454],
           [ 0.31233242,  0.28414052]])




```python
# Create an empty array
np.empty((3,2))
```




    array([[ 0.,  0.],
           [ 0.,  0.],
           [ 0.,  0.]])




```python
# Create a full array
np.full((2,2), 7)
```




    array([[7, 7],
           [7, 7]])




```python
# Create an array of evenly-spaced values
# from 10 to 25 (excluded) by 5
np.arange(10, 25, 5)
```




    array([10, 15, 20])




```python
# Create an array of evenly-spaced values
# from 0 to 2 in 9 intervals
np.linspace(0, 2, 9)
```




    array([ 0.  ,  0.25,  0.5 ,  0.75,  1.  ,  1.25,  1.5 ,  1.75,  2.  ])




```python
# Create an identity array or matrix
np.eye(2,2)
```




    array([[ 1.,  0.],
           [ 0.,  1.]])




```python
np.eye(3,3)
```




    array([[ 1.,  0.,  0.],
           [ 0.,  1.,  0.],
           [ 0.,  0.,  1.]])




```python
np.eye(3)
```




    array([[ 1.,  0.,  0.],
           [ 0.,  1.,  0.],
           [ 0.,  0.,  1.]])




```python
# Idem
np.identity(3)
```




    array([[ 1.,  0.,  0.],
           [ 0.,  1.,  0.],
           [ 0.,  0.,  1.]])



# Load Numpy Arrays from Text


```python
# Data in the text file

# Value1  Value2  Value3
# 0.2536  0.1008  0.3857
# 0.4839  0.4536  0.3561
# 0.1292  0.6875  0.5929
# 0.1781  0.3049  0.8928
# 0.6253  0.3486  0.8791
```


```python
# Set the current directory
import os

os.chdir('/home/ugo/Documents/Notebooks/DataCamp, Numpy tutorial')
print(os.getcwd())
```

    /home/ugo/Documents/Notebooks/DataCamp, Numpy tutorial



```python
# Import data
x, y, z = np.loadtxt('textfile.txt',
                    skiprows = 1,
                    unpack = True)
# unpack=True
# the values in column Value1 will be put in x, and so on
# delimiter
# comma-delimited data 
# specify the data type
# dtype

print(x)
```

    [ 0.2536  0.4839  0.1292  0.1781  0.6253]



```python
print(y)
```

    [ 0.1008  0.4536  0.6875  0.3049  0.3486]



```python
print(z)
```

    [ 0.3857  0.3561  0.5929  0.8928  0.8791]



```python
print(x)
print(y)
print(z)
```

    [ 0.2536  0.4839  0.1292  0.1781  0.6253]
    [ 0.1008  0.4536  0.6875  0.3049  0.3486]
    [ 0.3857  0.3561  0.5929  0.8928  0.8791]



```python
# Data in the text file

# Value1  Value2  Value3
# 0.4839  0.4536  0.3561
# 0.1292  0.6875  MISSING
# 0.1781  0.3049  0.8928
# MISSING 0.5801  0.2038
# 0.5993  0.4357  0.7410
```


```python
# Import data
my_array2 = np.genfromtxt('textfile2.txt',
                      skip_header = 1,
                      filling_values = -999)
# filling_values
# converts character strings in numeric columns to nan, 
# convert these values to other ones
# missing_values
# argument that allows to specify what the missing values

print(my_array2)
```

    [[  4.83900000e-01   4.53600000e-01   3.56100000e-01]
     [  1.29200000e-01   6.87500000e-01  -9.99000000e+02]
     [  1.78100000e-01   3.04900000e-01   8.92800000e-01]
     [ -9.99000000e+02   5.80100000e-01   2.03800000e-01]
     [  5.99300000e-01   4.35700000e-01   7.41000000e-01]]


# Save Numpy Arrays


```python
x = np.arange(0.0,5.0,1.0) # array of evenly-spaced values from 0 to 5 by 1

np.savetxt('test1.txt', x, delimiter=',') # to a text file
np.save('test2.npy', x) # to a binary file
np.savez('test3.npz', x) # to a uncompressed archive
np.savez_compressed('test4.npz', x) # compressed archive
```

# Inspect Numpy Arrays

Almost all the attributes that an array can have.


```python
# Print the number of `my_array`'s dimensions
print(my_array.ndim)
```

    2



```python
# Print the number of `my_array`'s elements
print(my_array.size)
```

    8



```python
# Print information about `my_array`'s memory layout
print(my_array.flags)
```

      C_CONTIGUOUS : True
      F_CONTIGUOUS : False
      OWNDATA : True
      WRITEABLE : True
      ALIGNED : True
      UPDATEIFCOPY : False



```python
# Print the length of one array element in bytes
print(my_array.itemsize)
```

    8



```python
# Print the total consumed bytes by `my_array`'s elements
print(my_array.nbytes)
```

    64



```python
# Print the length of `my_array`
print(len(my_array))
```

    2



```python
# Change the data type of `my_array`
my_array.astype(float)
```




    array([[ 1.,  2.,  3.,  4.],
           [ 5.,  6.,  7.,  8.]])



# Numpy Broadcasting Works

Work with arrays of different shapes when performing arithmetic operations.


```python
# Initialize `x`
x = np.ones((3,4))

# Check shape of `x`
print(x.shape)
```

    (3, 4)



```python
# Initialize `y`
y = np.random.random((3,4))

# Check shape of `y`
print(y.shape)
```

    (3, 4)



```python
print(x)
print(y)
```

    [[ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]]
    [[ 0.44011854  0.55827517  0.8107237   0.96725064]
     [ 0.55923674  0.7754099   0.69282818  0.27928312]
     [ 0.03662555  0.70499711  0.59944023  0.67982408]]



```python
# Add `x` and `y`
x + y
```




    array([[ 1.44011854,  1.55827517,  1.8107237 ,  1.96725064],
           [ 1.55923674,  1.7754099 ,  1.69282818,  1.27928312],
           [ 1.03662555,  1.70499711,  1.59944023,  1.67982408]])




```python
# Initialize `y`
y2 = np.arange(4)

# Check shape of `y`
print(y2.shape)
```

    (4,)



```python
print(x)
print(y2)
```

    [[ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]]
    [0 1 2 3]



```python
# Subtract `x` and `y`
x - y2
```




    array([[ 1.,  0., -1., -2.],
           [ 1.,  0., -1., -2.],
           [ 1.,  0., -1., -2.]])




```python
# Initialize `x` and `y`
x2 = np.ones((3,4))
y3 = np.random.random((5,1,4))
```


```python
print(x2.shape)
print(y3.shape)
```

    (3, 4)
    (5, 1, 4)



```python
print(x2)
print(y3)
```

    [[ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]]
    [[[ 0.51096464  0.17753054  0.64596468  0.77465719]]
    
     [[ 0.51629966  0.52917705  0.76817841  0.20105093]]
    
     [[ 0.04512461  0.64426203  0.3210533   0.88679126]]
    
     [[ 0.93015065  0.34094049  0.01714773  0.37384124]]
    
     [[ 0.02498021  0.73107663  0.10914001  0.89487447]]]



```python
# Add `x` and `y`
x2 + y3
```




    array([[[ 1.51096464,  1.17753054,  1.64596468,  1.77465719],
            [ 1.51096464,  1.17753054,  1.64596468,  1.77465719],
            [ 1.51096464,  1.17753054,  1.64596468,  1.77465719]],
    
           [[ 1.51629966,  1.52917705,  1.76817841,  1.20105093],
            [ 1.51629966,  1.52917705,  1.76817841,  1.20105093],
            [ 1.51629966,  1.52917705,  1.76817841,  1.20105093]],
    
           [[ 1.04512461,  1.64426203,  1.3210533 ,  1.88679126],
            [ 1.04512461,  1.64426203,  1.3210533 ,  1.88679126],
            [ 1.04512461,  1.64426203,  1.3210533 ,  1.88679126]],
    
           [[ 1.93015065,  1.34094049,  1.01714773,  1.37384124],
            [ 1.93015065,  1.34094049,  1.01714773,  1.37384124],
            [ 1.93015065,  1.34094049,  1.01714773,  1.37384124]],
    
           [[ 1.02498021,  1.73107663,  1.10914001,  1.89487447],
            [ 1.02498021,  1.73107663,  1.10914001,  1.89487447],
            [ 1.02498021,  1.73107663,  1.10914001,  1.89487447]]])



But what if the dimensions are not compatible? What if they are not equal or if one of them is not equal to 1? Fix this by manipulating the array.

# Array Mathematics

- `np.add(), np.subtract(), np.multiply(), np.divide() and np.remainder()`.


```python
x = np.array([[1, 2, 3], [3, 4, 5]])
y = np.array([6, 7, 8])

print(x)
print(y)
```

    [[1 2 3]
     [3 4 5]]
    [6 7 8]



```python
# Add `x` and `y`
np.add(x,y)
```




    array([[ 7,  9, 11],
           [ 9, 11, 13]])




```python
# Subtract `x` and `y`
np.subtract(x,y)
```




    array([[-5, -5, -5],
           [-3, -3, -3]])




```python
# Multiply `x` and `y`
np.multiply(x,y)
```




    array([[ 6, 14, 24],
           [18, 28, 40]])




```python
# Divide `x` and `y`; x/y
np.divide(x,y)
```




    array([[ 0.16666667,  0.28571429,  0.375     ],
           [ 0.5       ,  0.57142857,  0.625     ]])




```python
# Calculate the remainder of `x` and `y`
np.remainder(x,y)
```




    array([[1, 2, 3],
           [3, 4, 5]])



- `np.exp(), np.sqrt(), np.log()`.
- `np.dot()`.
- `a.sum(), a.min(), a.max(axis=0), a.cumsum(axis=1), a.mean(), a.median(), a.corrcoef(), a.std(b)`.


```python
x = np.array([[1, 2, 3], [3, 4, 5]])
print(x)
```

    [[1 2 3]
     [3 4 5]]



```python
x.sum()
```




    18




```python
x.min()
```




    1




```python
y = np.array([6, 7, 8])
print(y)
```

    [6 7 8]



```python
y.max(axis=0)
```




    8




```python
x.max(axis=1)
```




    array([3, 5])




```python
y.cumsum(axis=0)
```




    array([ 6, 13, 21])




```python
x.mean()
```




    3.0




```python
np.std(x)
```




    1.2909944487358056



- `==, <, >`.
- `np.array_equal()`
- `np.logical_or(), np.logical_not(), np.logical_and()`.


```python
a = np.array([True, True, False, False])
b = np.array([False, False, True, True])
```


```python
# `a` AND `b` 
np.logical_and(a, b)
```




    array([False, False, False, False], dtype=bool)




```python
# `a` OR `b` 
np.logical_or(a, b)
```




    array([ True,  True,  True,  True], dtype=bool)




```python
# `a` NOT `b` 
np.logical_not(a,b)
```




    array([False, False,  True,  True], dtype=bool)



# Subset, Slice, and Index Arrays

- `a[start:end]`, items start through the end (but the end is not included!).
- `a[start:]`, items start through the rest of the array.
- `a[:end]`, items from the beginning through the end (but the end is not included!).


```python
my_array = np.array([1,2,3,4])
print(my_array)
```

    [1 2 3 4]



```python
# Select the element at the 1st index
print(my_array[1])
```

    2



```python
print(my_2d_array)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Select the element at row 1 column 2
print(my_2d_array[1][2])
```

    7



```python
# Select the element at row 1 column 2
print(my_2d_array[1,2])
```

    7



```python
print(my_3d_array)
```

    [[[ 1  2  3  4]
      [ 5  6  7  8]]
    
     [[ 1  2  3  4]
      [ 9 10 11 12]]]



```python
# Select the element at row 1, column 2 and 
print(my_3d_array[1,1,2])
```

    11



```python
# Select items at index 0 and 1
print(my_array[0:2])
```

    [1 2]



```python
# Select items at row 0 and 1, column 1
print(my_2d_array[0:2,1])
```

    [2 6]



```python
# Select items at row 1
# This is the same as saying `my_3d_array[1,:,:]
print(my_3d_array[1,...])
```

    [[ 1  2  3  4]
     [ 9 10 11 12]]



```python
# Try out a simple example
print(my_array[my_array < 3])
```

    [1 2]



```python
# Specify a condition
bigger_than_3 = (my_3d_array >= 3)
```


```python
# Use the condition to index our 3d array
print(my_3d_array[bigger_than_3])
```

    [ 3  4  5  6  7  8  3  4  9 10 11 12]



```python
bigger_than_3 = (my_3d_array > 3) | (my_3d_array == 3)
```


```python
bigger_than_3
print(bigger_than_3)
```

    [[[False False  True  True]
      [ True  True  True  True]]
    
     [[False False  True  True]
      [ True  True  True  True]]]



```python
# Select elements at (1,0), (0,1), (1,2) and (0,0)
# [[r], [c]]
print(my_2d_array[[1, 0, 1, 0],[0, 1, 2, 0]])
```

    [5 2 7 1]



```python
# Select a subset of the rows and columns
# [[r], [c]]
print(my_2d_array[[1, 0, 1, 0]][:,[0,1,2,0]])
```

    [[5 6 7 5]
     [1 2 3 1]
     [5 6 7 5]
     [1 2 3 1]]


# Ask for Help


```python
# Look up info on `mean` with `np.lookfor()` 
print(np.lookfor("median"))
```

    Search results for 'median'
    ---------------------------
    numpy.median
        Compute the median along the specified axis.
    numpy.nanmedian
        Compute the median along the specified axis, while ignoring NaNs.
    numpy.ma.median
        Compute the median along the specified axis.
    numpy.pad
        Pads an array.
    numpy.percentile
        Compute the qth percentile of the data along the specified axis.
    numpy.nanpercentile
        Compute the qth percentile of the data along the specified axis,
    None



```python
# Get info on data types with `np.info()`
np.info(np.ndarray.dtype)
```

    Data-type of the array's elements.
    
    Parameters
    ----------
    None
    
    Returns
    -------
    d : numpy dtype object
    
    See Also
    --------
    numpy.dtype
    
    Examples
    --------
    >>> x
    array([[0, 1],
           [2, 3]])
    >>> x.dtype
    dtype('int32')
    >>> type(x.dtype)
    <type 'numpy.dtype'>


# Manipulate Arrays

## Transpose Arrays

There is no effect when transposing a 1-D array!


```python
# Print `my_2d_array`
print(my_2d_array)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Transpose `my_2d_array`
print(np.transpose(my_2d_array))
```

    [[1 5]
     [2 6]
     [3 7]
     [4 8]]



```python
# Or use `T` to transpose `my_2d_array` (more flexible, more arguments)
print(my_2d_array.T)
```

    [[1 5]
     [2 6]
     [3 7]
     [4 8]]


## Reshaping versus Resizing Arrays


```python
x = np.ones((3,4))
print(x)
```

    [[ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]]



```python
# Print the shape of `x`
print(x.shape)
```

    (3, 4)



```python
# Resize `x` to ((6,4))
np.resize(x, (6,4))
```




    array([[ 1.,  1.,  1.,  1.],
           [ 1.,  1.,  1.,  1.],
           [ 1.,  1.,  1.,  1.],
           [ 1.,  1.,  1.,  1.],
           [ 1.,  1.,  1.,  1.],
           [ 1.,  1.,  1.,  1.]])




```python
# Try out this as well
x.resize((6,4))

# Print out `x`
print(x)
```

    [[ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]
     [ 1.  1.  1.  1.]
     [ 0.  0.  0.  0.]
     [ 0.  0.  0.  0.]
     [ 0.  0.  0.  0.]]



```python
x = np.ones((1,12))
print(x)
```

    [[ 1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.]]



```python
# Print the size of `x` to see what's possible
print(x.size)
```

    12



```python
# Reshape `x` to (2,6)
print(x.reshape((2,6)))
```

    [[ 1.  1.  1.  1.  1.  1.]
     [ 1.  1.  1.  1.  1.  1.]]



```python
# Flatten `x`
# n-D arrays to a 1-D array
z = x.ravel()

# Print `z`
print(z)
```

    [ 1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.]


## How to Append Arrays


```python
my_array = np.array([1, 2, 3, 4])
print(my_array)
```

    [1 2 3 4]



```python
# Append a 1D array to `my_array`
new_array = np.append(my_array, [7, 8, 9, 10])

# Print `new_array`
print(new_array)
```

    [ 1  2  3  4  7  8  9 10]



```python
print(my_2d_array)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Append an extra column to `my_2d_array`
# axis 1 indicates the columns, 
# while axis 0 indicates the rows in 2-D arrays
new_2d_array = np.append(my_2d_array, [[7], [8]], axis=1)

# Print `new_2d_array`
print(new_2d_array)
```

    [[1 2 3 4 7]
     [5 6 7 8 8]]


## How to Insert and Delete Array Elements


```python
print(my_array)
```

    [1 2 3 4]



```python
# Insert `5` at index 1
np.insert(my_array, 1, 5)
```




    array([1, 5, 2, 3, 4])




```python
print(my_array)
```

    [1 2 3 4]



```python
# Delete the value at index 1
np.delete(my_array,[1])
```




    array([1, 3, 4])



## How to Join and Split Arrays

- The number of dimensions needs to be the same if want to concatenate two arrays with `np.concatenate()`.
- With `np.vstack()`, make sure that the number of columns in both arrays is the same.
- The same holds also for when using `np.r[]`.
- For `np.hstack()`, make sure that the number of dimensions is the same and that the number of rows in both arrays is the same.
- Prefer `np.concatenate()` or `np.stack()`.
- With `np.column_stack()`, make sure that the arrays have the same first dimension.
- `np.c_[]` is another way to concatenate. Here also, the first dimension of both arrays needs to match.


```python
x = np.array([1,1,1,1])
x = np.ones((4))
print(x)

print(my_array)
```

    [ 1.  1.  1.  1.]
    [1 2 3 4]



```python
# Concatentate `my_array` and `x`
print(np.concatenate((my_array,x)))
```

    [ 1.  2.  3.  4.  1.  1.  1.  1.]



```python
print(my_2d_array)
```

    [[1 2 3 4]
     [5 6 7 8]]



```python
# Stack arrays row-wise
print(np.vstack((my_array, my_2d_array)))
```

    [[1 2 3 4]
     [1 2 3 4]
     [5 6 7 8]]



```python
my_resized_array = np.vstack((my_array, my_array))
print(my_resized_array)
```

    [[1 2 3 4]
     [1 2 3 4]]



```python
# Stack arrays row-wise
print(np.r_[my_resized_array, my_2d_array])
```

    [[1 2 3 4]
     [1 2 3 4]
     [1 2 3 4]
     [5 6 7 8]]



```python
# Stack arrays horizontally
print(np.hstack((my_resized_array, my_2d_array)))
```

    [[1 2 3 4 1 2 3 4]
     [1 2 3 4 5 6 7 8]]



```python
# Stack arrays column-wise
print(np.column_stack((my_resized_array, my_2d_array)))
```

    [[1 2 3 4 1 2 3 4]
     [1 2 3 4 5 6 7 8]]



```python
# Stack arrays column-wise
print(np.c_[my_resized_array, my_2d_array])
```

    [[1 2 3 4 1 2 3 4]
     [1 2 3 4 5 6 7 8]]


## Split Arrays


```python
print(my_resized_array)
```

    [[1 2 3 4]
     [1 2 3 4]]



```python
# Split `my_stacked_array` horizontally at the 2nd index (left-right)
print(np.hsplit(my_resized_array, 2))
```

    [array([[1, 2],
           [1, 2]]), array([[3, 4],
           [3, 4]])]



```python
# Split `my_stacked_array` vertically at the 2nd index (top-bottom)
print(np.vsplit(my_resized_array, 2))
```

    [array([[1, 2, 3, 4]]), array([[1, 2, 3, 4]])]


# How to Visualize Numpy Arrays

- Following `%pylab`, `import matplotlib.pyplot as plt` forces to use the prefix `plt` before any `matplotlib` function.


```python
# Initialize an array
my_3d_array = np.array([[[1,2,3,4], [5,6,7,8]], [[1,2,3,4], [9,10,11,12]]], dtype = np.int64)

print(my_3d_array)
```

    [[[ 1  2  3  4]
      [ 5  6  7  8]]
    
     [[ 1  2  3  4]
      [ 9 10 11 12]]]



```python
# Pass the array to `np.histogram()`
# compute the occurrences of the array that fall within each bin
# the first array lists the frequencies for all the elements of the array,
# while the second array lists the bins that would be used without specifying any bins.
print(np.histogram(my_3d_array))
```

    (array([4, 2, 2, 1, 1, 1, 1, 1, 1, 2]), array([  1. ,   2.1,   3.2,   4.3,   5.4,   6.5,   7.6,   8.7,   9.8,
            10.9,  12. ]))



```python
# Specify the number of bins
print(np.histogram(my_3d_array, bins = range(0,13)))
```

    (array([0, 2, 2, 2, 2, 1, 1, 1, 1, 1, 1, 2]), array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12]))



```python
%matplotlib inline
import matplotlib.pyplot as plt
```


```python
# Construct the histogram with a flattened 3d array and a range of bins
# plt.hist() flattens data and the bins
plt.hist(my_3d_array.ravel(), bins = range(0,13))

# Add a title to the plot
plt.title('Frequency of My 3D Array Elements')
plt.grid(True)

# Show the plot
plt.show()
```


![png](img/python_numpy_arrays/output_152_0.png)


```python
# Create an array
points = np.arange(-5, 5, 0.01)

# Make a meshgrid
# need 2-D arrays of x and y coordinate values 
# create a rectangular grid out of an array of x values and an array of y values
xs, ys = np.meshgrid(points, points)
z = np.sqrt(xs ** 2 + ys ** 2)

# Display the image on the axes
plt.imshow(z, cmap=plt.cm.gray)
plt.grid(True)

# Draw a color bar
plt.colorbar()

# Show the plot
plt.show()
```


![png](img/python_numpy_arrays/output_153_0.png)

