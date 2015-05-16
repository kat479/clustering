# Clustering

This is the notes from 'Cluster Analysis in Data Mining'

###Calculation of dissimlarity Matrix

One can calculate the dissimilarity matrix using [daisy](https://stat.ethz.ch/R-manual/R-devel/library/cluster/html/daisy.html)
from the `cluster` package in R

###DBSCAN - A Density based Clustering Algorithm 
(excerpts from a [paper](http://www.academia.edu/8142139/Density_Based_Clustering_with_DBSCAN_and_OPTICS_-_Literature_Review))

Clustering with density-based algorithms identifies regions in which objects (also referred to as points) are close to one another. This closeness is understood in terms of proximity (dissimilarity) measure best suited for a given set of attributes. In that respect, the variations of density in a data set are being estimated based on the number of points in a neighbourhood of every single object belonging to that data set.

**Definition:** ɛ-neighboorhood

Let p and q be two arbitrary points within a dataset. Let ɛ be an arbitrary radius, and Nɛ(p) be the ɛ-neighbourhood of a point p. A point q belongs to the _ɛ - neighbourhood_ of a point p if the distance between these two is not greater than ɛ.

**Definition:** MinPts, core and border points

Depending on the number of objects within a given radius, the ɛ-neighbourhood of any point can be of high or low density. If high density constitutes a _cluster_ and low density represents _noise_, a threshold value needs to be identified to distinguish between these two. This is specified by MinPts parameter, which defines the lowest number of points in ɛ-radius region required to form a cluster. However, every cluster contains two types of objects: _core points_ (inside points) and _border points_.
 
Core points will always have at least MinPts in their ɛ-neighbourhood. Border points, on the other hand, are located at the edge of a dense region and will have significantly less points around them.

If a point was assessed on MinPts measure exclusively, any border point would be discarded from a cluster as, sensu stricto, its ɛ-neighbourhood is not sufficiently dense. To avoid that misclassification, density-based clustering supports different measures of reachability between points in a database. Roughly speaking, even though a border point is in a region considered to be of low density, it can still belong to a cluster if it is close enough to another point located in an adequately dense region. The notions of reachability as introduced by Ester et al (1996) are presented below.

**Definition:** direct density-reachable point, density-reachable point, density-connected point

A point q is _directly density-reachable_ from a point p if q belongs to the ɛ-neighboorhood of p and p is a core point. As illustrated in Figure1, the border point q (3 points in its ɛ-neighboorhood) is directly density-reachable from a core point p (4 points in its ɛ-neighboorhood). This relation would be symmetric, if both were core points.

![Figure 1](https://html2-f.scribdassets.com/8xst4md13440hztk/images/3-36c5d92acc.png)

![Figure 2](http://lh5.ggpht.com/-ejlneHmhNZA/VSTQHRZTwqI/AAAAAAAAG1s/fkLp8Y5xnjY/s1600-h/image%25255B15%25255D.png)
