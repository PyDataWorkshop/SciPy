
SciPy - FFTpack



Fourier Transformation is computed on a time domain signal to check its behavior in the frequency domain. Fourier transformation finds its application in disciplines such as signal and noise processing, image processing, audio signal processing, etc. SciPy offers the fftpack module, which lets the user compute fast Fourier transforms.
Following is an example of a sine function, which will be used to calculate Fourier transform using the fftpack module.

## Fast Fourier Transform
Let us understand what fast Fourier transform is in detail.

#### One Dimensional Discrete Fourier Transform
The FFT y[k] of length N of the length-N sequence x[n] is calculated by fft() and the inverse transform is calculated using ifft(). Let us consider the following example



```python
#Importing the fft and inverse fft functions from fftpackage
from scipy.fftpack import fft
import numpy as np

#create an array with random n numbers
x = np.array([1.0, 2.0, 1.0, -1.0, 1.5])

#Applying the fft function
y = fft(x)
print(y)
```

    [ 4.5       +0.j          2.08155948-1.65109876j -1.83155948+1.60822041j
     -1.83155948-1.60822041j  2.08155948+1.65109876j]



```python
The above program will generate the following output.
[ 4.50000000+0.j           2.08155948-1.65109876j   -1.83155948+1.60822041j
 -1.83155948-1.60822041j   2.08155948+1.65109876j ]
Let us look at another example
#FFT is already in the workspace, using the same workspace to for inverse transform

yinv = ifft(y)

print yinv

```


```python
The above program will generate the following output.
[ 1.0+0.j   2.0+0.j   1.0+0.j   -1.0+0.j   1.5+0.j ]
The scipy.fftpack module allows computing fast Fourier transforms. As an illustration, a (noisy) input signal may look as follows −

```


```python
import numpy as np
time_step = 0.02
period = 5.
time_vec = np.arange(0, 20, time_step)
sig = np.sin(2 * np.pi / period * time_vec) + 0.5 *np.random.randn(time_vec.size)
print sig.size
```

We are creating a signal with a time step of 0.02 seconds. 
The last statement prints the size of the signal sig. The output would be as follows −
1000
We do not know the signal frequency; we only know the sampling time step of the signal sig. The signal is supposed to come from a real function, so the Fourier transform will be symmetric. The scipy.fftpack.fftfreq() function will generate the sampling frequencies and scipy.fftpack.fft() will compute the fast Fourier transform.
Let us understand this with the help of an example.



```python
from scipy import fftpack
sample_freq = fftpack.fftfreq(sig.size, d = time_step)
sig_fft = fftpack.fft(sig)
print sig_fft
```


```python





The above program will generate the following output.
array([ 
   25.45122234 +0.00000000e+00j,   6.29800973 +2.20269471e+00j,
   11.52137858 -2.00515732e+01j,   1.08111300 +1.35488579e+01j,
   …….])
   



```


```python
#### Discrete Cosine Transform
A Discrete Cosine Transform (DCT) expresses a finite sequence of data points in terms of a sum of cosine functions oscillating at different frequencies. SciPy provides a DCT with the function dct and a corresponding IDCT with the function idct. Let us consider the following example.
from scipy.fftpack import dct
print dct(np.array([4., 3., 5., 10., 5., 3.]))
```


```python

The above program will generate the following output.
```


```python

array([ 60.,  -3.48476592,  -13.85640646,  11.3137085,  6.,  -6.31319305])
The inverse discrete cosine transform reconstructs a sequence from its discrete cosine transform (DCT) coefficients. The idct function is the inverse of the dct function. Let us understand this with the following example.



```


```python
from scipy.fftpack import dct
print idct(np.array([4., 3., 5., 10., 5., 3.]))
```


```python

The above program will generate the following output.
array([ 39.15085889, -20.14213562, -6.45392043, 7.13341236,
8.14213562, -3.83035081])

```
