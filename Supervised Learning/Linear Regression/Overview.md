# What is Linear Regression?

Linear Regression is one of the *most* fundamental machine learning algorithms. It is used to predict the value of a variable based on the value of another variable(s). The goal of Linear Regression is to update (or learn) the coefficients of the linear equation (in its most basic algebraic form, y = mx + b) so that it minimizes the error in the predictions it makes [1].

Some examples of what it can be used for are to determine the strength of the relationship between variables, or, when given a certain value of the independent variable(s), the value of the dependent variable (or in other words, a prediction) [2].

## Why is it Important?

Linear regression is important because it is simple yet powerful. It provides a clear understanding of the relationship between variables and is the foundation for more complex algorithms. It is widely used in various fields such as economics, biology, and engineering to make predictions and infer relationships [3].

## Key Terms:
- **Dependent Variable**: The variable you want to predict. Often represented as `y`.
- **Independent Variable**: The variable(s) you are using to predict the dependent variable. Often represented as `X`.
- **Bias Term**: Also known as the intercept, it is the value of Y when all independent variables are zero.

## How it works:

The the most simple form of linear regression we can use this slope-intercept formula.

            y = w0 + w1 * X

* `y`: This is the predicted value (dependent variable) for any X
* `w0`: This is the intercept, the value of y when X is zero (also commonly known as b in the standard slope-intercept formula).
* `w1`: This is the slope, the expected change to y as X increases (also commonly known as m in the standard slope-intercept formula).
* `X`: This is the value that influences y (independent variable). [2]

The equation can continue for n values of X and w leaving us with the equation...

            y = w0 + w1 * X1 + w2 * X2 + ... + wn * Xn

With each additional pair of w and X_i, the model becomes more complex and can capture more intricate relationships

## When Should it be Used?

To determine if your dataset is suitable for linear regression, ask yourself these questions:
* Are the variables measured at a continuous level (such as time or temperature)?
* Does it look like there is a linear relationship between the two variables if you plot them?
* Is the data independent of each other?
* Are there no significant outliers? (Note: methods can be employed to remove or deal with outliers)
* Is there homoscedasticity — a statistical concept where the variances along the best-fit line remain similar throughout?
* Do the errors follow a normal distribution?
If you answered yes to all of these questions, it is likely that applying linear regression to your dataset may be fruitful.
 

## Example 1: A linear relationship

Consider a [sample dataset](https://people.sc.fsu.edu/~jburkardt/datasets/regression/x01.txt) containing the independent variable, brain weight, and the dependent variable, body weight. In {INSERT FILENAME HERE}, we will provide step-by-step guidance on how to implement and train the model. After training, we can see that it learns the coefficients for the linear equation. The graph below plots all data points and shows the line that the model learned. Pretty cool!

## Example 2: A non-linear (polynomial) relationship

Now what happens if there are multiple independent variables? Consider a [sample dataset](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho) where the independent variables are model name, year, kilometers driven, fuel type, seller type, transmission, and number of owners. The dependent variable is the price the car sold for. In {FILENAME}, we will again provide a step-by-step guide on how to implement and train the model in a way that can take multiple independent variables.


## Sources:
[1] [IBM](https://www.ibm.com/topics/linear-regression#:~:text=the%20next%20step-,What%20is%20linear%20regression%3F,is%20called%20the%20independent%20variable.)
[2] [Scribbr](https://www.scribbr.com/statistics/simple-linear-regression/)
[3] [Statistics by Jim](https://statisticsbyjim.com/regression/linear-regression/)