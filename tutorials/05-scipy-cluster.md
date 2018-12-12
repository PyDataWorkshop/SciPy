
SciPy - Cluster
================


K-means clustering is a method for finding clusters and cluster centers in a set of unlabelled data. Intuitively, we might think of a cluster as – comprising of a group of data points, whose inter-point distances are small compared with the distances to points outside of the cluster. Given an initial set of K centers, the K-means algorithm iterates the following two steps −

1. For each center, the subset of training points (its cluster) that is closer to it is identified than any other center.
2. The mean of each feature for the data points in each cluster are computed, and this mean vector becomes the new center for that cluster.

These two steps are iterated until the centers no longer move or the assignments no longer change. Then, a new point x can be assigned to the cluster of the closest prototype. 

The SciPy library provides a good implementation of the K-Means algorithm through the cluster package. Let us understand how to use it.

### K-Means Implementation in SciPy
We will understand how to implement K-Means in SciPy.

#### Import K-Means
We will see the implementation and usage of each imported function.


```python
import scipy.cluster
from scipy.cluster.vq import kmeans,vq,whiten

#### Data generation
#We have to simulate some data to explore the clustering.
from numpy import vstack,array
from numpy.random import rand

# data generation with three features
data = vstack((rand(100,3) + array([.5,.5,.5]),rand(100,3)))
```


```python
data[0:9,:]
```




    array([[0.99817377, 0.62240622, 1.20520728],
           [0.93023766, 0.80861419, 0.55528294],
           [0.93007972, 1.2739864 , 0.65128115],
           [0.79749481, 0.82223636, 0.59215515],
           [0.66918786, 0.59201969, 1.07613652],
           [0.95532718, 1.34413154, 0.98160813],
           [0.59669358, 1.48783283, 0.82456277],
           [1.09682474, 0.61015007, 1.24707066],
           [0.91914752, 0.52499387, 1.39879969]])



Normalize a group of observations on a per feature basis. Before running K-Means, it is beneficial to rescale each feature dimension of the observation set with whitening. Each feature is divided by its standard deviation across all observations to give it unit variance.

#### Whiten the data
We have to use the following code to whiten the data.


```python
# whitening of data
data = whiten(data)
```

#### Compute K-Means with Three Clusters
Let us now compute K-Means with three clusters using the following code.


```python
# computing K-Means with K = 3 (2 clusters)
centroids,_ = kmeans(data,3)
```

The above code performs K-Means on a set of observation vectors forming K clusters. 
The K-Means algorithm adjusts the centroids until sufficient progress cannot be made, i.e. the change
in distortion, since the last iteration is less than some threshold. Here, we can observe the centroid
of the cluster by printing the centroids variable using the code given below.



```python
print(centroids)
```

    [[2.34450222 2.00851363 2.07310195]
     [1.07266054 1.30959075 1.16225373]
     [2.7707074  3.19460819 2.93174533]]


Assign each value to a cluster by using the code given below.


```python
# assign each sample to a cluster
clx,_ = vq(data,centroids)
```

The vq function compares each observation vector in the ‘M’ by ‘N’ obs array with the centroids and assigns the observation to the closest cluster. It returns the cluster of each observation and the distortion. We can check the distortion as well. Let us check the cluster of each observation using the following code.





```python
# check clusters of observation
print(clx)
```

    [2 2 0 2 0 0 0 0 2 0 2 0 2 0 2 0 2 0 0 0 2 2 2 2 2 2 0 0 2 2 2 0 2 2 2 2 2
     2 2 2 2 0 2 0 2 0 0 2 2 0 2 2 2 2 2 0 2 2 2 2 0 0 0 2 0 2 2 0 0 0 2 0 0 2
     0 2 0 2 2 2 2 0 0 0 0 0 2 0 0 2 2 2 0 0 2 0 0 2 2 2 0 1 0 1 1 0 1 1 1 1 1
     1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 0 1 1 0 1 1 1 1 0 1 1 1 1 1 1 1 1 1
     0 1 1 1 1 0 1 1 1 1 1 0 1 1 1 1 0 1 1 0 1 1 0 1 1 1 1 1 0 1 1 1 0 1 1 1 0
     0 1 1 1 0 1 1 1 1 1 0 0 1 0 1]



The distinct values 0, 1, 2 of the above array indicate the clusters.
