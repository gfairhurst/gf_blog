back to [main page](main.md)

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

## Logistic Regression vs Linear Regression
The linear regression model can work well for regression, but fails for classification. Why is that? 
- A linear model does not output probabilities, but it treats the classes as numbers (0 and 1) and fits the best hyperplane (for a single feature, it is a line) that minimizes the distances between the points and the hyperplane. So it simply interpolates between the points, and you cannot interpret it as probabilities.
- A linear model also extrapolates and gives you values below zero and above one. This is a good sign that there might be a smarter approach to classification.
- Since the predicted outcome is not a probability, but a linear interpolation between points, there is no meaningful threshold at which you can distinguish one class from the other.

## Logistic function 
A solution for classification is logistic regression. Instead of fitting a straight line or hyperplane, the logistic regression model uses the logistic function to squeeze the output of a linear equation between 0 and 1. The logistic function is a sigmoid function, which takes any real input t, and outputs a value between zero and one. Applying the sigmoid function to the linear regression, solves most of the problems mentioned above.  

The standard logistic function is defined as follows:

![](images/logit_sigmoid_func.png?raw=true)

![](images/logit_sigmoid_graph.png?raw=true)

Let us assume that *__t__* is a linear function of a single explanatory variable *__x__* (the case where t is a linear combination of multiple explanatory variables is treated similarly), then:

![](images/logit_linear_regression_1.png?raw=true)

In the logistic model, **p(x)** is interpreted as the probability of the dependent variable _**Y**_ equaling a success/case. The same can be written in a matrix form:

![](images/logit_sigmoid_matrix.png?raw=true)


## The Training Process

1) Initialize Parameters
2) Calculate y_hat for all observations
3) Calculate the total error (Cost), which is the sum of the differences between the estimated y_hat and the real label (y).
4) Change Paramenters to reduce cost
5) Go to step 2, until Cost is minimized.

notes:
- The most common way to optimize the parameters is done via minimize the Loss function using Gradient Descent.
- The iterative process can be stopped once there is no significant improvement in reducing the Cost.
- Cost and Loss function (J):

![](images/logit_loss_func.png?raw=true)
![](images/logit_optimization.png?raw=true)

## Interpretation

The interpretation of the weights in logistic regression differs from the interpretation of the weights in linear regression, since the outcome in logistic regression is a probability between 0 and 1. The weights do not influence the probability linearly any longer. The weighted sum is transformed by the logistic function to a probability. Therefore we need to reformulate the equation for the interpretation so that only the linear term is on the right side of the formula.

![](images/logit_log_odds.png?raw=true)

We call the term in the log() function **“odds”** (probability of event divided by probability of no event) and wrapped in the logarithm it is called **log odds**.

This formula shows that the logistic regression model is a linear model for the log odds. Great! That does not sound helpful! With a little shuffling of the terms, you can figure out how the prediction changes when one of the features Xj is changed by 1 unit. To do this, we can first apply the exp() function to both sides of the equation:

![](images/logit_odds.png?raw=true)

In the end, we have something as simple as exp() of a feature weight. A change in a feature by one unit changes the odds ratio (multiplicative) by a factor of exp(βj). We could also interpret it this way: A change in  
Xj by one unit increases the log odds ratio by the value of the corresponding weight

![](images/logit_charts.png?raw=true)

## Sources
- [Machine learning with Python Course @ Coursera](https://www.coursera.org/learn/machine-learning-with-python)
- [Wikipedia](https://en.wikipedia.org/wiki/Logistic_regression)
- [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/logistic.html)