#### SciPy - Special Package


The functions available in the special package are universal functions, which follow broadcasting and automatic array looping.
Let us look at some of the most frequently used special functions −
Cubic Root Function
Exponential Function
Relative Error Exponential Function
Log Sum Exponential Function
Lambert Function
Permutations and Combinations Function

#### Gamma Function
Let us now understand each of these functions in brief.
Cubic Root Function
The syntax of this cubic root function is – scipy.special.cbrt(x). This will fetch the element-wise cube root of x.
Let us consider the following example.
from scipy.special import cbrt
res = cbrt([10, 9, 0.1254, 234])
print res
The above program will generate the following output.
[ 2.15443469 2.08008382 0.50053277 6.16224015]

##### Exponential Function
The syntax of the exponential function is – scipy.special.exp10(x). This will compute 10**x element wise.
Let us consider the following example.
from scipy.special import exp10
res = exp10([2, 9])
print res
The above program will generate the following output.
[1.00000000e+02  1.00000000e+09]
Relative Error Exponential Function
The syntax for this function is – scipy.special.exprel(x). It generates the relative error exponential, (exp(x) - 1)/x.
When x is near zero, exp(x) is near 1, so the numerical calculation of exp(x) - 1 can suffer from catastrophic loss of precision. Then exprel(x) is implemented to avoid the loss of precision, which occurs when x is near zero.
Let us consider the following example.
from scipy.special import exprel
res = exprel([-0.25, -0.1, 0, 0.1, 0.25])
print res
The above program will generate the following output.
[0.88479687 0.95162582 1.   1.05170918 1.13610167]
Log Sum Exponential Function
The syntax for this function is – scipy.special.logsumexp(x). It helps to compute the log of the sum of exponentials of input elements.
Let us consider the following example.
<pre><code>
from scipy.special import logsumexp
import numpy as np
a = np.arange(10)
res = logsumexp(a)
print res
</code></pre>
The above program will generate the following output.
9.45862974443

##### Lambert Function
The syntax for this function is – scipy.special.lambertw(x). It is also called as the Lambert W function. The Lambert W function W(z) is defined as the inverse function of w * exp(w). In other words, the value of W(z) is such that z = W(z) * exp(W(z)) for any complex number z.
The Lambert W function is a multivalued function with infinitely many branches. Each branch gives a separate solution of the equation z = w exp(w). Here, the branches are indexed by the integer k.
Let us consider the following example. Here, the Lambert W function is the inverse of w exp(w).
<pre><code>
from scipy.special import lambertw
w = lambertw(1)
print w
print w * np.exp(w)
</code></pre>
The above program will generate the following output.
(0.56714329041+0j)
(1+0j)

#### Permutations & Combinations
Let us discuss permutations and combinations separately for understanding them clearly.
Combinations − The syntax for combinations function is – scipy.special.comb(N,k). Let us consider the following example −
from scipy.special import comb
res = comb(10, 3, exact = False,repetition=True)
print res
The above program will generate the following output.
220.0
Note − Array arguments are accepted only for exact = False case. If k > N, N < 0, or k < 0, then a 0 is returned.
Permutations − The syntax for combinations function is – scipy.special.perm(N,k). Permutations of N things taken k at a time, i.e., k-permutations of N. This is also known as “partial permutations”.
Let us consider the following example.
from scipy.special import perm
res = perm(10, 3, exact = True)
print res
The above program will generate the following output.
720

#### Gamma Function
The gamma function is often referred to as the generalized factorial since z*gamma(z) = gamma(z+1) and gamma(n+1) = n!, for a natural number ‘n’.
The syntax for combinations function is – scipy.special.gamma(x). Permutations of N things taken k at a time, i.e., k-permutations of N. This is also known as “partial permutations”.
The syntax for combinations function is – scipy.special.gamma(x). Permutations of N things taken k at a time, i.e., k-permutations of N. This is also known as “partial permutations”.
from scipy.special import gamma
res = gamma([0, 0.5, 1, 5])
print res
The above program will generate the following output.
[inf  1.77245385  1.  24.]

