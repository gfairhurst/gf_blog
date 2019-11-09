back to [main page](main.md)

# K-Means

![](images/K-means_header.jpg?raw=true)

## Intro to K-Means Clustering

K-Means is a type of *partitioning clustering*, that is, it divides the data into **K** *non-overlapping subsets* or clusters without any cluster internal structure or labels. This means, it's an *unsupervised* algorithm. Objects within a cluster are very similar, and objects across different clusters are very different or dissimilar.

Though the objective of K-Means is to form clusters in such a way that similar samples go into a cluster, and dissimilar samples fall into different clusters, it can be shown that instead of a similarity metric, we can use dissimilarity metrics. In other words, conventionally the distance of samples from each other is used to shape the clusters. So we can say K-Means tries to minimize the *intra-cluster* distances and maximize the *inter-cluster* distances. 

### K-Means objectives:
- To form clusters in such a way that similar samples go into a cluster, and dissimilar samples fall into different clusters.
- To minimize the “intra cluster” distances and maximize the “inter-cluster” distances.
- To divide the data into non-overlapping clusters without any cluster-internal structure


Now, the question is, how can we calculate the dissimilarity or distance of two cases such as two customers?

![](images/K-means_distance.png?raw=true)

**Note:** We have to *normalize* our feature set to get the accurate dissimilarity measure.  

There are other dissimilarity measures as well that can be used for this purpose, but it is highly dependent on datatype and also the domain that clustering is done for it. For example you may use **Euclidean distance, Cosine similarity, Average distance**, and so on. Indeed, the similarity measure highly controls how the clusters are formed, so it is recommended to understand the domain knowledge of your dataset and datatype of features and then choose the meaningful distance measurement. 

### How K-Means clustering works. 

![](images/K-means_algo.png?raw=true)

Let's assume that our dataset is a two-dimensional space. We can show the distribution of customers using a scatter plot: the Y-axis indicates age and the X-axis shows income of customers. 

![](images/K-means_scatter.png?raw=true)

We try to cluster the customer dataset into distinct groups or clusters based on these two dimensions. 
- **First step:** we should determine the number of clusters (K). Let's put K = 3. Then we randomly select three data points are called **centroids** shown in the plot with red color. 

![](images/K-means_step1.png?raw=true)

- **Second step:** we must assign each customer to the closest center. For this purpose, we have to calculate the distance of each data point or in our case each customer from the centroid points. As mentioned before, depending on the nature of the data and the purpose for which clustering is being used different measures of distance may be used to place items into clusters. Therefore, you will form a matrix where each row represents the distance of a customer from each centroid. It is called the *Distance Matrix.*

![](images/K-means_step2.png?raw=true)

- **Third step:** We use the distance matrix to find the nearest centroid to datapoints, and we assign each data point to that cluster. 
 We can easily say that it does not result in good clusters because the centroids were chosen randomly from the first. Indeed, the model would have a high error. The error is the total distance of each point from its centroid. It can be shown as within-cluster sum of squares error.

![](images/K-means_step3.png?raw=true)

- **Fourth step:** Intuitively, we try to reduce this error. It means we should shape clusters in such a way that the total distance of all members of a cluster from its centroid be minimized. Now, the question is, how can we turn it into better clusters with less error? Okay, we move centroids. In this step, each cluster center will be updated to be the mean for datapoints in its cluster. Indeed, each centroid moves according to their cluster members. In other words the centroid of each of the three clusters becomes the new mean.  
  
![](images/K-means_step4.png?raw=true) 

- **Fifth step:** K-Means is an iterative algorithm and we have to repeat steps two to four until the algorithm converges. In each iteration, it will move the centroids, calculate the distances from new centroids and assign data points to the nearest centroid. It results in the clusters with minimum error or the most dense clusters. However, as it is a heuristic algorithm, there is no guarantee that it will converge to the global optimum and the result may depend on the initial clusters. It means, this algorithm is guaranteed to converge to a result but the result may be a local optimum. To solve this problem, it is common to run the whole process multiple times with different starting conditions. This means with randomized starting centroids, it may give a better outcome. As the algorithm is usually very fast, it wouldn't be any problem to run it multiple times.

![](images/K-means_step5.png?raw=true) 

### K-Means Accuracy

Accuracy is a measure of comparing the true label to the predicted label. K-Means is an unsupervised clustering algorithm where a predicted label does not exist. So, accuracy can not be directly applied to K-Means clustering evaluation. However, there are two examples of metrics that you could use to evaluate your clusters.

- **Within Cluster Sum of Squares (WCSS)**, which measures the squared average distance of all the points within a cluster to the center of the cluster (known as the cluster centroid). This measurement can indicate the variability of the points within the cluster in terms of the average distance to the cluster center. A large sum of squares could indicate a very large a spread out cluster. A small sum of squares could indicate a small, compact cluster with little variation in the attributes of the points. This measurement is sometimes called *Cohesion* because it measures similarity between the data points in that cluster.
- **Between Clusters Sum of Squares (BCSS)**, which measures the squared average distance between all cluster centroids. This measurement can indicates the variation between all clusters. A large number can indicate clusters that are spread out. A small number can indicate clusters that are close to each other. This measurement is sometimes called *separation* because it measures the separation of the clusters.
- **Silhouette Coefficient**, combines both the *Cohesion* and *Separation*. The silhouette value is a measure of how similar an object is to its own cluster (cohesion) compared to other clusters (separation). The silhouette ranges from −1 to +1, where a high value indicates that the object is well matched to its own cluster and poorly matched to neighboring clusters. If most objects have a high value, then the clustering configuration is appropriate. If many points have a low or negative value, then the clustering configuration may have too many or too few clusters.

The silhouette can be calculated with any distance metric, such as the Euclidean distance or the Manhattan distance.

### How to choose the correct K value:
If we plot the wcss value against the number of clusters that we tried to get that wcss value, normally we end up getting a graph similar to below,

![](images/elbow.png?raw=true) 

## Sources
- [Machine learning with Python Course @ Coursera](https://www.coursera.org/learn/machine-learning-with-python)
- [Wikipedia](https://en.wikipedia.org/wiki/Silhouette_(clustering))
- [K-Means Accuracy](https://datascience.stackexchange.com/questions/41317/accuracy-for-kmeans-clustering)
- [Khan Academy](https://www.khanacademy.org/math/statistics-probability/analysis-of-variance-anova-library/analysis-of-variance-anova/v/anova-2-calculating-ssw-and-ssb-total-sum-of-squares-within-and-between-avi)