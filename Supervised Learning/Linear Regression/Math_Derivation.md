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

SSE squares the differences between actual and predicted values. Squaring ensures that all errors are positive and emphasizes larger errors more than smaller ones. This helps in identifying models that have large deviations from actual values.

Pros:
* Simple to compute and understand.
* Differentiable, making it suitable for optimization algorithms.

Cons:
* Sensitive to outliers, as squaring the error means that outliers have a much greater impact on the model's training.

When to Use SSE:
* When you need a simple and straightforward cost function.
* When the dataset does not have significant outliers.

**Mean Squared Error (MSE)**

This is very similar to SSE but takes the mean of the SSE:

$$ MSE = \frac{1}{m} \sum_{i=1}^{m} (y_i - \hat{y}_i)^2$$

Where:
* $y_i$ is the actual value of the dependent variable for the ( i )-th observation.
* $\hat{y}_i$ is the predicted value of the dependent variable for the ( i )-th observation.
* $m$ is the number of observations.

MSE averages the squared errors, providing a normalized measure of error. This makes it easier to compare the performance of models on different datasets or with different numbers of observations.

Pros
* Simple to compute and understand.
* Differentiable, making it suitable for optimization algorithms.
* Provides a normalized measure of error, making it easier to compare across different datasets (because of the division by the number of observations)

Cons
* Since this builds off of SSE, it still has the problem of being sensitive to outliers.

When to Use MSE:
* When you need a normalized measure of error.
* When comparing models across different datasets.

**Mean Absolute Error (MAE)**

Another cost function that is somewhat similar to MSE but using absolute value instead of squaring the error:

$$ MAE = \frac{1}{m} \sum_{i=1}^{m} |y_i - \hat{y}_i| $$

Where
* $y_i$ is the actual value of the dependent variable for the ( i )-th observation.
* $\hat{y}_i$ is the predicted value of the dependent variable for the ( i )-th observation.
* $m$ is the number of observations.

MAE measures the average magnitude of the errors without considering their direction. It is less sensitive to outliers compared to SSE and MSE because it does not square the errors.

Pros:
* Less sensitive to outliers compared to SSE and MSE.
* Provides a more interpretable measure of average error.

Cons:
* Not differentiable at zero, which can complicate optimization.

When to Use MAE:
* When you need a cost function that is less sensitive to outliers.
* When interpretability of the average error is important.

**Huber Loss**

This cost function combines the best of the SSE and MAE:

$$
L_\delta(y, \hat{y}) = 
\begin{cases} 
\frac{1}{2}(y - \hat{y})^2 & \text{for } |y - \hat{y}| \leq \delta \\
\delta |y - \hat{y}| - \frac{1}{2}\delta^2 & \text{otherwise}
\end{cases}
$$

Where 
* $y_i$ is the actual value of the dependent variable for the ( i )-th observation.
* $\hat{y}_i$ is the predicted value of the dependent variable for the ( i )-th observation
* $\delta$ is a hyperparameter that determines whether the outlier is an error.

Huber Loss is quadratic for small errors (like SSE) and linear for large errors (like MAE). This makes it robust and differentiable to outliers.

Pros:
* Robust to outliers while being differentiable.
* Balances the sensitivity to outliers and the smoothness of the error function.

Cons:
* Requires tuning the parameter $\delta$.

When to Use Huber Loss:
* When you need a balance between sensitivity to outliers and smoothness of the error function.
* When you can afford to tune the parameter $\delta$.

**Which One is Commonly Used?**

SSE/MSE is the most commonly used cost function for linear regression because it is simple to computer and differentiable, making it suitable for optimization algorithms like gradient descent. Despite its sensitivity to outliers, its mathematical properties make it a convenient choice for many applications. 

## Gradient Descent

This is an optimization algorithm used to minimize the cost function in ML models. In linear regression, it helps us find the optimal coefficients, $\vec{w} so that the error between the observed values and the predicted values is minimized. 

*Disclaimer: There is a lot to the concept of gradient descent and understanding the pros of using it and its shortcomings. This is something that will have its own section where we deeply go into it and how to address the different shortcomings. For this page, we will just be explaining it in its most basic form so that we can implement our own basic linear regression model.*

So the basic idea behind gradient descent is to iteratively adjust the model parameters $w$ to reduce the cost function. 

**The Gradient of the Cost Function**

For linear regression, the cost function we often use is the Mean Squared Error (MSE):

$$ MSE = \frac{1}{m} \sum_{i=1}^{m} (y_i - \hat{y}_i)^2 $$

To find the gradient of the MSE, we take the partial derivative of it with respect to $w_j$. While the detailed mathematical derivation is not crucial for understanding the concept, it is important to grasp what taking the partial derivative accomplishes.

**Key Point**: Taking the partial derivative of the MSE with respect to each coefficient $w_j$ tells us how the error changes as we adjust that specific coefficient.

The partial derivative of the MSE with respect to $w_j$ is:

$$ \frac{\partial \text{MSE}}{\partial w_j} = -\frac{2}{m} \sum_{i=1}^{m} (y_i - \hat{y}_i) X_{ij} $$

Where
* $X_{ij}$ is the j-th feature of the i-th observation

Now that we have the gradient of the MSE, we can understand the algorithm for training the linear regression model using gradient descent.

## The Gradient Descent Algorithm

**Weight Update Rule**

The gradient descent algorithm updates the coefficients using the following rule:

$$ w_j = w_j - \alpha \frac{\partial MSE}{\partial w_j} $$

Substituting the partial derivative we derived:

$$ w_j = w_j - \alpha \left( -\frac{2}{m} \sum_{i=1}^{m} (y_i - \hat{y}_i) X_{ij} \right) $$

Where 
* $\alpha$ is the learning rate

**Learning Rate, $\alpha$**

The learning rate is a crucial hyperparameter that controls how much the coefficients are adjusted with each step. It requires fine-tuning for optimal performance.

Important Considerations:
* If the learning rate is too large, the algorithm may overshoot the minimum and fail to converge.
* If the learning rate is too small, the algorithm will take very small steps and converge very slowly.

Signs that indicate the need for fine-tuning the learning rate:
* Too Large: The cost function oscillates or diverges.
* Too Small: The cost function decreases very slowly.

In other sections, we will talk about strategies to best optimize the use of the learning rate and its fine-tuning. For now, we will just assume it is a static variable we define before training the model. 

**Steps to Gradient Descent**

Now onto the actual algorithm that is commonly used for training linear regression models. 

1. **Initialize the Coefficients**: Start with initial guesses for $w_0, w_1, \dots, w_n$. These can be zeros or small random values.
2. **Compute Predicted Values**: Use the current coefficients to compute the predicted values, $\hat{y}_i$:

$$ \hat{y}_i = w_0 + w_1 \cdot X_{i1} + w_2 \cdot X_{i2} + \ldots + w_n \cdot + X_{in} $$

3. **Calculate the Gradient**: Compute the gradient of the cost function with respect to each coefficient:

$$ \frac{\partial \text{MSE}}{\partial w_j} = -\frac{2}{m} \sum_{i=1}^{m} (y_i - \hat{y}_i) X_{ij} $$

4. **Update the Coefficients**: Adjust the coefficients in the opposite direction of the gradient:

$$ w_j = w_j - \alpha \frac{\partial MSE}{\partial w_j} $$

5. **Repeat**: Repeat steps 2-4 until the cost function converges (i.e., changes very little between iterations) or a maximum number of iterations is reached.
