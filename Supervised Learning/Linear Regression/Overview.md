# What is Linear Regression?

Linear Regression is one of the *most* fundamental machine learning algorithms. It is used to predict the value of a variable based on the value of another variable(s). The goal of Linear Regression is to update (or learn) the coefficients of the linear equation (in its most basic algebraic form, ( y = mx + b )) so that it minimizes the error in the predictions it makes [1].

Some examples of what it can be used for are to determine the strength of the relationship between variables, or, when given a certain value of the independent variable(s), the value of the dependent variable (or in other words, a prediction) [2].

<br><br>

## Why is it Important?

Linear regression is important because it is simple yet powerful. It provides a clear understanding of the relationship between variables and is the foundation for more complex algorithms. It is widely used in various fields such as economics, biology, and engineering to make predictions and infer relationships [3].

<br><br>

## Key Terms:

* **Dependent Variable**: The variable you want to predict. Often represented as **y**.
* **Independent Variable**: The variable(s) you are using to predict the dependent variable. Often represented as **X**.
* **Bias Term**: Also known as the intercept, it is the value of Y when all independent variables are zero.

<br><br>

## How it works:

The most simple form of linear regression uses this slope-intercept formula:

$$ y = w_0 + w_1 \times X $$

* y: This is the predicted value (dependent variable) for any X, sometimes referred to as the response variable.
* $w_0$: This is the intercept, the value of y when X is zero (also commonly known as b in the standard slope-intercept formula).
* $w_1$: This is the slope, the expected change to y as X increases (also commonly known as m in the standard slope-intercept formula).
* X: This is the value that influences y (independent variable), sometimes referred to as the explanatory variable.

<br><br>

*Note: Sometimes this specific form of linear regression where there is only one dependent variable and independent variable is referred to as "simple linear regression" and instead of* $w_0$ *and* $w_1$ *they use* $\beta_1$ *and* $\beta_2$, *respectively. Then when there are multiple independent variables it is sometimes referred to as "multiple linear regression". To keep the equations and explanations as consistent and easy to follow as possible, this clashing notation was not used, but it is worthwhile to be aware of the different ways to refer to linear regression.*

<br><br>

The equation can continue for $n$ values of X and w, leaving us with the equation:

$$ y = w_0 + w_1 \times X_1 + w_2 \times X_2 + \ldots + w_n \times X_n $$

* $X_1, X_2, \ldots, X_n$ are the independent variables.
* $w_1, w_2, \ldots, w_n$ are the coefficients (slopes) corresponding to each independent variable.
* $w_0$ is still the intercept.

<br><br>

To simplify the notation, especially when dealing with multiple variables, we can use vector notation (implemented with Python libraries such as numpy). This allows us to represent the equation more compactly:

$$ \vec{y} = \vec{w} \cdot \vec{X} $$

* $\vec{y}$ is the vector of predicted values.
* $\vec{w}$ is the vector of coefficients (including the intercept).
* $\vec{X}$ is the vector of independent variables. When using the vectorized form $X_0$ will equal one, this is necessary to allow $w_0$ in $\vec{w}$ to remain the slope intercept. 

<br><br>

Now you may be asking... *why use vectorized form?*

Well, using vector notation simplifies the representation and computation, especially when dealing with large datasets and multiple variables. It allows for efficient matrix operations, which are crucial in machine learning algorithms.


<br><br>

Now let's dig a little deeper into what these values really mean...

* **Intercept ($w_0$)**: This is the starting point of the prediction. It represents the value of y when all independent variables are zero. In a multi-variable context, it adjusts the baseline prediction.
* **Coefficients ($w_1, w_2, \ldots, w_n$)**: Each coefficient represents the change in the dependent variable y for a one-unit change in the corresponding independent variable, holding all other variables constant. For example, $w_1$ indicates how much y changes for each unit increase in $X_1$.
* **Independent Variables ($X_1, X_2, \ldots, X_n$)**: These are the features or predictors used to make the prediction. Each variable contributes to the final prediction based on its coefficient.

<br><br>

## When Should it be Used?

To determine if your dataset is suitable for linear regression, ask yourself these questions:

1. Are the variables measured at a continuous level?

    * This means the variables should be things that can take on any value within a range, like time, temperature, or weight.

2. Does it look like there is a linear relationship between the variables?

    * If you plot the data points on a graph, do they roughly form a straight line? This indicates a linear relationship.

3. Is the data independent of each other?

    * Each data point should be independent. For example, the value of one data point should not influence the value of another.

4. Are there no significant outliers?

    * Outliers are data points that are very different from the rest. They can skew the results. If there are outliers, you might need to remove or handle them separately.

5. Is there homoscedasticity?

    * This is a fancy term that means the spread of the residuals (errors) is consistent across all levels of the independent variables. In simpler terms, the variability in the data should be roughly the same across the range of values.

6. Do the errors follow a normal distribution?

    * The differences between the observed and predicted values (errors) should be normally distributed. This means that most errors should be close to zero, with fewer errors as you move away from zero.

If you answered yes to most of these questions, then linear regression is likely a good fit for your dataset. [1]

<br><br>

## Example 1: A simple linear relationship

Consider a [sample dataset](https://people.sc.fsu.edu/~jburkardt/datasets/regression/x01.txt) containing the independent variable, brain weight, and the dependent variable, body weight. In {INSERT FILENAME HERE}, we will provide step-by-step guidance on how to implement and train the model. After training, we can see that it learns the coefficients for the linear equation. The graph below plots all data points and shows the line that the model learned. Pretty cool!

<br><br>

## Example 2: A multiple independents linear relationship

Now what happens if there are multiple independent variables? Consider a [sample dataset](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho) where the independent variables are model name, year, kilometers driven, fuel type, seller type, transmission, and number of owners. The dependent variable is the price the car sold for. In {FILENAME}, we will again provide a step-by-step guide on how to implement and train the model in a way that can take multiple independent variables.

<br><br>

## Sources:

[1] [IBM](https://www.ibm.com/topics/linear-regression#:~:text=the%20next%20step-,What%20is%20linear%20regression%3F,is%20called%20the%20independent%20variable.)

[2] [Scribbr](https://www.scribbr.com/statistics/simple-linear-regression/)

[3] [Statistics by Jim](https://statisticsbyjim.com/regression/linear-regression/)

*Note: This overview was developed with assistance from Microsoft Copilot.*
