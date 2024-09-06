# Kings County Housing Prices

## Contents
### 1. Objective
### 2. Data Cleaning
### 3. Feature Generation
### 4. Exploratory Data Analysis
### 5. Feature Selection
### 6. Model Comparison
### 7. Chosen Model
### 8. Tableau Dashboard

<br><br><br>



## Objective
This project deals with the prices of houses in Kings County, Washington. The data provided contains various features that help to determine the prices. 

Throughout the course of the project, I will be trying to understand, analyse how these factors contribute to the prices and will build a regression model that can predict prices based on the given features

<br>
### All project files including Data and Jupyter Notebook can be acessed from above
<br><br>
## Data Cleaning
1. Removed 177 duplicates from the "id" column
2. Managing outliers
<br><br>
## Feature Generation 
*1. Age*
   ```python
   df["age"] = df["date"].dt.year - df["yr_built"]
```
*2. Basement Present: Indicates whether the house has a basement or not*
 ```python
df["basement_present"] = df["sqft_basement"].apply(lambda x: 1 if x>0 else 0)
```
*3. Renovated: Indicated whether the house has been renovated or not*
 ```python
df["renovated"] = df["yr_renovated"].apply(lambda x: 1 if x>0 else 0)
```
<br><br>
## Exploratory Data Analysis

### Questions
1. Which features have linear relationships with price?
2. How do the number of bedrooms affect the price of the house?
3. Does the house being on the waterfront or not affect the price
4. Do houses that have been renovated have a higher price

### Findings
1. The 3 features with the most distinct linear relationship with price are Sqft_living, Grade, and Sqft_Above
   
<img src="https://github.com/user-attachments/assets/8589de01-2d87-4b0e-908a-2cba6fe6e614" width="800" height="300" >/

2. Price of houses increase with no. of bedrooms up to 5 and then again at 9. The most expensive houses have either 3,4 or 5 bedrooms

<img src="https://github.com/user-attachments/assets/5e988794-a33a-44c3-868a-efd73dc36806" width="500" height="300" >/

3. Houses at the waterfront or closer to the water have higher prices
   
<img src="https://github.com/user-attachments/assets/d488f491-1f86-4eed-9ba1-7241ec772717" width="300" height="200" >/   <img src="https://github.com/user-attachments/assets/e7018a3a-0121-4714-8351-5c2d1dbe88d5" width="400" height="200" >/   

4. Houses that have been renovated are priced higher than those those that have not been renovated
   
   A two sample independent test was conducted to ensure that the difference in the mean price for house that have been renovated and houses that have not been renovated is statistically significant
A sample of 200 houses was taken for each category

   Null Hypothesis: There is no difference in the mean prices of houses that have been renovated and houses that have not been renovated
   Alternate Hypothesis: There is difference in the mean prices of houes that have been renovated and houses that have not been renovated

   5% Level of significance was selected for this test

   The two sample test gave a p-value of 0.0000000139 which is lower than 0.05 therefore we reject the null hypothesis

<br><br>
## Feature Selection
1. Year Built and Date were dropped as the new Age column made them redundant
2. Yr_Renovated was dropped as a majority of the values were 0
3. Zipcode was dropped as it had too many distinct values to be converted to dummy columns

<br><br>
## Model Comparison
![image](https://github.com/user-attachments/assets/4671c0fa-8d52-4bb0-8789-44c83e1bee9d)


## Chosen Model

XGBoost Regressor was selected because it had the highest performing and least overfitting model 
After tuning hyperparameters of Xgboost with max depth as 5 and n_estimators as 100, train score of 0.90 and test score of 0.88 was obtained

<img src="https://github.com/user-attachments/assets/2cdeeafe-7e93-4ea9-b625-6dfdd15fc3e1" width="400" height="300" >


Other Models:
1. Linear regression was extremely underfitted and was not performing well. 
2. Random forest model was overfitting
<br><br>
## Tableau Dashboard

![image](https://github.com/user-attachments/assets/3d93aab6-4207-4a84-b546-af56ad928046)











