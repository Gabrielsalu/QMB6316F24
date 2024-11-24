# Assignment 3



Following the instructions in the document ```QMB6316_assignment_03.pdf``` above, 
enter your responses in the code blocks shown below.

*Please note that the document has been revised to clarify some details and correct a typo. These changes are shown in red.*


In this exercise, we will follow an approach different than that taken in class. 
We will first estimate a model with our choices of functional form, then consider exclusions of insignificant variables from the full model. 
Note that this approach allows for inclusion of possibly irrelevant variables and avoids excluding any relevant variables. 


At each stage, use the best model that you have found so far, 
incorporating the findings from the answer to the previous question.




a. Estimate a regression model that uses all available variables.
	Make sure to choose a reasonable transformation of the dependent variable, 
	such as the logarithmic transformation, if necessary.
	
```
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + cab + diesel + fwd + johndeere + spring + 
    summer + winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.75656 -0.23453  0.05714  0.27916  0.72523 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.892e+00  1.118e-01  79.523  < 2e-16 ***
horsepower          1.124e-02  1.079e-03  10.421  < 2e-16 ***
squared_horsepower -1.583e-05  2.279e-06  -6.948 2.89e-11 ***
age                -3.455e-02  3.479e-03  -9.929  < 2e-16 ***
enghours           -4.157e-05  9.685e-06  -4.292 2.49e-05 ***
cab                 4.644e-01  7.074e-02   6.564 2.76e-10 ***
diesel              1.308e-01  9.351e-02   1.399  0.16299    
fwd                 2.669e-01  5.914e-02   4.513 9.64e-06 ***
johndeere           2.896e-01  7.250e-02   3.995 8.41e-05 ***
spring             -1.159e-01  6.559e-02  -1.767  0.07833 .  
summer             -1.981e-01  6.433e-02  -3.080  0.00229 ** 
winter             -1.879e-01  7.188e-02  -2.614  0.00946 ** 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.402 on 264 degrees of freedom
Multiple R-squared:  0.7933,	Adjusted R-squared:  0.7847 
F-statistic: 92.12 on 11 and 264 DF,  p-value: < 2.2e-16
                   
                   

```

Does this seem to be a reasonable model, as opposed to using average tractor prices? 
Said differently, do at least some of the variables help to predict the prices of used tractors?
Is the R-squared or the R-bar-squared reasonably high?

```
WHEN COMPARING R & R-ADJUSTED FROM THE AVERAGE SALE PRICE AND THE LOG(SALESPRICE), BOTH VALUE ARE
LARGER IN THE LOG(SALES PRICE) SHOWING THAT MODEL HAS MORE CORRELATION WITH THE DATA THEN AVERAGE 
SALES PRICE MODEL


```


b. Which variables seem to help explain used tractor prices? 
	Which have positive and negative relationships with tractor prices?
	Which variables that do not seem to have statistically significant coefficients under this specification?
	
```
SIGNIFICANT - HORSEPOWER (+) SQUARED HORSEPOWER (-) AGE (-) ENGHOURS (-) CAB (+) FWD (+) 
JOHNDEERE (+) SUMMER (-) WINTER (-)

NO SIGNIFICANT - DIESEL, SPRING


```



c. Before making any reductions to your model, revise the model specification first
	by considering nonlinear specifications.
	A used tractor dealer tells you that overpowered used tractors are hard to sell, since they consume more fuel. 
      Tractor prices often increase with horsepower, up to a point, but beyond that they decrease. 
      To incorporate this advice, you create and include a variable for squared horsepower and include that in a new regression model. 
      

```
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + cab + diesel + fwd + johndeere + spring + 
    summer + winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.75656 -0.23453  0.05714  0.27916  0.72523 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.892e+00  1.118e-01  79.523  < 2e-16 ***
horsepower          1.124e-02  1.079e-03  10.421  < 2e-16 ***
squared_horsepower -1.583e-05  2.279e-06  -6.948 2.89e-11 ***
age                -3.455e-02  3.479e-03  -9.929  < 2e-16 ***
enghours           -4.157e-05  9.685e-06  -4.292 2.49e-05 ***
cab                 4.644e-01  7.074e-02   6.564 2.76e-10 ***
diesel              1.308e-01  9.351e-02   1.399  0.16299    
fwd                 2.669e-01  5.914e-02   4.513 9.64e-06 ***
johndeere           2.896e-01  7.250e-02   3.995 8.41e-05 ***
spring             -1.159e-01  6.559e-02  -1.767  0.07833 .  
summer             -1.981e-01  6.433e-02  -3.080  0.00229 ** 
winter             -1.879e-01  7.188e-02  -2.614  0.00946 ** 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.402 on 264 degrees of freedom
Multiple R-squared:  0.7933,	Adjusted R-squared:  0.7847 
F-statistic: 92.12 on 11 and 264 DF,  p-value: < 2.2e-16



```


  c.i) Hypothesize the signs for the coefficients on horsepower 
	under this scenario. 
		What should be the sign of the coefficient for horsepower? 
		What sign do you expect for squared horsepower?
      
