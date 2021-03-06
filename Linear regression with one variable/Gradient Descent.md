# Gradient Descent

- Gradient descent is a algorithm for minimizing the cost function. (You can use gradient descent to minimize other functions as well, not just the cost function J for the linear regression.)
- So we have our hypothesis function and we have a way of measuring how well it fits into the data. Now we need to estimate the parameters in the hypothesis function.
![Alt_text](https://i.imgur.com/gMNkqyV.jpg)

- Imagine that we graph our hypothesis function based on its fields theta_0 and theta_1  (actually we are graphing the cost function as a function of the parameter estimates). We are not graphing x and y itself, but the parameter range of our hypothesis function and the cost resulting from selecting a particular set of parameters.
- We put theta_0 on the x axis and theta_1 on the y axis, with the cost function on the vertical z axis. The points on our graph will be the result of the cost function using our hypothesis with those specific theta parameters. 
![alt_text](https://i.imgur.com/tTCT4WR.png)
- We will know that we have succeeded when our cost function is at the very bottom of the pits in our graph, i.e. when its value is the minimum. 
- The way we do this is by taking the derivative (the tangential line to a function) of our cost function. The slope of the tangent is the derivative at that point and it will give us a direction to move towards. We make steps down the cost function in the direction with the steepest descent. The size of each step is determined by the parameter α, which is called the learning rate. 
- For example, the distance between each 'star' in the graph above represents a step determined by our parameter α. A smaller α would result in a smaller step and a larger α results in a larger step. The direction in which the step is taken is determined by the partial derivative of J(theta_0,theta_1). Depending on where one starts on the graph, one could end up at different points. The image above shows us two different starting points that end up in two different places. 
- So if you had started the first point, you would've wound up at left local optimum, but if you started just at a slightly different location, you would've wound up at a very different local optimum.

 ## The gradient descent algorithm formula: 
- ![alt_text](https://i.imgur.com/W3RX6HA.jpg)
- := is the assignment operator.  If a := b  this means in computers take the value in b and use it overwrite whatever value is a. (Whereas in contrast, if I use the equal sign and I write a equals b, then this is a truth assertion)
- This alpha is the learning rate
- And the subtlety of how you implement gradient descent is for th expression, for this update equation, you want to simultaneously update theta 0 and theta 1.
- So I'm gonna set temp0 equals that, set temp1 equals that so basic compute the right-hand sides, and then having computed the right-hand sides and stored them into variables temp0 and temp1, I'm gonna update theta 0 and theta 1 simultaneously because that's the correct implementation.
- ![Alt_text](https://i.imgur.com/LbsrFD6.png)
- Right is wrong: by this time you've already updated theta 0, then you would be using the new value of theta 0 to compute this derivative term. And so this gives you a different value of temp1, than the left-hand side. Because you've now plugged in the new value of theta 0 into this equation. And so, this on the right-hand side is not a correct implementation of gradient descent.

## Example with just one parameter
- slightly simpler example, where we want to minimize the function of just one parameter. So say we have a cost function, j of just one parameter, theta one.
- We're going to compute this derivative (making a tangent to that point). The slope of a line is just this height divided by this horizontal length. Resulting to a negative or positiv number of the slope.
- Regardless of the slope theta_1 eventually converges to its minimum value. The following graph shows that when the slope is negative, the value of theta_1 increases and when it is positive, the value of theta_1  decreases. ![alt_text](https://i.imgur.com/2vgcaQR.png)
- On a side note, we should adjust our parameter  alpha α to ensure that the gradient descent algorithm converges in a reasonable time. Failure to converge or too much time to obtain the minimum value imply that our step size is wrong. ![alt_text](https://i.imgur.com/GcBPgCH.png)
![alt_text](https://i.imgur.com/Prh42xf.jpg)


## Gradient Descent For Linear Regression
- When specifically applied to the case of linear regression, a new form of the gradient descent equation can be derived. We can substitute our actual cost function and our actual hypothesis function and modify the equation to:
- In order to apply gradient descent, the key term we need is the derivative term. So you need to figure out what is this partial derivative term and plugging in the definition of the cause function j.
![alt_text](https://i.imgur.com/qWbCInT.jpg)
- After some simplifying:
![alt_text](https://i.imgur.com/B2cCTcM.jpg)
-We get the linear regression algorithm:
![alt_text](https://i.imgur.com/kcTHFBZ.jpg)
![alt_text](https://i.imgur.com/6o03Pvm.jpg)
- The point of all this is that if we start with a guess for our hypothesis and then repeatedly apply these gradient descent equations, our hypothesis will become more and more accurate.

- So, this is simply gradient descent on the original cost function J. This method looks at every example in the entire training set on every step, and is called batch gradient descent. Note that, while gradient descent can be susceptible to local minima in general, the optimization problem we have posed here for linear regression has only one global, and no other local, optima; thus gradient descent always converges (assuming the learning rate α is not too large) to the global minimum. Indeed, J is a convex quadratic function. Here is an example of gradient descent as it is run to minimize a quadratic function.
![alt_text](https://i.imgur.com/UlOUA11.png)
- The ellipses shown above are the contours of a quadratic function. Also shown is the trajectory taken by gradient descent, which was initialized at (48,30). The x’s in the figure (joined by straight lines) mark the successive values of θ that gradient descent went through as it converged to its minimum.
