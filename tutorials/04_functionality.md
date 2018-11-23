
SciPy - Basic Functionality



By default, all the NumPy functions have been available through the SciPy namespace. There is no need to import the NumPy functions explicitly, when SciPy is imported. The main object of NumPy is the homogeneous multidimensional array. It is a table of elements (usually numbers), all of the same type, indexed by a tuple of positive integers. In NumPy, dimensions are called as axes. The number of axes is called as rank.
Now, let us revise the basic functionality of Vectors and Matrices in NumPy. As SciPy is built on top of NumPy arrays, understanding of NumPy basics is necessary. As most parts of linear algebra deals with matrices only.
NumPy Vector
A Vector can be created in multiple ways. Some of them are described below.
Converting Python array-like objects to NumPy
Let us consider the following example.
import numpy as np
list = [1,2,3,4]
arr = np.array(list)
print arr
The output of the above program will be as follows.
[1 2 3 4]
Intrinsic NumPy Array Creation
NumPy has built-in functions for creating arrays from scratch. Some of these functions are explained below.
Using zeros()
The zeros(shape) function will create an array filled with 0 values with the specified shape. The default dtype is float64. Let us consider the following example.
import numpy as np
print np.zeros((2, 3))
The output of the above program will be as follows.
array([[ 0., 0., 0.],
[ 0., 0., 0.]])
Using ones()
The ones(shape) function will create an array filled with 1 values. It is identical to zeros in all the other respects. Let us consider the following example.
import numpy as np
print np.ones((2, 3))
The output of the above program will be as follows.
array([[ 1., 1., 1.],
[ 1., 1., 1.]])
Using arange()
The arange() function will create arrays with regularly incrementing values. Let us consider the following example.
import numpy as np
print np.arange(7)
The above program will generate the following output.
array([0, 1, 2, 3, 4, 5, 6])
Defining the data type of the values
Let us consider the following example.
import numpy as np
arr = np.arange(2, 10, dtype = np.float)
print arr
print "Array Data Type :",arr.dtype
The above program will generate the following output.
[ 2. 3. 4. 5. 6. 7. 8. 9.]
Array Data Type : float64
Using linspace()
The linspace() function will create arrays with a specified number of elements, which will be spaced equally between the specified beginning and end values. Let us consider the following example.
import numpy as np
print np.linspace(1., 4., 6)
The above program will generate the following output.
array([ 1. , 1.6, 2.2, 2.8, 3.4, 4. ])
Matrix
A matrix is a specialized 2-D array that retains its 2-D nature through operations. It has certain special operators, such as * (matrix multiplication) and ** (matrix power). Let us consider the following example.
import numpy as np
print np.matrix('1 2; 3 4')
The above program will generate the following output.
matrix([[1, 2],
[3, 4]])
Conjugate Transpose of Matrix
This feature returns the (complex) conjugate transpose of self. Let us consider the following example.
import numpy as np
mat = np.matrix('1 2; 3 4')
print mat.H
The above program will generate the following output.
matrix([[1, 3],
        [2, 4]])
Transpose of Matrix
This feature returns the transpose of self. Let us consider the following example.
import numpy as np
mat = np.matrix('1 2; 3 4')
mat.T
The above program will generate the following output.
matrix([[1, 3],
        [2, 4]])
When we transpose a matrix, we make a new matrix whose rows are the columns of the original. A conjugate transposition, on the other hand, interchanges the row and the column index for each matrix element. The inverse of a matrix is a matrix that, if multiplied with the original matrix, results in an identity matrix.


