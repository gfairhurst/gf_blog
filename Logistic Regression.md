back to main page

# Logistic Regression

## Intro to Logistic Regression

Logistic regression is a statistical and machine learning technique for <u>**classifying**</u> records of a dataset based on the values of the input fields. Despite its name, is a linear model for classification rather than regression. Logistic regression is also known in the literature as *logit regression*, *maximum-entropy classification (MaxEnt)* or the *log-linear classifier*. 
- Can be used for both binary classification and multi-class classification.
- Can not only predict the class of each case, we also measure the probability of a case belonging to a specific class.
- It is analogous to linear regression, but tries to predict a categorical or discrete target field instead of a numeric one. In linear regression, we might try to predict a continuous value of variables such as the price of a house, or fuel consumption of a car, etc. But in logistic regression, we predict a variable which is binary such as yes/no, true/false, successful or not successful, and so on, all of which can be coded as zero or one.
- In logistic regression dependent variables should be Numerical. If categorical, they should be dummy or indicator coded. 


## When should we use logistic regression? 
Here are four situations in which logistic regression is a good candidate: 
1) When the target field in your data is categorical or specifically is binary. 
2) You need the probability of your prediction. Logistic regression returns a probability score between zero and one. 
3) If your data is linearly separable. The decision boundary of logistic regression is a line or a plane or a hyper plane. A classifier will classify all the points on one side of the decision boundary as belonging to one class, and all those on the other side as belonging to the other class. (Please note that in using logistic regression, we can also achieve a complex decision boundary using polynomial processing as well)
4) You need to understand the impact of a feature. After finding the optimum parameters, a feature X with the weight Theta one close to zero has a smaller effect on the prediction than features with large absolute values of Theta one. Indeed, it allows us to understand the impact an independent variable has on the dependent variable while controlling other independent variables. 

## Logistic function 
An explanation of logistic regression can begin with an explanation of the standard logistic function. The logistic function is a sigmoid function, which takes any real input t, and outputs a value between zero and one. The standard logistic function is defined as follows:

![](images/logit_sigmoid_func.png?raw=true)

![](images/logit_sigmoid_graph.png?raw=true)

Let us assume that *__t__* is a linear function of a single explanatory variable *__x__* (the case where t is a linear combination of multiple explanatory variables is treated similarly), then:

![](images/logit_linear_regression_1.png?raw=true)

In the logistic model, **p(x)** is interpreted as the probability of the dependent variable _**Y**_ equaling a success/case. The same can be written in a matrix form:

![](images/logit_sigmoid_matrix.png?raw=true)

## Logistic Regression vs Linear Regression


The *sigmoid function*, also called the *logistic function*, 

## Sources
- ["Machine learning with Python" Course @ Coursera](https://www.coursera.org/learn/machine-learning-with-python)
- [Wikipedia](https://en.wikipedia.org/wiki/Logistic_regression)