# Machine Learing Notes

## Intro  Week 1
### 1.1 Definition###
Older and informal:   
> The field of study that gives computers the ability to learn without being explicitly programmed.  --Arthur Samuel  

A more modern definition:
> A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E.  --Tom Mitchell

~~~
Example: playing checkers.
E = the experience of playing many games of checkers
T = the task of playing checkers.
P = the probability that the program will win the next game.
~~~

- Supervised Learing  
- UnSupervised Learning  
- Others: Reinforcement Learning, Recommender systems

###1.2 Supervised Learning###
Supervised Learning: "Right answers" given  
In supervised learning, we are given a data set and already know what our correct output should look like, having the idea that there is a relationship between the input and the output.

- **Regression**: Predict continuous valued output(e.g. predict the house price)
- **Classification**: Diecrete valued output(0 or 1,e.g. tunor size --> bad or good)

###1.3 Unsupervised Learning###
"Right answer" not given.  
*Cocktail party problem*  
Unsupervised learning allows us to approach problems with little or no idea what our results should look like. We can derive structure from data where we don't necessarily know the effect of the variables.  
We can derive this structure by **clustering** the data based on relationships among the variables in the data.  

###1.4 Model Representation###

>Dataset/ Training Set  
"input" variable/ feature  
"output" variable/ feature
  
To describe the supervised learning problem slightly more formally, our goal is, given a training set, to learn a function h : X → Y so that h(x) is a “good” predictor for the corresponding value of y.   

###1.5 Cost Function###

We can measure the accuracy of our hypothesis function by using a cost function. This takes an average difference (actually a fancier version of an average) of all the results of the hypothesis with inputs from x's and the actual output y's.  
This function is otherwise called the "Squared error function", or "Mean squared error".   
A contour plot is a graph that contains many contour lines. A contour line of a two variable function has a constant value at all points of the same line. An example of such a graph is the one to the right below.  

###1.6 Gradient Descent###
The way we do this is by taking the derivative (the tangential line to a function) of our cost function. The slope of the tangent is the derivative at that point and it will give us a direction to move towards. We make steps down the cost function in the direction with the steepest descent. The size of each step is determined by the parameter α, which is called the learning rate.  
Cost function should be a convex function.  
"Batch" gradient descent: Ecah step of gradient descent uses all the traing examples.  
If **Learning Rate** is too small, it could raech **local** optimization rathan than **global** solution.

###1.7 Linear Algabra Review###
Matrix: n x m  
Vector: n x 1 Matrix。
Matrix addition and multiplication  

## Week 2##
Matlab Installed.
###2.1 Multiple features###
Linear regression with multiple variables is also known as "**multivariate linear regression**". 
Grdient Desnent in multiple features.  

###2.2 Gradient Descent practice: Feature Scaling###

Two techniques to help with this are **feature scaling** and **mean normalization**.  
**Idea**： Features are on a **similar scale**.  
**Feature Scaling**: dividing the input values by the range (i.e. the maximum value minus the minimum value) of the input variable, resulting in a new range of just 1.   
**Mean Normalization**: To make features have approximately zero mean.Mean normalization involves subtracting the **average value** for an input variable from the values for that input variable resulting in a new average value for the input variable of just zero.  
Get every feature **approximately** -1 < x < 1(not too small or too large)   

###2.3 Gradient Descent practice: Learing Rate###

Learning rate should not be too small(slow) or too big(may not converge,slow converge)  
Try a range of values.  

###2.4 Polynomial Regreession###

We can **combine** multiple features into one. For example, we can combine x1 and x2 into a new feature x3 by taking x1⋅x2.

We can **change the behavior or curve** of our hypothesis function by making it a quadratic, cubic or square root function (or any other form).  

###2.5 Normal Equation###

- No need to choose learning rate
- Don't need to iterate
- Slow if there are many features

If XTX is **noninvertible**, the common causes might be having :

- Redundant features, where two features are very closely related (i.e. they are linearly dependent)
- Too many features (e.g. m ≤ n). In this case, delete some features or use "regularization" (to be explained in a later lesson).

###Octave Tutorial###


##Week 3##

###3.1 Classification

- Email: Spam / Not Spam
- Online Transcations: Fradulent / Not 
- Tumor: Malignant / Benign

To attempt classification, one method is to use linear regression and map all predictions greater than 0.5 as a 1 and all less than 0.5 as a 0. However, this method doesn't work well because classification is not actually a linear function.  
    
The classification problem is just like the regression problem, except that the values y we now want to predict take on only a small number of discrete values.

###3.2 Logistic Regression

Want 0 <= h(x) <= 1  

Use **sigmoid function / Logistic function**

>h(theta&x) = estimated probability that y = 1 on input x

P(y = 0|x;theta) + P(y = 1|x;theta) = 1 

###3.3 Decision Boundary

predict y = 1 if h(x) >= 0.5  
predict y = 0 if h(x) < 0.5  

The **decision boundary** is the line that separates the area where y = 0 and where y = 1. It is created by our hypothesis function.

###3.4 Cost Function

We cannot use the same cost function that we use for linear regression because the Logistic Function will cause the output to be wavy, causing many local optima. In other words, it will not be a **convex** function.

Logistic regression cost function  
Cost(h,y) = -log(h(x)) if y = 1  
Cost(h,y) = -log(1- h(x)) if y = 0  

Cost = -y log(h(x)) - (1-y)log(1- h(x))

###3.5 Advanced Optimization

OPtimization algorithms:

- //Gradient descent
- Conjugate gradient
- BFGS
- L-BFGS

No need to mannually pick alpha. Often faster than gradient descnent. More complex.

Use Matlab commmands to calculate gradient.

```matlab
function [jVal, gradient] = costFunction(theta)
  jVal = [...code to compute J(theta)...];
  gradient = [...code to compute derivative of J(theta)...];
end

options = optimset('GradObj', 'on', 'MaxIter', 100);
initialTheta = zeros(2,1);
   [optTheta, functionVal, exitFlag] = fminunc(@costFunction, initialTheta, options);

```

###3.6 Multiclass Classification: One vs All

Since y = {0,1...n}, we divide our problem into n+1 (+1 because the index starts at 0) binary classification problems; in each one, we predict the probability that 'y' is a member of one of our classes.  

We are basically choosing one class and then lumping all the others into a single second class. We do this repeatedly, applying binary logistic regression to each case, and then use the hypothesis that returned the highest value as our prediction.

Train a logistic regression classifier hθ(x) for each class￼ to predict the probability that ￼ ￼y = i￼ ￼.

To make a prediction on a new x, pick the class ￼that maximizes hθ(x)






























