### Abstract – Summary
<p>The automobile data set is a group of highly correlated predictors along with a response that contains significant outliers that affect the performance of a linear regression machine learning model.  Through a mixture of data truncation, reducing the observations from 205 to 174, and transformation it is possible to create a linear regression model that does a tolerable job of predicting the price of a car using a subset of the predictors.  The model resulting from this process had a R^2 value of .8.</p>

### Research Questions

1.)	What features from the data set have the greatest impact on the price of a car?

The two categorical features with the greatest impact were body style values.  If the car was a hardtop, then it was cost $5,111 more and if it was hatchback it cost $3,353 less.  

2.)	How important was fuel efficiency to car price in 1985?  

<p>When I formulated the questions, I assumed that fuel efficiency would be a predictor, but I ended dropping it in favor of horsepower.  The greater the horsepower in a car the lower the fuel efficiency.  Horsepower had a positive coefficient, which suggests that low fuel efficiency was not prized, but there are a host confounding factors, including that models with the most horsepower, while usually the most expensive, are also only available to the wealthy due to their price.  Another study or analysis would need to be done to properly answer this question.</p>

### Methodology – Logic

<p>Creating this linear regression model was a fascinating process.  I entered the assignment thinking I would create a model that could be used to price a car using the features provided in the dataset.  I envisioned a model where each of the features in the dataset would have a corresponding untransformed dollar value, and I could add or subtract to the average price of a care based on the presence (or absence) of a give feature.  I was surprised by the results.</p>

<p>To begin with, I cleaned the data, removing null values and adjusting data types.  I then reviewed and removed numeric features that appeared to be highly related to each other.  For example, bore and stroke, two features in the original data set, are related to an engine’s horsepower so they were both removed.  I then reviewed the correlations among the remaining features and found significant correlations, which had the potential to affect the accuracy of the model.  I paired the model again and settled on length and HP as two features that had low correlation relative to the remaining predictors and yet could be easily accessible to car buyers: length and horsepower(hp).</p>

<p>Next, I turned my attention to the categorical variables: number of doors, body style, and drive wheels.   In deference to the general preference of machine learning algorithms to work with numbers, I converted the categorical variables into binary, dummy attributes.  I then split the data into 80% and 20% training and test sets and standardized the linear regression model on the data.  </p>

<p>The model had an R^2 value around 0.08, and I knew I had a problem.  I reviewed the plots and noticed that the scatter plots of both the length and the hp variable appeared to have the form of the exponential function.  I re-ran the model and found that the R^2 value went negative, which I didn’t realize could happen.   I tried transforming the two predictors again, this time using a second-order polynomial.  This time R^2 improved to 0.16, better….but not much.  I took another look at the plots and that’s when I realized that the issue was outliers.  More than 75% of the 174 response values—car prices—were less than $16,500, and yet there were 17 response values that were above $25,000 and 8 of those were above $35,000.</p>

<p>After excluding the 17 values greater $25,000, R^2 for the model reached a more respectable 0.809.  The F-statistic of 59, which is greater than 1 also supports the significance of the regression coefficients.  The residual plot for the model exhibited a mostly random appearance.  And after using the model I found plotting the predictions against the response resulted in the appearance of a one-to-one slope.  </p>

<p>Unfortunately, there remain some issues with the model.  One of the dummy variables was not statistically significant, but I was not sure how to treat it.   Further, there remain issues with multicollinearity in the model.  I’m just not sure whether or not to remove additional variables.  </p>

### Conclusions

<p>The result of this process is a linear regression model that has statistically significant coefficients and R^2 of .8.  While it is theoretically possible to use this model to predict the price of a 1985 car, given the cost of a car purchase, I recommend against its serious use.</p>
