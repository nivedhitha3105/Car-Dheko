# Car-Dheko


Car Dheko: Used Car Price Prediction

Problem Statement:

The aim of this project is to enhance customer experience and optimize the pricing process for used cars through machine learning. The goal is to develop a reliable, user-friendly tool using Streamlit to predict the prices of used cars based on a variety of features. This predictive tool should be designed as an interactive web application for seamless use by both customers and sales representatives.

Introduction:

The "Car Dheko - Used Car Price Prediction" project involves creating a machine learning model that accurately predicts the prices of used cars, based on historical data from Car Dheko. The dataset includes information about various car attributes, such as make, model, year, fuel type, and transmission type, gathered across different cities. The project’s objective is to process this data, develop and deploy a model capable of delivering instant price predictions for users. This involves data preprocessing, model development, evaluation, and integration of the model into a Streamlit application to ensure accessibility and practical utility for end-users.

Data Collection: 

The Dataset is contains the data of 6 different states in 6 different datasets in excel format.
The data has nested dictionaries and dictionaries in the columns. This is solved by generating a function. The `structure_data(df)` function restructures complex, nested data in a DataFrame by extracting details from specific JSON-like columns (`new_car_detail`, `new_car_overview`, `new_car_feature`, `new_car_specs`, and `car_links`). It iterates through each row, converts the nested JSON strings into dictionaries, and then organizes the data by extracting key-value pairs or lengths of nested lists where applicable. Each column's processed data is stored in separate DataFrames, which are appended to lists. After processing all rows, these lists are combined into separate DataFrames, which are then joined horizontally to create a single, consolidated DataFrame with renamed columns for clarity. The result is a well-structured DataFrame where all nested information is flattened and ready for analysis or modeling tasks.

Data Pre – processing:

The dataframe is then undergoes many pre-processing tasks such as changing the datatype and removing the unwanted values by replacing it with empty space and extracting only numeric values for numeric attributes for easy access. Then the pre-processed data is stored into a csv file for easy access. 

Handling the null values:

Then the process of filling the null values takes place. The null values of numerical data are filled by considering its mean and the required attributes are converted according to the required datatype. Then the null values are removed for both categorical and numerical data. 

Feature Selection:

The data has 77 attributes, we reduced the attributes by using random forest for feature selection and also some manual thinking which attributes are majorly considered for the upcoming process. 

The selective features that are selected are  'km', 'oem', 'model', 'modelYear', 'variantName', 'price', 'Registration Year', 'Ownership', 'Year of Manufacture’,’Comfort & Convenience', 'Exterior', 'Mileage', 'Color', 'Width', 'Wheel Base', 'Acceleration'. 

Then it is again stored into a csv file for future reference.

Removal of Null values:

The null values are handled by filling the mean for numerical data and by filling the mode for categorical data. 

Descriptive Statistics:
The mean, median, standard deviation, minimum value, Q1(25%) , Q2(50%) , Q3(75%) and maximum value is computed.

Label Encoder:
	The categorical columns are converted into numerical for easy implementation. For that, we use label encoder.

Model Development:

Train – Test split:
	The target variable of the data is stored in a separate variable ‘y’ and the remaining variables are considered as ‘x’. then the data is splitted into training and testing data using train_test_split in the ratio 80:20.

Model Selection:

•	Here, three different models are compared. Those models are Linear Regression, Decision tree Regressor and Gradient Boosting Algorithm. 
•	The model’s performance is improved by using cross – validation techniques with cv = 5 and negative mean squared error and grid search is also used for improving the performance of the model.
•	We also use Lasso and Ridge regularization to determine which model performs better.

Model Evaluation:

The model’s performance is evaluated using three different measures. They are 

	Mean Squared error
	Mean Absolute error
	R – squared value
	
	Mean Squared Error:
		MSE measures the average of the squares of the errors, indicating how far the model’s predictions deviate from the actual values. Lower MSE values indicate better model performance.
	Mean Absolute Error:
	MAE calculates the average of absolute differences between predicted and actual values, representing the average prediction error in the model. Like MSE, a lower MAE suggests a more accurate model.

	R – Squared value:
	R² explains the proportion of variance in the target variable that’s predictable from the independent variables. Ranges from 0 to 1, where a higher R² suggests the model explains more of the variance in the target.

Observation:

•	Gradient Boosting has the best performance overall, with the lowest MAE (0.73) and MSE (1.10), and the highest R²score (0.91). This indicates that Gradient Boosting is the most accurate model among the five, as it has the smallest error and explains the most variance in the target variable.

•	Decision Tree also performs relatively well, with the second-lowest MAE (0.94) and MSE (1.89) values, and a high R²score (0.83). However, it's slightly less effective than Gradient Boosting in terms of predictive accuracy.

•	Linear Regression, Lasso Regression, and Ridge Regression have identical performance metrics, with MAE (1.23), MSE (2.97), and R² (0.74). These models show higher error rates and explain less variance than Gradient Boosting and Decision Tree, suggesting they may be less suitable for this particular dataset or problem.

In summary, Gradient Boosting is the best model. therefore, Gradient Boosting regressor can predict the car prices better.
 
Streamlit Web Application:

	The gradient boosting model and min max scaling is saved as model for future use. 
	Then the dataset, min max scaling model and gradient boosting model is imported and the input features are given as input and the ‘price’ that is the target variable is considered for the prediction.
	Once we give some values in input, we will get the predicted price of the used car.

 






