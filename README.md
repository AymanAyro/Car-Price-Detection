# Car Price Regression Project

This project aims to predict car prices based on various features using machine learning models. It involves data preprocessing, feature engineering, and building multiple regression models to determine the most effective model for price prediction.

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset Information](#dataset-information)
- [Data Preprocessing](#data-preprocessing)
- [Feature Engineering](#feature-engineering)
- [Modeling](#modeling)
- [Results](#results)
- [Libraries Used](#libraries-used)

## Project Overview
The goal of this project is to predict the price of a car based on its features, including:
- Brand
- Year
- Kilometers Driven
- Fuel Type
- Transmission Type
- Engine Size
- Power
- Mileage

The workflow includes:
1. Data Import and Exploration
2. Data Cleaning and Preprocessing
3. Feature Engineering
4. Model Development and Evaluation

## Dataset Information
The dataset contains the following columns:
- **Name**: Name of the car (used to extract brand)
- **Location**: City where the car was sold
- **Year**: Year of manufacture
- **Kilometers_Driven**: Number of kilometers the car has been driven
- **Fuel_Type**: Type of fuel used by the car (e.g., Petrol, Diesel)
- **Transmission**: Type of transmission (Manual/Automatic)
- **Owner_Type**: Ownership status (First, Second, etc.)
- **Mileage**: Mileage of the car (in kmpl or km/kg)
- **Engine**: Engine displacement (in CC)
- **Power**: Power of the car (in bhp)
- **Seats**: Number of seats in the car
- **Price**: Price of the car (Target variable)

## Data Preprocessing
### Handling Missing Values
- **Mileage**, **Engine**, and **Power** columns had missing values which were cleaned by converting strings to numerical values and handling NaNs.
- **New_Price** column had too many missing values, so it was dropped.
- Rows with missing values for **Seats** were also removed.

### Encoding Categorical Data
- Used `LabelEncoder` and `OrdinalEncoder` to transform categorical variables into numerical format.

## Feature Engineering
- Extracted car **Brand** from the **Name** column.
- Scaled numerical features using `RobustScaler` to handle outliers.
- Boxplots were used to detect and remove extreme outliers from the dataset.
- A correlation matrix was plotted to identify feature relationships and redundancy. The **Name** column was dropped due to high correlation with **Brand**.

## Modeling
We developed and compared several machine learning models using the processed dataset:
1. **Linear Regression**
2. **Decision Tree Regressor**
3. **Random Forest Regressor**
4. **XGBoost Regressor**
5. **LightGBM Regressor**

Each model was trained and evaluated on the same dataset, and performance metrics were tracked using `MLflow` for experiment tracking.

## Results
| Model                  | Mean Squared Error (MSE) | R² Score  |
|------------------------|--------------------------|-----------|
| Linear Regression       | 19.35                    | 0.699     |
| Decision Tree Regressor | 9.16                     | 0.857     |
| Random Forest Regressor | 6.13                     | 0.905     |
| XGBoost Regressor       | 5.99                     | 0.907     |
| LightGBM Regressor      | 3.86                     | 0.940     |

![Screenshot 2024-09-23 032708](https://github.com/user-attachments/assets/36042fcd-57cd-4864-aead-246ed87b4052)

The **LightGBM Regressor** performed the best with an MSE of 3.86 and an R² Score of 0.94.

## Libraries Used
- **Pandas**: For data manipulation
- **Numpy**: For numerical computations
- **Matplotlib & Seaborn**: For data visualization
- **Scikit-learn**: For machine learning models and preprocessing
- **XGBoost**: For the XGBoost Regressor
- **LightGBM**: For the LightGBM Regressor
- **MLflow**: For tracking experiments and logging models

## Conclusion
This project demonstrates how to preprocess and engineer features for a regression task, and how to build and compare multiple machine learning models to predict car prices. Among the models used, **LightGBM** performed the best in terms of accuracy and efficiency.
