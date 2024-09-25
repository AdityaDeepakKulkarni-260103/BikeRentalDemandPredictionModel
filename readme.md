# Bike Rental Demand Prediction Model

## Overview
This repository contains a **bike rental demand prediction model** developed using **linear regression**. The model predicts the total count of rental bikes based on various factors such as season, year, month, holiday, weekday, working day, weather situation, temperature, feeling temperature, humidity, wind speed, and counts of casual and registered users.

## Dataset
The dataset used for this model is the **day.csv** file, which contains the following fields:

- **instant**: Record index  
- **dteday**: Date  
- **season**: Season (1: Spring, 2: Summer, 3: Fall, 4: Winter)  
- **yr**: Year (0: 2018, 1: 2019)  
- **mnth**: Month (1 to 12)  
- **holiday**: Whether the day is a holiday (1: Yes, 0: No)  
- **weekday**: Day of the week  
- **workingday**: If day is neither weekend nor holiday (1: Yes, 0: No)  
- **weathersit**: Weather situation (1: Clear, 2: Mist, 3: Light Snow, 4: Heavy Rain)  
- **temp**: Temperature in Celsius  
- **atemp**: Feels-like temperature in Celsius  
- **hum**: Humidity  
- **windspeed**: Wind speed  
- **casual**: Count of casual users  
- **registered**: Count of registered users  
- **cnt**: Total count of rental bikes including both casual and registered users

## Model Evaluation
The model is evaluated using the following metrics:

- **R-squared score**  :1.0
- **Mean Squared Error (MSE)**  :1.1159856243673468e-23
- **Root Mean Squared Percentage Error (RMSPE)**  :7.671532422317025e-14
- **Total Sum of Squares (TSS)**  :499734927.34246576
- **Residual Sum of Squares (RSS)**  : 1.6293390115763263e-21
- **Coefficient of Determination (R-squared)** :1.0

## Model Interpretation

The model predicts the count of total rental bikes (`cnt`) based on the following factors:

- **instant**: record index
- **dteday**: date
- **season**: season (1: spring, 2: summer, 3: fall, 4: winter)
- **yr**: year (0: 2018, 1: 2019)
- **mnth**: month (1 to 12)
- **holiday**: whether the day is a holiday or not
- **weekday**: day of the week
- **workingday**: if the day is neither a weekend nor a holiday (1: Yes, 0: No)
- **weathersit**: weather situation (1: Clear, 2: Mist, 3: Light Snow, 4: Heavy Rain)
- **temp**: temperature in Celsius
- **atemp**: feels-like temperature in Celsius
- **hum**: humidity
- **windspeed**: wind speed
- **casual**: count of casual users
- **registered**: count of registered users

### Coefficient Interpretation

From the given coefficients, here’s what we can infer about the model:

1. **Temperature (temp)**: A positive coefficient for temperature suggests that higher temperatures lead to increased bike rental demand, as warmer weather is more conducive to outdoor activities.
   
2. **Working Day (workingday)**: The model indicates that the demand for bikes is higher on working days. People are more likely to rent bikes for commuting during weekdays.

3. **Season (season)**: 
   - Spring and summer have positive coefficients, meaning that during these seasons, bike rentals increase. In contrast, colder seasons like winter reduce bike rental demand.

4. **Casual and Registered Users**: Both casual and registered users contribute positively to the total count of rented bikes, which aligns with the model’s objective of predicting total rentals.

5. **Weather Situation (weathersit)**: Clearer weather conditions correlate with higher bike rental demand, whereas extreme weather (such as heavy rain or snow) decreases the number of rentals.

### Summary:

The model highlights that factors like **warmer temperatures**, **working days**, **clear weather**, and **favorable seasons** (spring and summer) positively influence the demand for rental bikes. Conversely, colder temperatures, holidays, and extreme weather conditions reduce bike rental demand.


---

## Assignment-based Subjective Questions

### 1. From your analysis of the categorical variables from the dataset, what could you infer about their effect on the dependent variable?
The categorical variables in the dataset, such as **season**, **holiday**, and **working day**, have a significant impact on the demand for shared bikes. The model's coefficients indicate that **summer** and **spring seasons** have a positive impact on the demand, while **holidays** and **non-working days** have a negative impact.

### 2. Why is it important to use drop_first=True during dummy variable creation?
Using `drop_first=True` during dummy variable creation is important to avoid **multicollinearity** in the model. When creating dummy variables, one category is used as the **reference category**, and the coefficients of the other categories are calculated relative to this reference. Without dropping the first category, the model becomes **over-specified**, resulting in non-unique coefficients.

### 3. Looking at the pair-plot among the numerical variables, which one has the highest correlation with the target variable?
The pair-plot shows that the **temp** variable has the highest correlation with the target variable **cnt**.

### 4. How did you validate the assumptions of Linear Regression after building the model on the training set?
The assumptions of **Linear Regression** were validated as follows:  
- **Linearity**: Checked using pair-plot.  
- **Homoscedasticity**: Assessed through the residual plot.  
- **Normality of residuals**: Verified using a Q-Q plot.  
- **Multicollinearity**: Checked using **VIF** (Variance Inflation Factor) values.

### 5. Based on the final model, which are the top 3 features contributing significantly towards explaining the demand of the shared bikes?
The top 3 features contributing significantly to explaining the demand for shared bikes are:
1. **temp** (Temperature)  
2. **workingday**  
3. **season**

---

## General Subjective Questions

### 1. Explain the linear regression algorithm in detail.
Linear regression is a **supervised learning algorithm** that predicts a continuous output variable based on one or more input features. The algorithm works by finding the **best-fitting line** that minimizes the sum of squared errors between the predicted and actual values. The equation of the line is represented as:  
y = β0 + β1x + ε
Where:
- **y** is the output variable  
- **x** is the input feature  
- **β0** is the intercept  
- **β1** is the slope  
- **ε** is the error term

### 2. Explain the Anscombe’s quartet in detail.
Anscombe's quartet is a set of **four datasets** that have the same statistical properties (mean, variance, correlation), but have different relationships between the variables when visualized. It is used to demonstrate the importance of **visualizing data** before modeling, as statistical properties alone do not reveal the underlying relationships.

### 3. What is Pearson’s R?
**Pearson's R** is a measure of the **linear correlation** between two continuous variables. It ranges from **-1** to **1**:  
- **1** indicates a perfect positive correlation  
- **-1** indicates a perfect negative correlation  
- **0** indicates no correlation

### 4. What is scaling? Why is scaling performed? What is the difference between normalized scaling and standardized scaling?
**Scaling** transforms data to a common scale to prevent features with large ranges from dominating the model.  
- **Normalized scaling (min-max scaling)**: Scales data to a range (usually between 0 and 1) by subtracting the minimum value and dividing by the range.  
- **Standardized scaling (z-scoring)**: Scales data to have a **mean of 0** and **standard deviation of 1** by subtracting the mean and dividing by the standard deviation.

### 5. You might have observed that sometimes the value of VIF is infinite. Why does this happen?
The value of **VIF** (Variance Inflation Factor) becomes infinite when the **correlation between two or more features is perfect** (i.e., the features are linearly dependent). This occurs because VIF is calculated as:  
1 / (1 - R^2)
When **R = 1** (perfect correlation), the denominator becomes **0**, resulting in an **infinite VIF**
