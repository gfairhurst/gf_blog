back to [main page](main.md)

# Regression
![](images/linear_regression_header.jpg?raw=true)

## Intro to Regression

Regression is the process of predicting a continuous value. In regression, there are two types of variables, a **dependent variable (or target)**, and one or more **independent variables (predictors)**. The dependent variable, can be seen as the target we try to predict, and the independent variables, also known as *explanatory variables*, can be seen as the causes of those states. The independent variables are shown conventionally by **X**, and the dependent variable is notated by **y**.  

![](images/linear_regression_xy.png?raw=true)

Our regression model relates Y (the dependent variable) to a function of X (the independent variables). The key point in the regression, is that our dependent value should be continuous, and cannot be a discrete value. However, the independent variable or variables, can be measured on either a categorical, or continuous measurement scale.  

## Types of Regression models

- Simple Regression
  - Simple Linear Regression
  - Simple Non-linear Regression
- Multiple Regression
  - Multiple Linear Regression
  - Multiple Non-linear Regression

## Regression Algorithms

- Linear, Polynomial, Lasso, Stepwise, Risge & Elastic Net regression
- Ordinal regression
- Poisson regression
- Fast Forest Quantile regression
- Bayesian linear regression
- Neural Network regression
- Decision forest tree regression
- KNN (K-nearest neighbors)

## Simple Linear Regression

Simple Linear Regression establishes a relationship between dependent variable (Y) *one* independent variable (X) using a best fit straight line (also known as regression line). It is represented by an equation **Y = a + b \* X**, where a is **intercept**, b is **slope** of the line. This equation can be used to predict the value of target variable based on given predictor variable.

![](images/regression_simple_linear.png?raw=true)