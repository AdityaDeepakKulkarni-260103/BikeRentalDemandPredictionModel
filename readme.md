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
The model predicts the count of total rental bikes based on the following factors:

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

### Model Coefficients
The coefficients of the model are:
