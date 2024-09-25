**Bike Rental Demand Prediction Model**

**Overview**
This repository contains a bike rental demand prediction model developed using linear regression. The model predicts the total count of rental bikes based on various factors such as season, year, month, holiday, weekday, working day, weather situation, temperature, feeling temperature, humidity, wind speed, and counts of casual and registered users.

**Dataset**
The dataset used for this model is the day.csv file, which contains the following fields:

instant: Record index
dteday: Date
season: Season (1: Spring, 2: Summer, 3: Fall, 4: Winter)
yr: Year (0: 2018, 1: 2019)
mnth: Month (1 to 12)
holiday: Whether the day is a holiday (1: Yes, 0: No)
weekday: Day of the week
workingday: If day is neither weekend nor holiday (1: Yes, 0: No)
weathersit: Weather situation (1: Clear, 2: Mist, 3: Light Snow, 4: Heavy Rain)
temp: Temperature in Celsius
atemp: Feels-like temperature in Celsius
hum: Humidity
windspeed: Wind speed
casual: Count of casual users
registered: Count of registered users
cnt: Total count of rental bikes including both casual and registered users

**Model Evaluation**
The model is evaluated using the following metrics:
R-squared score
Mean Squared Error (MSE)
Root Mean Squared Percentage Error (RMSPE)
Total Sum of Squares (TSS)
Residual Sum of Squares (RSS)
Coefficient of Determination (R-squared)

**Model Interpretation**
The model predicts the count of total rental bikes based on the following factors:
instant: Record index
dteday: Date
season: Season (1: Spring, 2: Summer, 3: Fall, 4: Winter)
yr: Year (0: 2018, 1: 2019)
mnth: Month (1 to 12)
holiday: Whether the day is a holiday (1: Yes, 0: No)
weekday: Day of the week
workingday: If day is neither weekend nor holiday (1: Yes, 0: No)
weathersit: Weather situation (1: Clear, 2: Mist, 3: Light Snow, 4: Heavy Rain)
temp: Temperature in Celsius
atemp: Feels-like temperature in Celsius
hum: Humidity
windspeed: Wind speed
casual: Count of casual users
registered: Count of registered users

**Model Coefficients**
The coefficients of the model are:

[-4.68113842e-14 -7.00521884e-13 -7.63817285e-13 1.18991695e-13   9.69340993e-13 1.04427445e-13 6.83890429e+02 1.57894944e+03   9.60458391e-14 -4.15326891e-13 2.02364857e-13 7.51931009e-13   4.86889466e-13 -1.05438375e-13 1.05999700e-13 6.60709620e-13   4.71357850e-13 3.84265397e-14 9.79261968e-14 9.60835231e-14   -1.37483631e-13 -2.79589539e-13 -2.68846138e-13]
The intercept of the model is: 4546.361301369863

**Assignment-based Subjective Questions**
From your analysis of the categorical variables from the dataset, what could you infer about their effect on the dependent variable?
The categorical variables in the dataset, such as season, holiday, and working day, have a significant impact on the demand for shared bikes. The model's coefficients indicate that summer and spring seasons have a positive impact on the demand, while holidays and non-working days have a negative impact.

Why is it important to use drop_first=True during dummy variable creation?
Using drop_first=True during dummy variable creation is important to avoid multicollinearity in the model. When creating dummy variables, one category is used as the reference category, and the coefficients of the other categories are calculated relative to this reference. Without dropping the first category, the model becomes over-specified, resulting in non-unique coefficients.

Looking at the pair-plot among the numerical variables, which one has the highest correlation with the target variable?
The pair-plot shows that the temp variable has the highest correlation with the target variable cnt.

How did you validate the assumptions of Linear Regression after building the model on the training set?
The assumptions of Linear Regression were validated as follows:

Linearity: Checked using pair-plot.
Homoscedasticity: Assessed through the residual plot.
Normality of residuals: Verified using a Q-Q plot.
Multicollinearity: Checked using VIF (Variance Inflation Factor) values.

Based on the final model, which are the top 3 features contributing significantly towards explaining the demand of the shared bikes?
The top 3 features contributing significantly to explaining the demand for shared bikes are:

temp (Temperature)
workingday
season

**General Subjective Questions**
Explain the linear regression algorithm in detail.
Linear regression is a supervised learning algorithm that predicts a continuous output variable based on one or more input features. The algorithm works by finding the best-fitting line that minimizes the sum of squared errors between the predicted and actual values. The equation of the line is represented as:

y = β0 + β1x + ε
Where:

y is the output variable,
x is the input feature,
β0 is the intercept,
β1 is the slope,
ε is the error term.
Explain the Anscombe’s quartet in detail.
Anscombe's quartet is a set of four datasets that have the same statistical properties (mean, variance, correlation), but have different relationships between the variables when visualized. It is used to demonstrate the importance of visualizing data before modeling, as statistical properties alone do not reveal the underlying relationships.

What is Pearson’s R?
Pearson's R is a measure of the linear correlation between two continuous variables. It ranges from -1 to 1:

1 indicates a perfect positive correlation,
-1 indicates a perfect negative correlation,
0 indicates no correlation.
What is scaling? Why is scaling performed? What is the difference between normalized scaling and standardized scaling?
Scaling transforms data to a common scale to prevent features with large ranges from dominating the model.

Normalized scaling (min-max scaling): Scales data to a range (usually between 0 and 1) by subtracting the minimum value and dividing by the range.
Standardized scaling (z-scoring): Scales data to have a mean of 0 and standard deviation of 1 by subtracting the mean and dividing by the standard deviation.
You might have observed that sometimes the value of VIF is infinite. Why does this happen?
The value of VIF (Variance Inflation Factor) becomes infinite when the correlation between two or more features is perfect (i.e., the features are linearly dependent). This occurs because VIF is calculated as:


1 / (1 - R^2)
When R = 1 (perfect correlation), the denominator becomes 0, resulting in an infinite VIF.

What is a Q-Q plot? Explain the use and importance of a Q-Q plot in linear regression.
A Q-Q plot (Quantile-Quantile plot) is a graphical method used to check the normality of residuals in linear regression. The plot compares the quantiles of the residuals to the quantiles of a normal distribution. If the residuals are normally distributed, the points will lie on a straight line. Checking the normality of residuals is important for validating the model's predictions.
