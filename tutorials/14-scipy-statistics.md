
## SciPy - Stats


All of the statistics functions are located in the sub-package scipy.stats and a fairly complete listing of these functions can be obtained using info(stats) function. A list of random variables available can also be obtained from the docstring for the stats sub-package. This module contains a large number of probability distributions as well as a growing library of statistical functions.

Each univariate distribution has its own subclass as described in the following list 

* 1 ``rv_continuous``: A generic continuous random variable class meant for subclassing
* 2 ``rv_discrete``: A generic discrete random variable class meant for subclassing
* 3 ``rv_histogram``: Generates a distribution given by a histogram


```python
import scipy.stats
```

### Normal Continuous Random Variable
A probability distribution in which the random variable X can take any value is continuous random variable. The location (loc) keyword specifies the mean. The scale (scale) keyword specifies the standard deviation.

As an instance of the ``rv_continuous`` class, norm object inherits from it a collection of generic methods and completes them with details specific for this particular distribution.

To compute the CDF at a number of points, we can pass a list or a NumPy array. Let us consider the following example.



```python
from scipy.stats import norm
import numpy as np
print(norm.cdf(np.array([1,-1., 0, 1, 3, 4, -2, 6])))
```

    [0.84134475 0.15865525 0.5        0.84134475 0.9986501  0.99996833
     0.02275013 1.        ]


To find the median of a distribution, we can use the Percent Point Function (PPF), which is the inverse of the CDF. 
Let us understand by using the following example.


```python
from scipy.stats import norm
print(norm.ppf(0.5))
```

    0.0


To generate a sequence of random variates, we should use the size keyword argument, which is shown in the following example.



```python
from scipy.stats import norm
print(norm.rvs(size = 5))


```

    [ 0.71960502 -0.11906798 -0.73291816 -1.63043358  1.22701588]



```python

The above output is not reproducible. To generate the same random numbers, use the seed function.
```

### Uniform Distribution
A uniform distribution can be generated using the uniform function. Let us consider the following example.



```python
from scipy.stats import uniform
print uniform.cdf([0, 1, 2, 3, 4, 5], loc = 1, scale = 4)
The above program will generate the following output.
array([ 0. , 0. , 0.25, 0.5 , 0.75, 1. ])
```


```python
Build Discrete Distribution
Let us generate a random sample and compare the observed frequencies with the probabilities.
```


```python


#### Binomial Distribution
As an instance of the ``rv_discrete class, the binom object inherits from it a collection of generic methods and completes them with details specific for this particular distribution. Let us consider the following example.

```


```python
from scipy.stats import uniform
print( uniform.cdf([0, 1, 2, 3, 4, 5], loc = 1, scale = 4) )
```

    [0.   0.   0.25 0.5  0.75 1.  ]


### Descriptive Statistics
The basic stats such as Min, Max, Mean and Variance takes the NumPy array as input and returns the respective results. A few basic statistical functions available in the scipy.stats package are described in the following table.


1. ``describe()``: Computes several descriptive statistics of the passed array
2. ``gmean()``: Computes geometric mean along the specified axis
3. ``hmean()``: Calculates the harmonic mean along the specified axis
4. ``kurtosis()``: Computes the kurtosis
5. ``mode()``: Returns the modal value
6. ``skew()``: Tests the skewness of the data
7. ``_oneway()``: Performs a 1-way ANOVA
8. ``iqr()``: Computes the interquartile range of the data along the specified axis
9. ``zscore()``: Calculates the z score of each value in the sample, relative to the sample mean and standard deviation
10. ``sem()``: Calculates the standard error of the mean (or standard error of measurement) of the values in the input array



```python
Several of these functions have a similar version in the scipy.stats.mstats, which work for masked arrays. Let us understand this with the example given below.

```


```python

from scipy import stats
import numpy as np
x = np.array([1,2,3,4,5,6,7,8,9])
print(x.max(),x.min(),x.mean(),x.var())



```

    9 1 5.0 6.666666666666667



```python
### T-test
Let us understand how T-test is useful in SciPy.

### ttest_1samp
Calculates the T-test for the mean of ONE group of scores. 
This is a two-sided test for the null hypothesis that the expected value (mean) of a sample of independent 
observations ‘a’ is equal to the given population mean, popmean. Let us consider the following example.


```


```python
from scipy import stats
rvs = stats.norm.rvs(loc = 5, scale = 10, size = (50,2))
print(stats.ttest_1samp(rvs,5.0))

```

    Ttest_1sampResult(statistic=array([ 0.01428355, -0.62429212]), pvalue=array([0.98866176, 0.53533178]))



```python
The above program will generate the following output.
Ttest_1sampResult(statistic = array([-1.40184894, 2.70158009]),
pvalue = array([ 0.16726344, 0.00945234]))
```

### Comparing two samples

In the following examples, there are two samples, which can come either from the same or from different distribution, and we want to test whether these samples have the same statistical properties.

``ttest_ind``− Calculates the T-test for the means of two independent samples of scores. 

This is a two-sided test for the null hypothesis that two independent samples have identical average (expected) values. This test assumes that the populations have identical variances by default.

We can use this test, if we observe two independent samples from the same or different population. 

Let us consider the following example.



```python
from scipy import stats
rvs1 = stats.norm.rvs(loc = 5,scale = 10,size = 500)
rvs2 = stats.norm.rvs(loc = 5,scale = 10,size = 500)
print(stats.ttest_ind(rvs1,rvs2))

```

    Ttest_indResult(statistic=-0.4192258530153042, pvalue=0.6751412960942891)



You can test the same with a new array of the same length, but with a varied mean. 
Use a different value in loc and test the same.

