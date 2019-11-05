back to [main page](main.md)

# Support Vector Machine (SVM)

## Intro to SVM
Support Vector Machine, abbreviated as SVM can be used for both regression and classification tasks. But, it is widely used in classification objectives. 

The objective of the support vector machine algorithm is to find a hyperplane in an N-dimensional space(N — the number of features) that distinctly classifies the data points. To separate the two classes of data points, there are many possible hyperplanes that could be chosen. Our objective is to find a plane that has the maximum margin, i.e the maximum distance between data points of both classes. Maximizing the margin distance provides some reinforcement so that future data points can be classified with more confidence.

![](images/svm_hyperplanes.png?raw=true)

Hyperplanes are decision boundaries that help classify the data points. Data points falling on either side of the hyperplane can be attributed to different classes. Also, the dimension of the hyperplane depends upon the number of features. If the number of input features is 2, then the hyperplane is just a line. If the number of input features is 3, then the hyperplane becomes a two-dimensional plane. It becomes difficult to imagine when the number of features exceeds 3.

![](images/svm_support_vectors.png?raw=true)

Support vectors are data points that are closer to the hyperplane and influence the position and orientation of the hyperplane. Using these support vectors, we maximize the margin of the classifier. Deleting the support vectors will change the position of the hyperplane. These are the points that help us build our SVM.

In addition to performing linear classification, SVMs can efficiently perform a non-linear classification using what is called the **kernel trick**, implicitly mapping their inputs into high-dimensional feature spaces (i.e. transforming the space as to be able to separate the classes using linear hyperplanes)

![](images/svm_kerneling.png?raw=true)


## Pros and Cons of SVM

- Advantages
  - Accurate in high-dimensional spaces
  - Memory efficient
- Disadvantages
  - Prone to over-fitting
  - No probability estimation
  - dowsn't work well for small datasets.

## SVM Applications

SVM works well for:
- Image recognitaion (hand written digit recognition)
- Text mining tasks (detecting spam, text category assignment and sentiment analysis)
- Gene expression data classification


## Sources
- [Machine learning with Python Course @ Coursera](https://www.coursera.org/learn/machine-learning-with-python)
- [Wikipedia](https://en.wikipedia.org/wiki/Support-vector_machine)
- [Towards Datascience](https://towardsdatascience.com/support-vector-machine-introduction-to-machine-learning-algorithms-934a444fca47)