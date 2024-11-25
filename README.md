# PracticalApplication2_DriversOfCarPrices
## **What drives the price of a car?**
## Overview
In this application, we will explore a dataset from Kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing. My goal is to understand what factors make a car more or less expensive. As a result of my analysis, I would provide clear recommendations to my client -- a used car dealership -- as to what consumers value in a used car.
## Business Understanding
The question is **"what drives the price of a car?"**. Our business interest is to identify the attributes of a used car that is valued by the consumers.

The used car buyer is aware that the car he/she plans to buy is not a brand new car but they typically to look for few factors either numerical features like milege or model year etc. and categorical features like color, make, condition etc so as to assess the value and decides how much price to pay for that car.

So as a Data Scientist, my job is to identify such features based on exisitng data and identify a model that can predict the price based on such factors thus the user-car dealer will better leverage this predictive data to align their inventory accordingly for better business value.
## Data Understanding
To understand the data, Did the following steps:
  ### Initial steps
  1. Read 'vehicles.csv' into a pandas dataframe
  2. Displayed sample data using df.sample(5) to see what features are there in the dataset
  3. Gained some domain knowledge and checked data and possible relationships among them
  ### Next Steps
  5. Using df.info() found the total features, size of the dataset and data types of features
  6. Searched for duplicate data
  7. Identified 'not relevant data (ex. 'Id', 'VIN' etc.)
  8. Identified 'missing data' and plotted data

