
# Introduction
Linear regression is an analysis that assesses whether one or more predictor variables explain the dependent (criterion) variable.

#Fig Adding immages
<img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/40aca331-eac5-42b2-8d0c-c6ef0718d735/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220327%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220327T083055Z&X-Amz-Expires=86400&X-Amz-Signature=623e42693fb2074d701d6c647801ed8bdebc2c46a78c1c2954f024a7926ad260&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject"
	 style="object-fit:scale-down;
            object-position: center;
            width:100%;
            height:300px;"/>



## Assumptions

1. Linear relationship between the independent and the dependent variable

    <p>If this is not the case, there is no point fitting a linear line on a non linear independent variable.</p>
    <p>To check if this assumption is met, we create a scatter plot between the dependent and independent variable. *We generally do not check the correlation between the two variables as it gives the strength of relationship between two variables not necessarily linear. Adding an example below.*</p>
    <img src="https://s3.us-west-2.amazonaws.com/secure.notion-static.com/40aca331-eac5-42b2-8d0c-c6ef0718d735/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220327%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220327T083055Z&X-Amz-Expires=86400&X-Amz-Signature=623e42693fb2074d701d6c647801ed8bdebc2c46a78c1c2954f024a7926ad260&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject"
    style="object-fit:scale-down;
            object-position: center;
            width:100%;
            height:300px;"/>
    
2. There should be no multi-collinearity in the dataset. (No two features should have high correlation between them) 
    
    This is done because while fitting a line we assume the variable to be as independent and the B value found changes the value of Y with one increment of X when rest all variables are constant. This would not be in the case it features are collinear.
    
3. Independence - All observations are independent of each other
4. There should be Homoscedasticity in the residuals. 
    
    Error term should show random behavior when compared with the predicted values.
    
5. No auto correlation between between errors.
    
    If there is a correlation between the errors, that means the linear regression is not capturing the underlying pattern of the data.
    
6. Errors should be normally distributed. This we can check using QQ plot




linear model makes a prediction by simply computing a weighted sum of the input features, plus a constant called the bias term (also called the intercept term)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9c7cc0ee-cf56-4bae-9c3a-3e5311b59887/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9c7cc0ee-cf56-4bae-9c3a-3e5311b59887/Untitled.png)



- ŷ is the predicted value
- n is the number of features
- xi is the ith feature value
- θj is the jth model parameter (including the bias term θ0 and the feature weights
θ1, θ2, ⋯, θn)

**Using vectorized form**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7470ae21-f77e-4a7b-a14e-a743dceaba86/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7470ae21-f77e-4a7b-a14e-a743dceaba86/Untitled.png)

It is simpler to minimize the Mean Square Error (MSE) than the RMSE (computationally easier) reason we calculate rmse is that it has the same units as average distance from the mean line

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc7490ec-b87a-4b90-a979-32e86182ce42/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dc7490ec-b87a-4b90-a979-32e86182ce42/Untitled.png)

## The Normal Equation

value of θ that minimizes the cost function, there is a closed-form solution, a mathematical equation that gives the result directly

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a6c52c5-84e8-4331-878e-4018acd00496/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a6c52c5-84e8-4331-878e-4018acd00496/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6db1a52-7d5b-47c6-aec0-9eb9bf8e502c/image-1579148691147.jpg1618642342.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d6db1a52-7d5b-47c6-aec0-9eb9bf8e502c/image-1579148691147.jpg1618642342.jpg)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/72bb52b0-16c5-4f4b-bbc6-c9ddbfcfc744/image-1579148740899.jpg435115261.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/72bb52b0-16c5-4f4b-bbc6-c9ddbfcfc744/image-1579148740899.jpg435115261.jpg)

**Computational Complexity**

It is computationally heavy as it has to compute the inverse of XT·X.

But, making predictions with a trained model is linear and takes less time.

### What is regression?

Regression is a technique used to model and analyze the relationships between variables and often times how they contribute and are related to producing a particular outcome together.

### How does it work?

1. Assuming the data looks something like this
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9aab2c0-7aa2-43d6-a9de-5da9a7a377c3/Untitled.png)
    
2. We fit the most basic fitting line, that is the mean line for all the mouse sizes.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7fb60d23-9ab0-468f-957c-6a8adbbd7975/Untitled.png)
    
3. Next, we calculate sum of squares of residuals for this line
4. Then we rotate the line a bit and measure the SS of residuals
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/78b82a35-3bf9-4354-8f0d-1f981b60218e/Untitled.png)
    
5. We create a plot SS residuals and rotations and select parameters where the SS residuals was minimum
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7897e6ef-3f05-49f5-9b00-e35785e9a9c1/Untitled.png)
    
6. This will give us the equation of the line, which will have two parameters B0 and B1.

