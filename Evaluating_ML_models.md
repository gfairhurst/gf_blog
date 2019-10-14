# Evaluating ML models
information from this summary was taken from Alice Zheng book **"Evaluating machine learning models"** 


## Classification Metrics

Classification is about predicting class labels given input data. In binary classification, there are two possible output classes. In multi‐
class classification, there are more than two possible classes.

### Accuracy
Accuracy simply measures how often the classifier makes the correct prediction. It’s the ratio between the number of correct predictions
and the total number of predictions (the number of data points in the test set)

accuracy $=\frac{\# \text { correct predictions }}{\# \text { total data points }}$

\text { accuracy }=\frac{\# \text { correct predictions }}{\# \text { total data points }}


### Confusion Matrix
Accuracy looks easy enough. However, it makes no distinction between classes; correct answers for class 0 and class 1 are treated equally. One might want to look at how many examples failed for class 0 versus class 1, because the cost of misclassification might differ for the two classes, or one might have a lot more test data of one class than the other. For example, when a doctor makes a medical diagnosis that a patient has cancer when he doesn’t (known as a false positive) has very different consequences than making the call that a patient doesn’t have cancer when he does (a false negative).  
  
A confusion matrix (or confusion table) shows a more detailed breakdown of correct and incorrect classifications for each class. The rows of the matrix correspond to ground truth labels, and the columns represent the prediction. Suppose the test dataset contains 100 examples in the positive class and 200 examples in the negative class; then, the confusion table might look something like this:

## Regression Metrics
