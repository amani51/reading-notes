# Class-10
## Linear Regressions
### Reading
##### Linear regression is used to model the relationship between two variables and estimate the value of a response by using a line-of-best fit. This calculator is built for simple linear regression, where only one predictor variable (X) and one response (Y) are used.
![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Linear_regression.svg/400px-Linear_regression.svg.png)
#### How to run Linear regression in Python scikit-Learn
![](https://sp-ao.shortpixel.ai/client/to_auto,q_glossy,ret_img,w_1024,h_427/https://pianalytix.com/wp-content/uploads/2020/11/Scikit-Learn-1024x427.jpg)
- **Scikit-learn** is a powerful Python module for machine learning. It contains function for regression, classification, clustering, model selection and dimensionality reduction. 
- Important functions to keep in mind while fitting a linear regression model are:
    - **lm.fit()** : fits a linear model
    - **lm.predict()** : Predict Y using the linear model with estimated coefficients
    - **lm.score()** : Returns the coefficient of determination (R^2). A measure of how well-observed outcomes are replicated by the model, as the proportion of total variation of outcomes explained by the model.
- In practice you wont implement linear regression on the entire data set, you will have to split the data sets into training and test data sets. So that you train your model on training data and see how well it performed on test data.
- **train_test_split** divides data sets randomly.
- **Residual plots** are a good way to visualize the errors in your data. If you have done a good job then your data should be randomly scattered around line zero. If you see structure in your data, that means your model is not capturing something. May there is an interaction between 2 variables that you are not considering, or maybe you are measuring time-dependent data. If you get some structure in your data, you should go back to your model and check whether you are doing a good job with your parameters.
#### Linear Regression in Python
- Regression searches for relationships among **variables**.
- find a **function that maps some features or variables to others** sufficiently well.

- he dependent features are called the **dependent variables, outputs, or responses**. The independent features are called the **independent variables, inputs, regressors, or predictors**.
- **When Do You Need Regression?**
    - Typically, you need regression to answer whether and how some phenomenon influences the other or how several variables are related.
    - when you want to **forecast** a response using a new set of predictors.
- **The coefficient of determination**, denoted as **𝑅²**, tells you which amount of variation in 𝑦 can be explained by the dependence on 𝐱, using the particular regression model. A **larger** 𝑅² indicates a **better fit** and means that the **model can better explain** the variation of the output with different inputs.

- The value **𝑅² = 1** corresponds to **SSR = 0**. That’s the **perfect fit**, since the values of predicted and actual responses fit completely to each other.
- **Simple or single-variate linear regression** is the simplest case of linear regression, as it has a single independent variable, 𝐱 = 𝑥
![](https://files.realpython.com/media/fig-lin-reg.a506035b654a.png)
- **Multiple or multivariate linear regression** is a case of linear regression with two or more independent variables.
![](https://miro.medium.com/max/541/1*Pc8EZljAb4X5IGyLd_Jvdw.png)
- **Polynomial Regression** is a form of Linear regression known as a special case of Multiple linear regression which estimates the relationship as an nth degree polynomial.
![](https://www.w3schools.com/python/img_polynomial_regression.png)
- **Underfitting and Overfitting**
    - **Underfitting** occurs when a model can’t accurately capture the dependencies among data, usually as a consequence of its own simplicity. 
    - **Overfitting** happens when a model learns both data dependencies and random fluctuations. In other words, a model learns the existing data too well. Complex models, which have many features or terms, are often prone to overfitting.
![](https://files.realpython.com/media/poly-reg.5790f47603d8.png)
- **Python Packages for Linear Regression**
    - **NumPy** is a fundamental Python scientific package that allows many high-performance operations on single-dimensional and multidimensional arrays.
    -  **scikit-learn** is a widely used Python library for machine learning, built on top of NumPy and some other packages. 

- Five basic steps when you’re implementing linear regression:
    1. Import the packages and classes that you need.
    2. Provide data to work with, and eventually do appropriate transformations.
    3. Create a regression model and fit it with existing data.
    4. Check the results of model fitting to know whether the model is satisfactory.
    5. Apply the model for predictions.