### Calculating R2, Coefficient of determination

1. We fit a line which shows no variations with the y axis, mean line, and calculate its variance with Y axis.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f428859-f2de-4f1f-91b3-35357bcd82d8/Untitled.png)
    
2. Then, we calculate the variance from the line we fitted.
3. R2 tells us how much variance of the data can be explained by the fitted line.
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/34c610ab-e7b6-4795-ade7-ee56ce1d929f/Untitled.png)
    

It is variation explained by weight/ variation without taking weight into account.

It is also the square of the correlation coefficient. But R2 are easier to interpret as these are in percentages. Basically, R = 0.3 is not 2 times better than R = 0.15 as R2 = 90% and R2 = 22.5%.

Whereas we can directly compare the R2 values. Only drawback in R2 value is they cannot be negative.

### Adjusted R2

Adding more variables are added R2 would increase as it might reduce the SS fit. But that does not mean it is significant.

For this, we use adjusted R2.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ae40d7f8-1882-4c2d-8fc5-a69ce8eee764/Untitled.png)

Here, n-1 and n-p-1 are the DOF of the variables.

Understanding the metric returned during the regression

We never know the true beta of the variable, so we take a sample always from a population to fit a regression. So the beta values obtained are used to infer the actual beta variable.

We use hypothesis testing to establish a significance level based on which we can infer the relationship between coefficients

This is the output we get after the linear regression

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b2dd0dce-2b80-473f-b898-637589cf8d53/Untitled.png)

ANNOVA test statistics

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/faa4a672-5cda-45cf-96b4-d8363fd7c111/Untitled.png)

If we take out mean of all the values, the Total SS is the sum of square of the difference of each value from its mean.

The SS for the model is the SS after the model has been fit. Basically how much explaining the model is doing.

The residual SS is calculated by the sum of difference in (y pred - y act)^2. SSfit.

The df for total is number of obs - 1, for model is number of independent variables, and for residual is N-K-1.

Mean squared is SS/df and is used to calculate the F statistic so that we know that the model would be helpful in explaining variance.

F = MS(model)/ MS(residual)

If P value of F statistic is less than 5% than we go accept that the independent variable be able to explain the model

R2 here is modelSS/ totalSS

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9bc3e553-8fdc-482a-b054-8a651c65b591/Untitled.png)

These are metrics displayed based on the ANOVA test. As, p value is less than 5% we accept the test.

The next table

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/48ddd587-3774-4a89-ad98-a632f6d2299e/Untitled.png)

Coef will tell the weight for each variable.

Understanding standard error, t-statistic, p value

Standard error

We take a lot of samples from the population and calculate their means. The standard deviation of those means is called standard error.

T value

Coefficient/ standard error, what are the odds the coefficient does not contribute the final equation. i.e. the coeff is actually zero. This is used to calculate the p value.

Understanding VIF (variance inflation factor)

Used to find multi collinearity in features. 

When there is multi collinearity the feature weights that are highly correlated become very unreliable and tend to shift a lot even with a small change in the dataset.

But this does not change the model performance, but hampers the model explainability.

Always go for cross validation to address this issue.

In classification it does not matter.

 

High collinearity between features does not mean they'll be multi collinear. Vice versa is also true.

eg. - multi collinearity between a column which has sum of all other columns

VIF is calculated by predicting one independent variable by all other independent variable.

The R2 of this regression is calculated and 

$VIF = 1/(1-R^2)$

for that regression for that particular variable. If variable is explained by the other variable for 90% then drop that variable.

VIF > 10 is dropped

### Calculating P value for R2

P value for R2 comes from the F statistic

F = Ratio of (X explained by Y using the line) to the (X not explained by Y)

The numerator is same as R2 which is reduction in variance caused by the fitted line. = 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d80f4533-0ba4-4b86-99bd-a708b8be3637/Untitled.png)

The denominator will be the sum of squares of the residuals.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fae9e587-870d-4cdb-91c6-e3cf98c65dac/Untitled.png)

Here, the P's are the DOF which convert SS to variances

- P-fit is number of params in the line, which is 2. B1 and B0.
- P-mean will be 1. As this one has a Y intercept.
- n will be the number of points in the line.

Why do we have n-Pfit instead of just n in the denominator of SS fit?

It is a correction made as if the parameter become a lot more the SS fit will decrease a lot and n will stay the same. So net denominator is reduced a lot, so F increases a lot. This is done to make the denominator stable.

### Turning the F statistic to a P value?

First take a random sample and calculate the F value and put it into the histogram and repeat is thousand of times.

We'll get a smooth distribution, then we calculate the F value for the entire dataset and plot on the distribution.

The p value will be the area under the F curve to the right side of the populations F statistic.

p value is smaller when there are more number of observations compared to the parameter in the fit equation.