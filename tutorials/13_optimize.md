
SciPy - Optimize

The scipy.optimize package provides several commonly used optimization algorithms. This module contains the following aspects −
Unconstrained and constrained minimization of multivariate scalar functions (minimize()) using a variety of algorithms (e.g. BFGS, Nelder-Mead simplex, Newton Conjugate Gradient, COBYLA or SLSQP)
Global (brute-force) optimization routines (e.g., anneal(), basinhopping())
Least-squares minimization (leastsq()) and curve fitting (curve_fit()) algorithms
Scalar univariate functions minimizers (minimize_scalar()) and root finders (newton())
Multivariate equation system solvers (root()) using a variety of algorithms (e.g. hybrid Powell, Levenberg-Marquardt or large-scale methods such as Newton-Krylov)
Unconstrained & Constrained minimization of multivariate scalar functions
The minimize() function provides a common interface to unconstrained and constrained minimization algorithms for multivariate scalar functions in scipy.optimize. To demonstrate the minimization function, consider the problem of minimizing the Rosenbrock function of the NN variables −
f(x)=
∑
i=1
N−1
100(
x
i
−
x
2
i−1
)
f(x)=∑i=1N−1100(xi−xi−12)
The minimum value of this function is 0, which is achieved when xi = 1.

#### Nelder–Mead Simplex Algorithm
In the following example, the minimize() routine is used with the Nelder-Mead simplex algorithm (method = 'Nelder-Mead') (selected through the method parameter). Let us consider the following example.
import numpy as np
from scipy.optimize import minimize

def rosen(x):

x0 = np.array([1.3, 0.7, 0.8, 1.9, 1.2])
res = minimize(rosen, x0, method='nelder-mead')

print(res.x)
The above program will generate the following output.
[7.93700741e+54  -5.41692163e+53  6.28769150e+53  1.38050484e+55  -4.14751333e+54]
The simplex algorithm is probably the simplest way to minimize a fairly well-behaved function. It requires only function evaluations and is a good choice for simple minimization problems. However, because it does not use any gradient evaluations, it may take longer to find the minimum.
Another optimization algorithm that needs only function calls to find the minimum is the Powell‘s method, which is available by setting method = 'powell' in the minimize() function. 
Least Squares
Solve a nonlinear least-squares problem with bounds on the variables. Given the residuals f(x) (an m-dimensional real function of n real variables) and the loss function rho(s) (a scalar function), least_squares find a local minimum of the cost function F(x). Let us consider the following example.
In this example, we find a minimum of the Rosenbrock function without bounds on the independent variables.
#Rosenbrock Function
def fun_rosenbrock(x):
   return np.array([10 * (x[1] - x[0]**2), (1 - x[0])])
   
from scipy.optimize import least_squares
input = np.array([2, 2])
res = least_squares(fun_rosenbrock, input)

print res
Notice that, we only provide the vector of the residuals. The algorithm constructs the cost function as a sum of squares of the residuals, which gives the Rosenbrock function. The exact minimum is at x = [1.0,1.0].
The above program will generate the following output.
active_mask: array([ 0., 0.])
      cost: 9.8669242910846867e-30
      fun: array([ 4.44089210e-15, 1.11022302e-16])
      grad: array([ -8.89288649e-14, 4.44089210e-14])
      jac: array([[-20.00000015,10.],[ -1.,0.]])
   message: '`gtol` termination condition is satisfied.'
      nfev: 3
      njev: 3
   optimality: 8.8928864934219529e-14
      status: 1
      success: True
         x: array([ 1., 1.])
Root finding
Let us understand how root finding helps in SciPy.
Scalar functions
If one has a single-variable equation, there are four different root-finding algorithms, which can be tried. Each of these algorithms require the endpoints of an interval in which a root is expected (because the function changes signs). In general, brentq is the best choice, but the other methods may be useful in certain circumstances or for academic purposes.
Fixed-point solving
A problem closely related to finding the zeros of a function is the problem of finding a fixed point of a function. A fixed point of a function is the point at which evaluation of the function returns the point: g(x) = x. Clearly the fixed point of gg is the root of f(x) = g(x)−x. Equivalently, the root of ff is the fixed_point of g(x) = f(x)+x. The routine fixed_point provides a simple iterative method using the Aitkens sequence acceleration to estimate the fixed point of gg, if a starting point is given.
Sets of equations
Finding a root of a set of non-linear equations can be achieved using the root() function. Several methods are available, amongst which hybr (the default) and lm, respectively use the hybrid method of Powell and the Levenberg-Marquardt method from the MINPACK.
The following example considers the single-variable transcendental equation.
x2 + 2cos(x) = 0
A root of which can be found as follows −
import numpy as np
from scipy.optimize import root
def func(x):
   return x*2 + 2 * np.cos(x)
sol = root(func, 0.3)
print sol
The above program will generate the following output.
fjac: array([[-1.]])
fun: array([ 2.22044605e-16])
message: 'The solution converged.'
   nfev: 10
   qtf: array([ -2.77644574e-12])
      r: array([-3.34722409])
   status: 1
   success: True
      x: array([-0.73908513])


