SciPy - Input & Output

The Scipy.io (Input and Output) package provides a wide range of functions to work around with different format of files. Some of these formats are −

* Matlab
* IDL
* Matrix Market
* Wave
* Arff
* Netcdf, etc.

Let us discuss in detail about the most commonly used file formats −

### MATLAB
Following are the functions used to load and save a .mat file.
Sr. No.
Function & Description

1. ``loadmat``: Loads a MATLAB file
2. ``savemat``: Saves a MATLAB file
3. ``whosmat``: Lists variables inside a MATLAB file

Let us consider the following example.
<pre><code>
import scipy.io as sio
import numpy as np

#Save a mat file
vect = np.arange(10)
sio.savemat('array.mat', {'vect':vect})

#Now Load the File
mat_file_content = sio.loadmat(‘array.mat’)
Print mat_file_content
</code></pre>
The above program will generate the following output.
<pre><code>
{
   'vect': array([[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]]), '__version__': '1.0', 
   '__header__': 'MATLAB 5.0 MAT-file Platform: posix, Created on: Sat Sep 30 
   09:49:32 2017', '__globals__': []
}
</code></pre>
We can see the array along with the Meta information. If we want to inspect the contents of a MATLAB file without reading the data into memory, use the whosmat command as shown below.
<pre><code>
import scipy.io as sio
mat_file_content = sio.whosmat(‘array.mat’)
print mat_file_content
</code></pre>
The above program will generate the following output.
<pre><code>
[('vect', (1, 10), 'int64')]
</code></pre>

