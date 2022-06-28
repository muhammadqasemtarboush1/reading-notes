# Class 13
## Linear Regression in Python

### What is Linear Regression
Linear regression is probably one of the most important and widely used regression techniques. It’s among the
simplest regression methods. One of its main advantages is the ease of interpreting results.

### Problem Formulation
Linear regression calculates the estimators of the regression coefficients or simply the predicted weights,
denoted with 𝑏₀, 𝑏₁, …, 𝑏ᵣ. These estimators define the estimated regression function 𝑓(𝐱) = 𝑏₀ + 𝑏₁𝑥₁ + ⋯ + 𝑏ᵣ𝑥ᵣ.
This function should capture the dependencies between the inputs and output sufficiently well.

### Regression Performance
The coefficient of determination, denoted as 𝑅², tells you which amount of variation in 𝑦 can be explained by the 
dependence on 𝐱, using the particular regression model. A larger 𝑅² indicates a better fit and means that the model 
can better explain the variation of the output with different inputs.

### Underfitting and Overfitting
* Underfitting occurs when a model can’t accurately capture the dependencies among data, usually as a consequence 
of its own simplicity. It often yields a low 𝑅² with known data and bad generalization capabilities when applied 
with new data.

* Overfitting happens when a model learns both data dependencies and random fluctuations. In other words, a model
learns the existing data too well. Complex models, which have many features or terms, are often prone to overfitting.
When applied to known data, such models usually yield high 𝑅².

### Python Packages for Linear Regression
* NumPy is a fundamental Python scientific package that allows many high-performance operations on single-dimensional 
and multidimensional arrays. It also offers many mathematical routines. Of course, it’s open-source.
* scikit-learn is a widely used Python library for machine learning, built on top of NumPy and some other packages.
It provides the means for preprocessing data, reducing dimensionality, implementing regression, classifying, 
clustering, and more. Like NumPy, scikit-learn is also open-source.

### Simple Linear Regression With scikit-learn
There are five basic steps when you’re implementing linear regression:
1. Import the packages and classes that you need.
2. Provide data to work with, and eventually do appropriate transformations.
3. Create a regression model and fit it with existing data.
4. Check the results of model fitting to know whether the model is satisfactory.
5. Apply the model for predictions.

### Multiple Linear Regression With scikit-learn
You can implement multiple linear regression following the same steps as you would for simple regression.
The main difference is that your x array will now have two or more columns.

### Polynomial Regression With scikit-learn
Implementing polynomial regression with scikit-learn is very similar to linear regression. There’s only one extra
step: you need to transform the array of inputs to include nonlinear terms such as 𝑥².

### Beyond Linear Regression
Linear regression is sometimes not appropriate, especially for nonlinear models of high complexity.

Fortunately, there are other regression techniques suitable for the cases where linear regression doesn’t work well.
Some of them are support vector machines, decision trees, random forest, and neural networks.



### Summary:
You now know what linear regression is and how you can implement it with Python and three open-source packages: 
NumPy, scikit-learn, and statsmodels. You use NumPy for handling arrays. Linear regression is implemented 
with the following:
 * scikit-learn if you don’t need detailed results and want to use the approach consistent with other
regression techniques
 * statsmodels if you need the advanced statistical parameters of a model
Both approaches are worth learning how to use and exploring further. The links in this article can be very useful 
for that.

--- 
## [Source](https://realpython.com/linear-regression-in-python/)
--- 
## How to run Linear regression in Python scikit-Learn

* Scikit-learn :is a powerful Python module for machine learning. It contains function for regression, 
classification, clustering, model selection and dimensionality reduction. 

### Exploring Boston Housing Data Set
Y = boston housing price(also called “target” data in Python)

X = all the other features (or independent variables)
![I am going to store linear regression object in a variable called lm.](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Skitlearn-linear-model1.png)
If you want to look inside the linear regression object, you can do so by typing LinearRegression. and the press <tab> key. This will give a list of functions available inside linear regression object.
![look](https://bigdata-madesimple.com/wp-content/uploads/2016/04/linear-regression.png)
Important functions to keep in mind while fitting a linear regression model are:

lm.fit() -> fits a linear model

lm.predict() -> Predict Y using the linear model with estimated coefficients

lm.score() -> Returns the coefficient of determination (R^2). A measure of how well observed outcomes are
replicated by the model, as the proportion of total variation of outcomes explained by the model.

You can also explore the functions inside lm object by pressing lm.<tab>

### Residual Plots
Residual plots are a good way to visualize the errors in your data. If you have done a good job then your data 
should be randomly scattered around line zero. If you see structure in your data, that means your model is not
capturing some thing. Maye be there is a interaction between 2 variables that you are not considering, or may be 
you are measuring time dependent data. If you get some structure in your data, you should go back to your model and
check whether you are doing a good job with your parameters.

## Conclusion
To recap what I have done till now,

* I explored the boston data set and then renamed its column names.
* I explored the boston data set using .DESCR, my goal was to predict the housing prices using the given features.
* I used Scikit learn to fit linear regression to the entire data set and calculated the mean squared error.
* I made a train-test split and calculated the mean squared error for my training data and test data.
* I then plotted the residuals for my training and test datasets.


### [Source](https://www.crayondata.com/how-to-run-linear-regression-in-python-scikit-learn/)
---