```
HORSEPOWER (+) SQUAREHORESEPOWER (-)


```

  c.ii) Perform 1-sided t-tests of the hypotheses for each of the horsepower coefficients. 
That is, are the t-statistics higher than 1.96, with the same sign as you hypothesized?

```

HORSEPOWER (+) T-VALUE = 10.421
SQUAREDHORSEPOWER (-) T-VALUE = -6.948



```

  c.iii) Compare the models with and without the quadratic functional form for horsepower.
            Which model do you recommend? 
		Be sure to cite evidence to support your choice. 
		Specifically, check the four specification criteria: 
		statistical significant $t$-statistics, 
		an increase in R-squared, 
		a good theoretical justification, and 
		no large change in the other coefficients.

```
I RECOMMEND THE MODEL WITH THE QUADRADIC. BOTH R & ADJUSTED R VALUES ARE HIGHER.



```


d. Again, use the best model that results from the answer to the previous question to address further questions.
	Use the model you have so far to test that the time of year has no effect on the sale of tractors.
	That is, test whether the t-statistics on the seasonal indicators are statistically significant. 
	Is there evidence that tractor prices follow a seasonal pattern? 

```
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + cab + diesel + fwd + johndeere + spring + 
    summer + winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.75656 -0.23453  0.05714  0.27916  0.72523 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.892e+00  1.118e-01  79.523  < 2e-16 ***
horsepower          1.124e-02  1.079e-03  10.421  < 2e-16 ***
squared_horsepower -1.583e-05  2.279e-06  -6.948 2.89e-11 ***
age                -3.455e-02  3.479e-03  -9.929  < 2e-16 ***
enghours           -4.157e-05  9.685e-06  -4.292 2.49e-05 ***
cab                 4.644e-01  7.074e-02   6.564 2.76e-10 ***
diesel              1.308e-01  9.351e-02   1.399  0.16299    
fwd                 2.669e-01  5.914e-02   4.513 9.64e-06 ***
johndeere           2.896e-01  7.250e-02   3.995 8.41e-05 ***
spring             -1.159e-01  6.559e-02  -1.767  0.07833 .  
summer             -1.981e-01  6.433e-02  -3.080  0.00229 ** 
winter             -1.879e-01  7.188e-02  -2.614  0.00946 ** 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.402 on 264 degrees of freedom
Multiple R-squared:  0.7933,	Adjusted R-squared:  0.7847 
F-statistic: 92.12 on 11 and 264 DF,  p-value: < 2.2e-16
00


```
	
	
e. Finally, consider another modification to your model. 
	Some say that John Deere tractors hold their value longer than other tractors. 
      This raises the question of whether an additional hour of use affects the value of a John Deere tractor 
	differently than for tractors of other brands. 
	You can test this by including an interaction with ```enghours:johndeere``` in the regression.
	
```

lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + cab + diesel + fwd + johndeere + enghours:johndeere + 
    spring + summer + winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.76552 -0.23263  0.05137  0.27305  0.75048 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.896e+00  1.121e-01  79.330  < 2e-16 ***
horsepower          1.122e-02  1.081e-03  10.377  < 2e-16 ***
squared_horsepower -1.574e-05  2.289e-06  -6.877 4.44e-11 ***
age                -3.455e-02  3.484e-03  -9.918  < 2e-16 ***
enghours           -4.335e-05  1.026e-05  -4.224 3.31e-05 ***
cab                 4.669e-01  7.100e-02   6.576 2.59e-10 ***
diesel              1.363e-01  9.420e-02   1.447  0.14923    
fwd                 2.660e-01  5.924e-02   4.491 1.06e-05 ***
johndeere           2.466e-01  1.088e-01   2.267  0.02423 *  
spring             -1.203e-01  6.619e-02  -1.817  0.07032 .  
summer             -2.027e-01  6.498e-02  -3.119  0.00202 ** 
winter             -1.881e-01  7.198e-02  -2.613  0.00948 ** 
enghours:johndeere  1.112e-05  2.094e-05   0.531  0.59564    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4025 on 263 degrees of freedom
Multiple R-squared:  0.7935,	Adjusted R-squared:  0.7841 
F-statistic: 84.24 on 12 and 263 DF,  p-value: < 2.2e-16

```

Test the hypothesis, at the 5 percent level of significance, that the slope for engine hours differs by brand. 

Does an additional hour of use affect the price of a John Deere tractor
differently than tractors of other brands?
	
```
AT 5% SIGNIFICANCE, WE ARE LOOKING FOR A T-VALUE OF AT LEAST 1.96. THE RELATIONSHIP BETWEEN ENGINE 
HOUR AND JONHDEERE PROVE INSIGNICANT, WITH A T- VALUE OF 0.531. LOWER THAN THE MINIMUM 1.96/



```
	
	
	
