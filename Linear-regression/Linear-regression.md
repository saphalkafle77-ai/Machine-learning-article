---
layout: post
title: "Linear Regression: From Best Fit Line to Elastic Net"
date: 2026-03-30
---

## What problem does linear regression solve?

Linear regression is used to build a model based on continuous data . It deals to analyize relationship between
dependent and independent variable. Example:
"When I want to predict house price based on its location,house id, LotArea etc.
I need a line that best fits the data."

---

## The best fit line
It is a straight line on a plot that represent relationship between two variables(independent and dependent) .
<img width="304" height="304" alt="image" src="https://github.com/user-attachments/assets/06c66bcf-98cc-4249-9214-c65d025f6df3" />
The equation for best fit line is y = mx + c in math where m is slope and c is intercept. 
The distance between the actual value and predicted value is called error . The minimum the error the best the model works.

To check how much error a model has we use cost function.

---

## Cost function (MSE)

Cost function basically measures how much error does our model contain.
The most common function is Mean squared error :- MSE=n1​∑i=1n​(yi​−y^​i​)2 where yi is actual value and y^i is predicted value

Cost function is used to minimize resudial error but it dooesnot minimize error byt itself.
We use an algorithm called Gradient Descent to minimize it.

---

## Gradient descent

It minimizes the cost step by step, like rolling  a ball down a hill. 
Gradient  means slope and Descent means moving downward . 

![Gradient descent animation](assets/images/gradient-descent.gif)

How to know how much change in our parameter is needed to go downward or upward??
The answer is we need convergence theroem ie :- θ=θ−α⋅(∂θ/∂J) 
where θ = Paramters (slope,intercept)
      α = learning rate(step size)
      ∂θ/∂J = slope of cost function​
If our α is too small, it leads to slow training.
If our α is too big then it can miss the minima 

---

## code 

<img width="510" height="169" alt="image" src="https://github.com/user-attachments/assets/ea48936e-7c46-4cbe-bed4-f0b607bb9e7b" />

Then training our model to predcit 
y_pred = model.predict(X_test)
y_pred



After training our model we use evaluation matrices to measure how good our model is
## Evaluation metrics

| Metric | Meaning | Good when |
|--------|---------|-----------|
| R²     | How much variance explained | Closer to 1 is better |
| MAE    | Average absolute error | Outliers are present |
| RMSE   | Penalises big errors more | Large errors are costly |

---

## Feature engineering and the dummy variable trap

Feature engineering is done before training our model. Our data can be messy, so feature engineering 
is used to transform our input, create new column, and delete column that are unnecessary to make our model performance better.

## It includes 
Encoding Categorical variable .

When you use one-hot encoding, always drop one column.
X = pd.get_dummies(X,columns = ["Color"], drop_first = True,dtype = int)
Example: if you have [Red, Blue, Green], keep only [Blue, Green].
Red = 0,0 means Red automatically.


Dummy variable trap 
Merging of two or more columns into one column. 

Creating useful derived features from  existing ones helps in feature engineering.


## Overfitting and underfitting

- **Underfitting**: model too simple, bad on training data ,high bias and low variance.
- **Overfitting**: model memorises training data, fails on new data , low bias and high variance.
- variance = sensitivity
- bias = error fcolumnsong assumpticolumns[Overfitting vs underfitting](assets/images/overfitting.png)
- **Fix**: use regularisation

---

## Lasso, Ridge, and Elastic Net

| Method | Penalty | Use when |
|--------|---------|----------|
| Lasso (L1) | Absolute value of weights | Many useless features 
| Ridge (L2) | Square of weights | All features matter |
| Elastic Net | L1 + L2 mixed | You are not sure |

---

## My key takeaway
## Connection of all the topics 
At first, we have a dataset . We use feature engineering on that dataset to improve our model performance.
We train our data using various algorithms depending on whether the data is continuous or categorical.
We find a relation between slope and intercept ie Best fit line.
Then we use cost function  to get best parameter for training the model and know how wrong our line is.
After training we check its performance by evaluation metrices.
If our model is overfitting, we use regularization.


![How all concepts connect](assets/images/concept-map.png)
```

