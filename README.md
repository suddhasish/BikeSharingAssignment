# Bike sharing Assignment

**Problem Statement**

A bike-sharing system is a service in which bikes are made available for shared use to individuals on a short term basis for a price or free. Many bike share systems allow people to borrow a bike from a "dock" which is usually computer-controlled wherein the user enters the payment information, and the system unlocks it. This bike can then be returned to another dock belonging to the same system.


A US bike-sharing provider BoomBikes has recently suffered considerable dips in their revenues due to the ongoing Corona pandemic. The company is finding it very difficult to sustain in the current market scenario. So, it has decided to come up with a mindful business plan to be able to accelerate its revenue as soon as the ongoing lockdown comes to an end, and the economy restores to a healthy state. 


In such an attempt, BoomBikes aspires to understand the demand for shared bikes among the people after this ongoing quarantine situation ends across the nation due to Covid-19. They have planned this to prepare themselves to cater to the people's needs once the situation gets better all around and stand out from other service providers and make huge profits.


They have contracted a consulting company to understand the factors on which the demand for these shared bikes depends. Specifically, they want to understand the factors affecting the demand for these shared bikes in the American market. The company wants to know:

Which variables are significant in predicting the demand for shared bikes.
How well those variables describe the bike demands
Based on various meteorological surveys and people's styles, the service provider firm has gathered a large dataset on daily bike demands across the American market based on some factors. 


**Business Goal:**

You are required to model the demand for shared bikes with the available independent variables. It will be used by the management to understand how exactly the demands vary with different features. They can accordingly manipulate the business strategy to meet the demand levels and meet the customer's expectations. Further, the model will be a good way for management to understand the demand dynamics of a new market.


## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Conclusions](#conclusions)
* [Acknowledgements](#acknowledgements)

<!-- You can include any other section that is pertinent to your problem -->

## General Information

**Background:**
The project involves building a multiple linear regression model to predict the demand for shared bikes. This prediction model is crucial for BoomBikes, a US-based bike-sharing provider, which has experienced a significant decline in revenue due to the COVID-19 pandemic. The company aims to understand the factors influencing the demand for shared bikes to develop a strategic business plan that can help them recover and thrive post-pandemic.

**Business problem:**

BoomBikes is facing challenges in sustaining its operations during the ongoing pandemic. The company wants to prepare for the post-lockdown period by understanding the demand dynamics for shared bikes. The goal is to identify significant variables that affect bike demand and to quantify how these variables impact the demand. This understanding will enable BoomBikes to adjust their business strategies to meet customer needs effectively and gain a competitive edge in the market.

**Dataset:**
    The dataset provided for this project, **day.csv**, contains daily bike demand data across the American market, with various features that could influence the demand. 
    The fields in the dataset include:

                instant: Record index
                dteday: Date
                season: Season (1: Spring, 2: Summer, 3: Fall, 4: Winter)
                yr: Year (0: 2018, 1: 2019)
                mnth: Month (1 to 12)
                holiday: Whether the day is a holiday (1) or not (0)
                weekday: Day of the week
                workingday: Whether the day is a working day (1) or not (0)
                weathersit: Weather situation:
                weathersit_1: Clear, Few clouds, Partly cloudy
                weathersit_2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
                weathersit_3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
                weathersit_4: Heavy Rain + Ice Pellets + Thunderstorm + Mist, Snow + Fog
                temp: Temperature in Celsius
                atemp: Feeling temperature in Celsius
                hum: Humidity
                windspeed: Wind speed
                casual: Count of casual users
                registered: Count of registered users
                cnt: Count of total rental bikes, including both casual and registered users
    The target variable for the model is 'cnt', which represents the total demand for shared bikes. The dataset also includes other independent variables that may influence bike demand, such as meteorological data and other relevant factors.

    By analyzing this dataset, the project aims to build a robust multiple linear regression model to predict bike demand and provide actionable insights for BoomBikes' management.

<!-- You don't have to answer all the questions - just the ones relevant to your project. -->

## Conclusions

- **Univariate Analysis Conclusions:**

    * Temperature, Humidity, and Windspeed Distribution:
        The temperature predominantly ranges between 10 - 30 Celsius.
        Humidity levels are mostly between 50 - 89.
        Windspeed is generally between 5 - 15.


    * User Count Distribution:

        Casual user counts typically range from 0 - 1000.
        Registered user counts are mostly between 2000 - 5000.
        Overall bike rental counts are generally aligned between 3000 - 5000.

- **Segmented Univariate Analysis Conclusions:**


    * Seasonal Impact on Bike Rentals:

        The mean bike rental count is higher during summer and fall.
        Rental count gradually increases from january to july and it decreases steadily starting August till december.
 
    * Weather Conditions and Bike Rentals:

        Higher bike rental counts are observed under below weather conditions.

         1: Clear, Few clouds, Partly cloudy, Partly cloudy
         2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist

    * Rental count is high on non holiday.

    * Rental count is high on 2019.


- **Bivariate Analysis Conclusions**

    * Correlation Among Numeric Variables:

      - There is a high positive correlation between temperature and feeling temperature, indicating potential multicollinearity.
      - Both temperature and feeling temperature show a positive correlation with bike rental counts.
      - Bike rental counts are negatively correlated with wind speed and humidity, suggesting that higher wind speeds and humidity levels deter bike rentals.


- **Multivariate Analysis Conclusions**

    Multivariate Relationships:

    - Rental count is positively correlated with year and temperature.
    - Temperature is highly positively correlated with feeling temperature, count, and fall, but negatively correlated with spring.
    - Rental count is negatively correlated with wind speed.

### Linear Regression Model Conclusions


- Model 1 - Initial Model:

    The initial model shows a high chance of multicollinearity and insignificance among variables.
    Acceptable ranges for p-values (<0.05) and VIF (<5) are not met, necessitating feature elimination.



- Model 2 - Statsmodel Implementation:

    This model has lower R-squared and adjusted R-squared values compared to the previous model, but VIF values are within acceptable limits.


- Model 3 - Further Feature Elimination:

    Based on RFE, variables such as 'workingday', 'Saturday', 'summer', 'July', and 'November' are suggested for elimination.
    Combining p-values and VIF values helps refine the list of variables for elimination.



- Model 4 - Final Model:

    The final model shows good R-squared values without significant reduction from the first model.
    VIF values are low for all feature columns, indicating minimal multicollinearity.
    Both VIFs and p-values are within acceptable ranges, making this model suitable for final predictions.

**Model Evaluation Conclusions**

Final Model Evaluation:

The difference in R-squared scores between train and test data is very low (<5%), indicating robust model performance.
RMSE for multiple linear regression is 0.091, MAE is 0.068, and MSE is 0.008, all within acceptable ranges.
The final model equation provides a clear representation of the relationship between variables and bike rental counts, confirming the model's reliability in predicting bike rentals.


These conclusions provide a comprehensive understanding of the exploratory data analysis and the linear regression modeling process, highlighting key insights and the effectiveness of the final predictive model.


We can see that the equation of our best fitted line is:


  **Cnt = 0.2314*yr - 0.0910*holiday + 0.4698*temp - 0.1439*hum - 0.1890*windspeed - 0.0791*fall - 0.1422*spring - 0.0580*weathersit_2 - 0.2393*weathersit_3 + 0.1004*September + 0.3745**

Please follow **Suddhasish_Kar.ipynb** for more details
<!-- You don't have to answer all the questions - just the ones relevant to your project. -->


## Technologies Used
- Python - version 3.11.5
- NumPy - version 1.26.4
- Pandas - version 2.2.2
- Matplotlib - version 3.8.4
- Seaborn - version 0.13.2
- scikit-learn  - 1.5.0
- statsmodels - 0.14.2

<!-- As the libraries versions keep on changing, it is recommended to mention the version of library used in this project -->

## Acknowledgements
This is a Assignment done as a part of Executive PG Programme in AI & ML from IIIT, Bangalore by upGrad.

Batch: ML C65

- This project was inspired by real-world business scenarios in Bike share / rental industry.
- Gratitude goes to the open-source community for making the technologies used in this project accessible.

## Contact
Created by [@suddhasish] - feel free to contact me!

<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
