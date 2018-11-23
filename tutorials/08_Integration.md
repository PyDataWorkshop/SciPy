SciPy - Integrate


When a function cannot be integrated analytically, or is very difficult to integrate analytically, one generally turns to numerical integration methods. SciPy has a number of routines for performing numerical integration. Most of them are found in the same scipy.integrate library. The following table lists some commonly used functions.
Sr No.
Function & Description
1
quad
Single integration
2
dblquad
Double integration
3
tplquad
Triple integration
4
nquad
n-fold multiple integration
5
fixed_quad
Gaussian quadrature, order n
6
quadrature
Gaussian quadrature to tolerance
7
romberg
Romberg integration
8
trapz
Trapezoidal rule
9
cumtrapz
Trapezoidal rule to cumulatively compute integral
10
simps
Simpson’s rule
11
romb
Romberg integration
12
polyint
Analytical polynomial integration (NumPy)
13
poly1d
Helper function for polyint (NumPy)
Single Integrals
The Quad function is the workhorse of SciPy’s integration functions. Numerical integration is sometimes called quadrature, hence the name. It is normally the default choice for performing single integrals of a function f(x) over a given fixed range from a to b.
∫
b
a
f(x)dx
∫abf(x)dx
The general form of quad is scipy.integrate.quad(f, a, b), Where ‘f’ is the name of the function to be integrated. Whereas, ‘a’ and ‘b’ are the lower and upper limits, respectively. Let us see an example of the Gaussian function, integrated over a range of 0 and 1.
We first need to define the function → 
f(x)=
e
−
x
2
f(x)=e−x2
, this can be done using a lambda expression and then call the quad method on that function.
import scipy.integrate
from numpy import exp
f= lambda x:exp(-x**2)
i = scipy.integrate.quad(f, 0, 1)
print i
The above program will generate the following output.
(0.7468241328124271, 8.291413475940725e-15)
The quad function returns the two values, in which the first number is the value of integral and the second value is the estimate of the absolute error in the value of integral.
Note − Since quad requires the function as the first argument, we cannot directly pass exp as the argument. The Quad function accepts positive and negative infinity as limits. The Quad function can integrate standard predefined NumPy functions of a single variable, such as exp, sin and cos.
Multiple Integrals
The mechanics for double and triple integration have been wrapped up into the functions dblquad, tplquad and nquad. These functions integrate four or six arguments, respectively. The limits of all inner integrals need to be defined as functions.
Double Integrals
The general form of dblquad is scipy.integrate.dblquad(func, a, b, gfun, hfun). Where, func is the name of the function to be integrated, ‘a’ and ‘b’ are the lower and upper limits of the x variable, respectively, while gfun and hfun are the names of the functions that define the lower and upper limits of the y variable.
As an example, let us perform the double integral method.
∫
1/2
0
dy
∫
1−4
y
2

√
0
16xydx
∫01/2dy∫01−4y216xydx
We define the functions f, g, and h, using the lambda expressions. Note that even if g and h are constants, as they may be in many cases, they must be defined as functions, as we have done here for the lower limit.
import scipy.integrate
from numpy import exp
from math import sqrt
f = lambda x, y : 16*x*y
g = lambda x : 0
h = lambda y : sqrt(1-4*y**2)
i = scipy.integrate.dblquad(f, 0, 0.5, g, h)
print i
The above program will generate the following output.
(0.5, 1.7092350012594845e-14)
In addition to the routines described above, scipy.integrate has a number of other integration routines, including nquad, which performs n-fold multiple integration, as well as other routines that implement various integration algorithms. However, quad and dblquad will meet most of our needs for numerical integration.

