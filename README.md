# PracticalApplication2_DriversOfCarPrices
## **What drives the price of a car?**
## Overview
In this application, we will explore a dataset from Kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing. My goal is to understand what factors make a car more or less expensive. As a result of my analysis, I would provide clear recommendations to my client -- a used car dealership -- as to what consumers value in a used car.
## Business Understanding
The question is **"what drives the price of a car?"**. Our business interest is to identify the attributes of a used car that are valued by the consumers.

The used car buyer is aware that the car he/she plans to buy is not a brand new car but they typically to look for few factors like numerical features like **milege or model year** etc. and categorical features like **color, make, condition** etc so as to assess the value and decide how much price to pay for a car.

As a Data Scientist, my job is to identify such features based on exisitng data and identify a model that can predict the price and help the used-car dealer to adjust and align their inventory for better business outcomes.
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
  Based on data analyis, I did the following:

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
**Modeling basics:**
1. Split df_numeric data into Train/Test data
2. Initialized StandardScaler
3. scaled Train/Test numerical data
### Models
**1. Linear Regression with 2 features (Input: year, odometer & output: Price)**

    1.1. Got MSEs for train, test data

    1.2. Plotted - Scatter plot of predicted test values

    1.3. predicted - My own car value (An experiment to check the model I created: Answer is pretty close to my car value. yoo-hoo!)

![Alt tezt](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/Model1%20LinearRegression%20Plot.png)

**2. Cross validation of numerical features using SequentialFeatureSelector and CV**
    
    2.1. Based on SFS feature selection, it seems 'year' feature is good enough for the linear model.
    
    2.2. MSE improved slightly when compared to linear regression with 2 features (Year, Odometer)

**3. Ridge Regression Model - Numerical features (Year, Odometer) and Alpha values (1-100)**
    
    3.1. Model complexity is getting reduced as we increase the alpha parameter

**4. Ridge Regression Model - Numerical features (Year, Odometer), Alpha values (1-100) and GRIDSearchCV**
    
    4.1. Ridge value model = 1.0 seems to be better based GridSearchCV

**5. Lasso Regression Model - Numerical features (Year, Odometer) and Standardizarion using Scaler**
    
    5.1. MSE values are slightly better compared to Ridge Regression model

**6. Linear Regression Model with OneHotEncoder(cylinders), OrdinalCoder(condition), Polynominal features(2)**
    
    6.1. MSE values are the best compared to all other models above
    
    6.2. Plotted - Scatter plots of model performance (plot 1, plot2, plot3)
    
    6.3. Clearly this model perform much better than all other models above.

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/LinearR-%20MoreFeatures%20Plot1.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/LinearR-%20MoreFeatures%20Plot2.png)

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/LinearR-%20MoreFeatures%20Plot3.png)

## Evalution

Based on model evaluation, the linear regression model with features like 'year', 'odometer', 'condition', 'cylinders' shown good model performance and lower MSE

### MSE values matrix for various models

| Model Name                 | Train MSE          | Test MSE           |
|----------------------------|--------------------|--------------------|
| Simple Linear Regresssion  | 0.6922398137428262 | 0.6880111324033108 |
| Ridge Liner Regression     | 66715854.17542116  | 66308226.0611658   |
| Lasso Linear Regression    | 66130206.603414    | 65801827.082749404 |
| LR with OHE, OEC           | 48880292.09100207  | 48335495.11685542  |
------------------------------------------------------------------------

## Deployment

Dear Mr. Kurt
Based on extensive data analysis of user car data, machine learning modeling, predictions, we are able to infer that the following 4 features are very important for customers of used cars. so you may adjust your car inventory accordingly and let us know if you have any other questions.

**Below are the important features valued by customers:**

1. Odometer reading

2. Year of Car

3. Condition of the car

4. Number of Cylinders

**Key notes to consider:**

1. The **'odometer'** should be as low as possible

2. The **'year'** should be as latest as possible

3. The **'condition'** should be in excellent, good or like-new for better value

4. The **'cylinders'** should be 8, 6 or 4 as valued by customers


## Response from Kurt

### Well Done team! Thanks for the insights and appreciate the help. We will adjust our car inventory as recommended!

### Thank you!

![Alt text](https://github.com/ravikduvvuri/PracticalApplication2_DriversOfCarPrices/blob/main/kurt.jpeg)



