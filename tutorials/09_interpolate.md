
 
 
SciPy - Interpolate




In this chapter, we will discuss how interpolation helps in SciPy.
What is Interpolation?
Interpolation is the process of finding a value between two points on a line or a curve. To help us remember what it means, we should think of the first part of the word, 'inter,' as meaning 'enter,' which reminds us to look 'inside' the data we originally had. This tool, interpolation, is not only useful in statistics, but is also useful in science, business, or when there is a need to predict values that fall within two existing data points.
Let us create some data and see how this interpolation can be done using the scipy.interpolate package.
import numpy as np
from scipy import interpolate
import matplotlib.pyplot as plt
x = np.linspace(0, 4, 12)
y = np.cos(x**2/3+4)
print x,y
The above program will generate the following output.
(
   array([0.,  0.36363636,  0.72727273,  1.09090909,  1.45454545, 1.81818182, 
          2.18181818,  2.54545455,  2.90909091,  3.27272727,  3.63636364,  4.]),
            
   array([-0.65364362,  -0.61966189,  -0.51077021,  -0.31047698,  -0.00715476,
           0.37976236,   0.76715099,   0.99239518,   0.85886263,   0.27994201,
          -0.52586509,  -0.99582185])
)
Now, we have two arrays. Assuming those two arrays as the two dimensions of the points in space, let us plot using the following program and see how they look like.
plt.plot(x, y,’o’)
plt.show()
The above program will generate the following output.
 
1-D Interpolation
The interp1d class in the scipy.interpolate is a convenient method to create a function based on fixed data points, which can be evaluated anywhere within the domain defined by the given data using linear interpolation.
By using the above data, let us create a interpolate function and draw a new interpolated graph.
f1 = interp1d(x, y,kind = 'linear')

f2 = interp1d(x, y, kind = 'cubic')
Using the interp1d function, we created two functions f1 and f2. These functions, for a given input x returns y. The third variable kind represents the type of the interpolation technique. 'Linear', 'Nearest', 'Zero', 'Slinear', 'Quadratic', 'Cubic' are a few techniques of interpolation.
Now, let us create a new input of more length to see the clear difference of interpolation. We will use the same function of the old data on the new data.
xnew = np.linspace(0, 4,30)

plt.plot(x, y, 'o', xnew, f(xnew), '-', xnew, f2(xnew), '--')

plt.legend(['data', 'linear', 'cubic','nearest'], loc = 'best')

plt.show()
The above program will generate the following output.
 
Splines
To draw smooth curves through data points, drafters once used thin flexible strips of wood, hard rubber, metal or plastic called mechanical splines. To use a mechanical spline, pins were placed at a judicious selection of points along a curve in a design, and then the spline was bent, so that it touched each of these pins.
Clearly, with this construction, the spline interpolates the curve at these pins. It can be used to reproduce the curve in other drawings. The points where the pins are located is called knots. We can change the shape of the curve defined by the spline by adjusting the location of the knots.
Univariate Spline
One-dimensional smoothing spline fits a given set of data points. The UnivariateSpline class in scipy.interpolate is a convenient method to create a function, based on fixed data points class – scipy.interpolate.UnivariateSpline(x, y, w = None, bbox = [None, None], k = 3, s = None, ext = 0, check_finite = False).
Parameters − Following are the parameters of a Univariate Spline.
This fits a spline y = spl(x) of degree k to the provided x, y data.
‘w’ − Specifies the weights for spline fitting. Must be positive. If none (default), weights are all equal.
‘s’ − Specifies the number of knots by specifying a smoothing condition.
‘k’ − Degree of the smoothing spline. Must be <= 5. Default is k = 3, a cubic spline.
Ext − Controls the extrapolation mode for elements not in the interval defined by the knot sequence.
if ext = 0 or ‘extrapolate’, returns the extrapolated value.
if ext = 1 or ‘zero’, returns 0
if ext = 2 or ‘raise’, raises a ValueError
if ext = 3 of ‘const’, returns the boundary value.
check_finite – Whether to check that the input arrays contain only finite numbers.
Let us consider the following example.
import matplotlib.pyplot as plt
from scipy.interpolate import UnivariateSpline
x = np.linspace(-3, 3, 50)
y = np.exp(-x**2) + 0.1 * np.random.randn(50)
plt.plot(x, y, 'ro', ms = 5)
plt.show()
Use the default value for the smoothing parameter.
 
spl = UnivariateSpline(x, y)
xs = np.linspace(-3, 3, 1000)
plt.plot(xs, spl(xs), 'g', lw = 3)
plt.show()
Manually change the amount of smoothing.
 
spl.set_smoothing_factor(0.5)
plt.plot(xs, spl(xs), 'b', lw = 3)
plt.show()
 

