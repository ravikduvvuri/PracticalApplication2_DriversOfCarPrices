# PracticalApplication2_DriversOfCarPrices
## **What drives the price of a car?**
## Overview
In this application, we will explore a dataset from Kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing. My goal is to understand what factors make a car more or less expensive. As a result of my analysis, I would provide clear recommendations to my client -- a used car dealership -- as to what consumers value in a used car.
## Business Understanding
The question is **"what drives the price of a car?"**. Our business interest is to identify the attributes of a used car that is valued by the consumers.

The used car buyer is aware that the car he/she plans to buy is not a brand new car but they typically to look for few factors either numerical features like milege or model year etc. and categorical features like color, make, condition etc so as to assess the value and decides how much price to pay for that car.

So as a Data Scientist, my job is to identify such features based on exisitng data and identify a model that can predict the price based on such factors thus the user-car dealer will better leverage this predictive data to align their inventory accordingly for better business value.
## Data Understanding
To understand the data, Did the following:
  ### Initial steps done
  1. Imported relevant libraries (Updated this section as needed in future)
  2. Read 'vehicles.csv' into a pandas dataframe
  3. Displayed sample data using df.sample(5) to see what features are there in the dataset
  4. Gained some domain knowledge and checked data and possible relationships among them
  ### Next steps done
  5. Using df.info() found the total features, size of the dataset and data types of features
  6. Searched for duplicate data
  7. Identified 'not relevant data' (ex. 'Id', 'VIN' etc.)
  8. Identified 'missing data' and plotted it
    
  ![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/MissingData.png)

## Data Preparation
### Pre-processing of data / Data cleanup
  Based on data analyis, did the following:

  1. Converted Features like 'year', 'odometer' into integers
  2. Dropped 'Id', 'VIN' as they are not useful for price prediction.
  3. Dropped 'Size' feature since 70% of data is missing, so it is not useful to fill-in with any existing data.
  4. Using mode(), Filled-in missing values in other categorical features (condition,cylinders,drive,type,paint_color)
  5. Removed null value rows since the null data is less than 5 percent for all other features (namely 'year', 'manufacturer','model','fuel','odometer','title_status','transmission' etc.)
  6. Removed zero values of 'odometer', 'price'
### Outliers removal
  7. Removed outliers data using Z_score
  8. Adjusted data based on 25%, 50% and 75% data ranges for better representation
  9. Checked price distribution after outliers removal
  10. Clean Dataframes ready:  **df, df_numeric**
     
![Alt test](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/PriceDistribution.png)

### Plots of Clean data
These plots provide the information about how clean data looks like from distrition perspective
1. Pair plot - Numeric data
2. Box plots - Numeric data
3. Bar Plots - Categorical data

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/PairPlot.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/BoxPlot%20-%20Year.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/BoxPlot%20-%20Price.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/BoxPlot%20-%20Odometer.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/Bar%20plot%20%20-%20Transmission.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/Bar%20plot%20%20-%20Title.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/Bar%20plot%20%20-%20Fuel.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/Bar%20plot%20%20-%20Cylinders.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/Bar%20plot%20%20-%20Condition.png)

## Modeling
Modeling basics:
1. Train Test split df_numeric data
2. Initialize StandardScaler
3. scale Train and Test numerical data
### Models
1. Model 1 - Linear Regression with 2 features (Input: year, odometer & output: Price)
   1.1. Get MSEs for train, test data
   1.2. Scatter plot of predicted test values
   1.3. Predict my own car value (An experiment to check the model I created: Answer is pretty close to my car value. yoo-hoo!)

