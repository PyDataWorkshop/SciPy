SciPy - Linalg



SciPy is built using the optimized ATLAS LAPACK and BLAS libraries. It has very fast linear algebra capabilities. All of these linear algebra routines expect an object that can be converted into a two-dimensional array. The output of these routines is also a two-dimensional array.

#### SciPy.linalg vs NumPy.linalg
A scipy.linalg contains all the functions that are in numpy.linalg. Additionally, scipy.linalg also has some other advanced functions that are not in numpy.linalg. Another advantage of using scipy.linalg over numpy.linalg is that it is always compiled with BLAS/LAPACK support, while for NumPy this is optional. Therefore, the SciPy version might be faster depending on how NumPy was installed.

#### Linear Equations
The scipy.linalg.solve feature solves the linear equation a * x + b * y = Z, for the unknown x, y values.
As an example, assume that it is desired to solve the following simultaneous equations.
\[
x + 3y + 5z = 10
2x + 5y + z = 8
2x + 3y + 8z = 3
\]
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
[xyz]=[135251238]−1[1083]=125[−23212919]=[−9.285.160.76].
However, it is better to use the linalg.solve command, which can be faster and more numerically stable.
The solve function takes two inputs ‘a’ and ‘b’ in which ‘a’ represents the coefficients and ‘b’ represents the respective right hand side value and returns the solution array.
Let us consider the following example.
<pre><code>
#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy arrays
a = np.array([[3, 2, 0], [1, -1, 0], [0, 5, 1]])
b = np.array([2, 4, -1])

#Passing the values to the solve function
x = linalg.solve(a, b)

#printing the result array
print x
</code></pre>
The above program will generate the following output.
array([ 2., -2., 9.])

#### Finding a Determinant
The determinant of a square matrix A is often denoted as |A| and is a quantity often used in linear algebra. In SciPy, this is computed using the det() function. It takes a matrix as input and returns a scalar value.
Let us consider the following example.
<pre><code>
#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy array
A = np.array([[1,2],[3,4]])

#Passing the values to the det function
x = linalg.det(A)

#printing the result
print x
<code></pre>
The above program will generate the following output.
-2.0

#### Eigenvalues and Eigenvectors
The eigenvalue-eigenvector problem is one of the most commonly employed linear algebra operations. We can find the Eigen values (λ) and the corresponding Eigen vectors (v) of a square matrix (A) by considering the following relation −
Av = λv
scipy.linalg.eig computes the eigenvalues from an ordinary or generalized eigenvalue problem. This function returns the Eigen values and the Eigen vectors.

Let us consider the following example.
<pre><code>
#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy array
A = np.array([[1,2],[3,4]])

#Passing the values to the eig function
l, v = linalg.eig(A)

#printing the result for eigen values
print l

#printing the result for eigen vectors
print v
</code></pre>
The above program will generate the following output.
<pre><code>
array([-0.37228132+0.j, 5.37228132+0.j]) #--Eigen Values
array([[-0.82456484, -0.41597356], #--Eigen Vectors
       [ 0.56576746, -0.90937671]])
</code></pre>      
### Singular Value Decomposition
A Singular Value Decomposition (SVD) can be thought of as an extension of the eigenvalue problem to matrices that are not square.
The scipy.linalg.svd factorizes the matrix ‘a’ into two unitary matrices ‘U’ and ‘Vh’ and a 1-D array ‘s’ of singular values (real, non-negative) such that a == U*S*Vh, where ‘S’ is a suitably shaped matrix of zeros with the main diagonal ‘s’.
Let us consider the following example.
<pre><code>
#importing the scipy and numpy packages
from scipy import linalg
import numpy as np

#Declaring the numpy array
a = np.random.randn(3, 2) + 1.j*np.random.randn(3, 2)

#Passing the values to the eig function
U, s, Vh = linalg.svd(a)

# printing the result
print U, Vh, s
</code></pre>
The above program will generate the following output.
<pre><code>
(
   array([
      [ 0.54828424-0.23329795j, -0.38465728+0.01566714j,
      -0.18764355+0.67936712j],
      [-0.27123194-0.5327436j , -0.57080163-0.00266155j,
      -0.39868941-0.39729416j],
      [ 0.34443818+0.4110186j , -0.47972716+0.54390586j,
      0.25028608-0.35186815j]
   ]),

   array([ 3.25745379, 1.16150607]),

   array([
      [-0.35312444+0.j , 0.32400401+0.87768134j],
      [-0.93557636+0.j , -0.12229224-0.33127251j]
   ])
)


</code></pre>
