Vehicle Price Prediction using Machine Learning

Problem Statement

Objective: Predict the price of a vehicle based on its specifications such as make, model, year, mileage, engine, fuel type, transmission, body type, etc.

Problem Type: Supervised Learning --> Regression

Target Variable: - price

The goal of this project is to predict the resale price of a vehicle using historical vehicle data. This can help dealerships, pricing platforms, and customers make data-driven pricing decisions.

Dataset Information

The dataset contains vehicle specifications and resale prices

Includes both numerical and categorical features




Key Features:


name	The full name of the vehicle, including make, model, and trim.

description	A brief description of the vehicle, often including key features and selling points.




make	The manufacturer of the vehicle (e.g., Ford, Toyota, BMW).

model	The model name of the vehicle.

year	The year the vehicle was manufactured.

price	The price of the vehicle in USD.


engine	Details about the engine, including type and specifications.

cylinders	The number of cylinders in the vehicle's engine.

fuel	The type of fuel used by the vehicle (e.g., Gasoline, Diesel, Electric).

mileage	The mileage of the vehicle, typically in miles.

transmission	The type of transmission (e.g., Automatic, Manual).


trim	The trim level of the vehicle, indicating different feature sets or packages.

body	The body style of the vehicle (e.g., SUV, Sedan, Pickup Truck).

doors	The number of doors on the vehicle.

exterior_color	The exterior color of the vehicle.

interior_color	The interior color of the vehicle.

drivetrain	The drivetrain of the vehicle (e.g., All-wheel Drive, Front-wheel Drive).





Tech Stack & Libraries:

Language: Python

Libraries Used: pandas, numpy, matplotlib, seaborn, scikit-learn

Project Workflow

Data Loading: - Loaded the data into pandas DataFrame.

Exploratory Data Analysis (EDA): - Performed the EDA to understand the data, datatypes, summary statistics and distribution of various columns.

I also analyzed various plots to understand the data more clearly like:

Firstly, I started with finding the price distribution for that I used histplot after plotting it found that the data is right skewed means mean > median.

Secondly, I used the scatter plot between year and price column and found Prices vary a lot within the same year. So, there are no strong linear relationships between price and year.

Identified categorical & numerical features: Did this before finding the correlation among the numerical columns.

Lastly, I used the correlation heatmap and found the relationships among various columns and I found newer vehicles cost more; mileage negatively impacts price.

Checked missing values: - After performing EDA next I started with data cleaning for that first I found the missing values.

Handling the missing values: -

Numerical --> fill with median

Categorical --> fill with mode

Median is robust to outliers for numerical data.

Mode is best for categorical data

Feature Engineering: - For that I dropped unnecessary columns.

Dropped columns such as description and name because:

• They do not contribute to price prediction

• They introduce high cardinality

Finding the age of vehicles is necessary because: - Buyers care about age, and not the exact year.

Price drops as age increases --> strong relationship.


Data Preprocessing

Encoded categorical variables: Categorical variables were encoded using Label Encoding to convert text categories into numerical format required by ML models.

Feature scaling (for Linear Regression)

Splitted the dataset in such a way that training contains 80% and test contains 20%.

Standardizing the numerical data: - So that it has mean = 0 and standard deviation=1 using standard scaler class of scikit-learn library.

Model Training: - I used multiple models and compared the results thereof:


For the given specific problem, I used

1.	Linear Regression

2.	Ridge Regression

3.	Lasso Regression

4.	Decision Tree Regressor

5.	Random Forest Regressor

6.	Support vector Regressor

Trained all these models and found their respective y_pred value.

Model Evaluation: - Defining our function for model evaluation. 

For model evaluation we used r2_score, mean absolute error and root mean squared error but not the accuracy as it is a regression problem.

R2 score: -R2 represents the proportion of variance in vehicle prices explained by the model, indicating its overall goodness of fit  

Mean Absolute Error (MAE): - MAE quantifies the average absolute difference between predicted and actual vehicle prices, providing a clear measure of typical prediction error.  

Root Mean Square Error (RMSE): - RMSE emphasizes larger prediction errors by squaring deviations, making it effective for evaluating real-world price prediction accuracy.

 

Random Forest Regressor



R2 Score: 0.7164



MAE: 4339.11



RMSE: 8501.53



Model Comparison & Conclusion



The Random Forest Regressor outperforms all other algorithms across all evaluation metrics.



It achieves a significantly higher R² score 0.71 , indicating a much better ability to explain variance in vehicle prices.



Additionally, it records substantially lower MAE and RMSE, demonstrating more accurate predictions and reduced large errors.




Therefore, Random Forest Regressor is selected as the final model for prediction due to its superior predictive performance.



The models were evaluated using:



R² Score – Measures variance explained by the model



MAE – Average absolute prediction error



RMSE – Penalizes large prediction errors and reflects real-world price deviation.




Analysis of Feature Contributions to Vehicle Price Prediction

 
This model can help us to estimate the vehicle prices based on features like year, fuel type, transmission, mileage etc.

