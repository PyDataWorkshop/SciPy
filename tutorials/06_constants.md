
## SciPy - Constants



SciPy constants package provides a wide range of constants, which are used in the general scientific area.

#### 1. SciPy Constants Package
The scipy.constants package provides various constants. We have to import the required constant and use them as per the requirement. Let us see how these constant variables are imported and used.
To start with, let us compare the ‘pi’ value by considering the following example.
<pre><code>
#Import pi constant from both the packages
from scipy.constants import pi
from math import pi

print("sciPy - pi = %.16f"%scipy.constants.pi)
print("math - pi = %.16f"%math.pi)
<code></pre>
The above program will generate the following output.
sciPy - pi = 3.1415926535897931
math - pi = 3.1415926535897931

#### List of Constants Available
The following tables describe in brief the various constants.
Mathematical Constants

Sr. No.
Constant
Description
1
pi
pi
2
golden
Golden Ratio
Physical Constants
The following table lists the most commonly used physical constants.
Sr. No.
Constant & Description
1
c
Speed of light in vacuum
2
speed_of_light
Speed of light in vacuum
3
h
Planck constant
4
Planck
Planck constant h
5
G
Newton’s gravitational constant
6
e
Elementary charge
7
R
Molar gas constant
8
Avogadro
Avogadro constant
9
k
Boltzmann constant
10
electron_mass(OR) m_e
Electronic mass
11
proton_mass (OR) m_p
Proton mass
12
neutron_mass(OR)m_n
Neutron mass
Units
The following table has the list of SI units.
Sr. No.
Unit
Value
1
milli
0.001
2
micro
1e-06
3
kilo
1000
These units range from yotta, zetta, exa, peta, tera ……kilo, hector, …nano, pico, … to zepto.
Other Important Constants
The following table lists other important constants used in SciPy.
Sr. No.
Unit
Value
1
gram
0.001 kg
2
atomic mass
Atomic mass constant
3
degree
Degree in radians
4
minute
One minute in seconds
5
day
One day in seconds
6
inch
One inch in meters
7 micron: One micron in meters
8 light_year: One light-year in meters
9 atm
Standard atmosphere in pascals
10
acre: One acre in square meters
11
liter: One liter in cubic meters
12 gallon: One gallon in cubic meters
13
kmh
Kilometers per hour in meters per seconds
14: degree_Fahrenheit
One Fahrenheit in kelvins
15
eV
One electron volt in joules
16
hp
One horsepower in watts
17
dyn: One dyne in newtons
18:  lambda2nu

#### Convert wavelength to optical frequency

Remembering all of these are a bit tough. The easy way to get which key is for which function is with the scipy.constants.find() method. Let us consider the following example.
<pre><code>
import scipy.constants
res = scipy.constants.physical_constants["alpha particle mass"]
print res
</code></pre>


The above program will generate the following output.
<pre><code>
[
   'alpha particle mass',
   'alpha particle mass energy equivalent',
   'alpha particle mass energy equivalent in MeV',
   'alpha particle mass in u',
   'electron to alpha particle mass ratio'
]
</code></pre>

This method returns the list of keys, else nothing if the keyword does not match.

