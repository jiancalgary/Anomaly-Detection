# **Anomaly Detection**
In this post, I summarized multiple anomaly detection methods using human genreated simulation data in Python, including the folowing contents:

* What are Outliers ?
* Statistical Methods for Univariate Data
* Using Gaussian Mixture Models
* Fitting an elliptic envelope
* Isolation Forest
* Local Outlier Factor
* Using clustering method like DBSCAN

### 1. Outliers
* New data which doesn't belong to general trend (or distribution) of entire data are known as outliers.
* Data belonging to general trend are known as inliners.
* Learning models are impacted by presence of outliers.
* Anomaly detection is another use of outlier detection in which we find out unusual behaviour.
* Data which were detected outliers can be deleted from complete dataset.
* Outliers can also be marked before using them in learning methods

### 2. Statistical Methods for Univariate Data
* Using Standard Deviation Method - zscore
* Using Interquartile Range Method - IRQ

### 3. Using Gaussian Mixture Models
* Data might contain more than one peaks in the distribution of data.
* Trying to fit such multi-model data with unimodel won't give a good fit.
* GMM allows to fit such multi-model data.
* Configuration involves number of components in data, n_components.
* covariance_type controls the shape of cluster
  - full : cluster will be modeled to eclipse in arbitrary dir
  - sperical : cluster will be spherical like kmeans
  - diag : cluster will be aligned to axis
* We will see how GMM can be used to find outliers

### 4. Fitting Elliptical Envelope
* The assumption here is, regular data comes from known distribution ( Gaussion distribution )
* Inliner location & variance will be calculated using `Mahalanobis distances` which is less impacted by outliers.
* Calculate robust covariance fit of the data.

### 5. Isolation Forest
* Based on RandomForest
* Useful in detecting outliers in high dimension datasets.
* This algorithm randomly selects a feature & splits further.
* Random partitioning produces shorter part for anomolies.
* When a forest of random trees collectively produce shorter path lengths for particular samples, they are highly likely to be anomalies.

### 6. Local Outlier Factor
* Based on nearest neighbours
* Suited for moderately high dimension datasets
* LOF computes a score reflecting degree of abnormility of a data.
* LOF Calculation
  - Local density is calculated from k-nearest neighbors.
  - LOF of each data is equal to the ratio of the average local density of his k-nearest neighbors, and its own local density.
  - An abnormal data is expected to have smaller local density.
* LOF tells you not only how outlier the data is but how outlier is it with respect to all data
