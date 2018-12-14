

```python
SciPy - Linalg



SciPy is built using the optimized ATLAS LAPACK and BLAS libraries. It has very fast linear algebra capabilities. All of these linear algebra routines expect an object that can be converted into a two-dimensional array. The output of these routines is also a two-dimensional array.

#### SciPy.linalg vs NumPy.linalg
A scipy.linalg contains all the functions that are in numpy.linalg. Additionally, scipy.linalg also has some other advanced functions that are not in numpy.linalg. Another advantage of using scipy.linalg over numpy.linalg is that it is always compiled with BLAS/LAPACK support, while for NumPy this is optional. Therefore, the SciPy version might be faster depending on how NumPy was installed.

#### Linear Equations
The scipy.linalg.solve feature solves the linear equation a * x + b * y = Z, for the unknown x, y values.
As an example, assume that it is desired to solve the following simultaneous equations.
x + 3y + 5z = 10
2x + 5y + z = 8
2x + 3y + 8z = 3
```

$$ \begin{pmatrix} 1 \\ 2 \\ 3 \end{pmatrix}  = \begin{pmatrix} 1  &amp; 6 \\ 2 &amp; 6 \\ 3 &amp; 3 \end{pmatrix}$$


```python

To solve the above equation for the x, y, z values, we can find the solution vector using a matrix inverse as shown below.
⎡
⎣
⎢
x
y
z
⎤
⎦
⎥
=
⎡
⎣
⎢
1
2
2
3
5
3
5
1
8
⎤
⎦
⎥
−1
⎡
⎣
⎢
10
8
3
⎤
⎦
⎥
=
1
25

⎡
⎣
⎢
−232
129
19
⎤
⎦
⎥
=
⎡
⎣
⎢
−9.28
5.16
0.76
⎤
⎦
⎥
.



```

[xyz]=[135251238]−1[1083]=125[−23212919]=[−9.285.160.76].
However, it is better to use the linalg.solve command, which can be faster and more numerically stable.
The solve function takes two inputs ‘a’ and ‘b’ in which ‘a’ represents the coefficients and ‘b’ represents the respective right hand side value and returns the solution array.
Let us consider the following example.



```python

#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy arrays
a = np.array([[3, 2, 0], [1, -1, 0], [0, 5, 1]])
b = np.array([2, 4, -1])

#Passing the values to the solve function
x = linalg.solve(a, b)

#printing the result array
print(x)

```

    [ 2. -2.  9.]




#### Finding a Determinant
The determinant of a square matrix A is often denoted as |A| and is a quantity often used in linear algebra. In SciPy, this is computed using the det() function. It takes a matrix as input and returns a scalar value.
Let us consider the following example.


```python

#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy array
A = np.array([[1,2],[3,4]])

#Passing the values to the det function
x = linalg.det(A)

#printing the result
print(x)
```

    -2.0



```python
#### Eigenvalues and Eigenvectors
The eigenvalue-eigenvector problem is one of the most commonly employed linear algebra operations. We can find the Eigen values (λ) and the corresponding Eigen vectors (v) of a square matrix (A) by considering the following relation −
Av = λv
scipy.linalg.eig computes the eigenvalues from an ordinary or generalized eigenvalue problem. This function returns the Eigen values and the Eigen vectors.

Let us consider the following example.

```


```python
#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy array
A = np.array([[1,2],[3,4]])

#Passing the values to the eig function
l, v = linalg.eig(A)

#printing the result for eigen values
print(l)

#printing the result for eigen vectors
print(v)
```

    [-0.37228132+0.j  5.37228132+0.j]
    [[-0.82456484 -0.41597356]
     [ 0.56576746 -0.90937671]]



```python



The above program will generate the following output.
array([-0.37228132+0.j, 5.37228132+0.j]) #--Eigen Values
array([[-0.82456484, -0.41597356], #--Eigen Vectors
       [ 0.56576746, -0.90937671]])


```

#### Singular Value Decomposition
A Singular Value Decomposition (SVD) can be thought of as an extension of the eigenvalue problem to matrices that are not square.
The scipy.linalg.svd factorizes the matrix ‘a’ into two unitary matrices ‘U’ and ‘Vh’ and a 1-D array ‘s’ of singular values (real, non-negative) such that a == U*S*Vh, where ‘S’ is a suitably shaped matrix of zeros with the main diagonal ‘s’.
Let us consider the following example.


```python

#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy array
a = np.random.randn(3, 2) + 1.j*np.random.randn(3, 2)

#Passing the values to the eig function
U, s, Vh = linalg.svd(a)

# printing the result
print(U, Vh, s)

```

    [[-0.53702482+0.10989141j -0.28819535+0.36707585j -0.09037427+0.68815657j]
     [-0.03492613-0.48530979j  0.69487486-0.23386121j  0.04953132+0.472503j  ]
     [ 0.14530431-0.66458216j -0.34767678+0.35182024j  0.53918131-0.04294304j]] [[-0.67556375+0.j          0.73585306-0.04619409j]
     [-0.73730158+0.j         -0.67423652+0.04232604j]] [2.22450039 1.12640672]

