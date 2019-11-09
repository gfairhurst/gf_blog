back to [main page](main.md)

# Clustering
![](images/k-means_header.jpg?raw=true)

## Intro to Clustering
 
**Classification algorithms** predict categorical classed labels. This means assigning instances to predefined classes. For example, if an analyst wants to analyze customer data in order to know which customers might default on their payments, she uses a labeled dataset as training data and uses classification approaches such as a decision tree, Support Vector Machines or SVM, or logistic regression, to predict the default value for a new or unknown customer. Generally speaking, classification is a *supervised* learning where each training data instance belongs to a particular class. 

**Clustering algorithms** however, the data is unlabeled and the process is unsupervised. For example, we can use a clustering algorithm such as k-means to group similar customers and assign them to a cluster, based on whether they share similar attributes, such as; age, education, and so on. 

A cluster is a group of data points or objects in a dataset that are similar to other objects in the group, and dissimilar to datapoints in other clusters.

### Clustering Uses:
- Exploratory data analysis
- Summary generation
- Outlier detection
- Finding duplicates

### Industry examples for Clustering
1) In the retail industry, clustering is used to find associations among customers based on their demographic characteristics and use that information to identify buying patterns of various customer groups. 
2) Also, it can be used in recommendation systems to find a group of similar items or similar users and use it for collaborative filtering, to recommend things like books or movies to customers.
3) In banking, analysts find clusters of normal transactions to find the patterns of fraudulent credit card usage. Also they use clustering to identify clusters of customers. For instance, to find loyal customers versus churned customers.
4) In the insurance industry, clustering is used for fraud detection in claims analysis, or to evaluate the insurance risk of certain customers based on their segments.
5) In publication media, clustering is used to auto categorize news based on his content or to tag news, then cluster it so as to recommend similar news articles to readers.
6) In medicine, it can be used to characterize patient behavior, based on their similar characteristics. So as to identify successful medical therapies for different illnesses or in biology, clustering is used to group genes with similar expression patterns or to cluster genetic markers to identify family ties. 

### Some Clustering algorithms and their characteristics:
- **Partitioned-based clustering** is a group of clustering algorithms that produces fear like clusters. These algorithms are *relatively efficient* and are used for *medium and large sized* datasets. 
  - [K-Means](K-Means.md), 
  - K-Medians or 
  - Fuzzy c-Means.  
- **Hierarchical clustering** algorithms produce trees of clusters, such as agglomerative and divisive algorithms. This group of algorithms are *very intuitive* and are generally good for use with *small size* datasets.
- **Density-based clustering** algorithms produce arbitrary shaped clusters. They are especially good when dealing with spatial clusters or when there is noise in your data set. For example, the DB scan algorithm.

## Sources
- [Machine learning with Python Course @ Coursera](https://www.coursera.org/learn/machine-learning-with-python)