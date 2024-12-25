# Mathematical Derivation of Linear Regression

## The Slope-Intercept Formula

It all starts with the slope-intercept formula, y = mx + b. This is the keystone to the whole model as it defines relationships in the data. However, this equation in its everyday algebra form is limited to handling only one independent variable. What if there are multiple independent variables? We can slightly alter the equation to:

$$ y = w_0 + w_1 \times x $$

Here, we replace $b$ with $w_0$ and $m$ with $w_1$. This adjustment helps us see how the equation can be extended to handle multiple independent variables.

**Extending to Multiple Variables**

Now we can continue that pattern for $n$ independent variables. When doing this the equation becomes:

$$ y = w_0 + w_1 \times X_1 + w_2 \times X_2 + ... + w_n \times X_n $$

Since this is all addition, we do not lose the concept of a linear equation. We can make a final adjustment by considering $w_0$ as being multiplied by 1. If we assume that $X_0$ is always set to 1, we can rewrite the equation as:

$$ y = w_0 \times X_0 + w_1 \times X_1 + w_2 \times X_2 + ... + w_n \times X_n $$

**Vectorized Form**

In implementation, $X$ and $y$ are vectors containing the data for the model. We can rewrite the equation in a more compact and efficient vectorized form: 

$$ \vec{y} = \vec{w} \cdot \vec{X} $$

Where $\vec{w} \cdot \vec{X}$ is the dot product $w$ and $X$ as seen below:

$$ \vec{w} \cdot \vec{X} = w_0 \times X_0 + w_1 \times X_1 + w_2 \times X_2 + ... + w_n \times X_n $$

This compact form allows us to efficiently compute the predicted values using matrix operations, which is especially useful when dealing with large datasets and multiple variables.

**Example** 

If we have 2 independent variables, $X_1$ and $X_2$:

$$ y = w_0 + w_1 \times X_1 + w_2 \times X_2 $$

In vectorized form this is written as:

$$ \vec{y} = \vec{w} \cdot \vec{X} $$

Where: 

* $\vec{w} = [w_0, w_1, w_2]$
* $\vec{X} = [X_0, X_1, X_2]$ (where $X_0 = 1$)

This approach simplifies the computation and makes the model more scalable

## The Cost Function

The objective of linear regression is to find the coefficients, $w_0, w_1, ..., w_n$, such that they minimize the error between the observed values and the predicted values. This is achieved by minimizing the cost function. There are a couple of different common cost functions that are used in linear regression each with there own pros and cons. 

**Sum of Squared Errors (SSE)**

This is one of the more common cost functions for linear regression:

$$ SSE = \sum_{i=1}^{m} (y_i - \hat{y}_i)^2 $$

Where:
* $y_i$ is the actual value of the dependent variable for the ( i )-th observation.
* $\hat{y}_i$ is the predicted value of the dependent variable for the ( i )-th observation.
* $m$ is the number of observations.

SSE ensures that the errors are always viewed as positive by squaring the difference between actual and predicted values. This is important because if the errors were both negative and positive, they could cancel each other out, making the error appear smaller than it is.

Pros:
* Simple to compute and understand.
* Differentiable, making it suitable for optimization algorithms.

Cons:
* Sensitive to outliers, as squaring the error means that outliers have a much greater impact on the model's training.

**Mean Squared Error (MSE)**

This is very similar to SSE but takes the mean of the SSE:

$$ MSE = $$

Where:
* 
* 

Explanation similar to SSE

2. Mean Absolute Error (MAE)
