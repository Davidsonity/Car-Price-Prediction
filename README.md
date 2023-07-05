# Car Price Prediction

![car](https://user-images.githubusercontent.com/96771321/214902051-e184f7e2-d64e-4cb0-b369-cdc0faa6699e.jpg)
View notebook @ https://github.com/Davidsonity/Car-Price-Prediction/blob/main/notebook.ipynb

This project aims to develop a regression model to predict the selling price of cars based on their characteristics. The dataset used in this project contains historical data of car sale adverts, including various features such as brand, type, color, mileage, and year of registration.

## Dataset Description

The dataset consists of a collection of car sale adverts with over 40,000 observations and 12 features. Each observation represents a car advert and includes the following columns:

- `public_reference`: A unique ID for each vehicle.
- `mileage`: The number of miles traveled or covered by the vehicle.
- `reg_code`: The registration code assigned to the motor vehicle.
- `standard_color`: The color of the motor vehicle.
- `standard_make`: The automotive brand of the vehicle.
- `standard_model`: The specific model of the vehicle.
- `vehicle_condition`: The condition of the vehicle (used or new).
- `year_of_registration`: The year when the vehicle was registered.
- `price`: The selling price of the vehicle.
- `body_type`: The body type of the vehicle.
- `crossover_car_and_van`: A boolean value indicating if the vehicle is a crossover car and van.
- `fuel_type`: The type of fuel consumed by the vehicle.

## Project Overview

The main objective of this project is to develop a regression model that can accurately predict the selling price of cars based on their characteristics. The project follows the following steps:

1. **Data Understanding and Exploration**: In this phase, the dataset is analyzed to gain insights into the features, distributions, and relationships between variables. Visualizations and statistical analysis are performed to understand the data better.

2. **Data Preprocessing**: This phase involves handling missing values, outliers, and noise in the dataset. Data cleaning techniques such as imputation, removal of outliers, and normalization are applied to ensure the quality and reliability of the data.

3. **Feature Engineering**: The dataset is transformed by creating new features or modifying existing ones to enhance the predictive power of the model. Feature engineering techniques such as one-hot encoding, label encoding, and feature scaling are employed to prepare the data for model training.

4. **Model Development**: Various regression algorithms such as Linear Regression, Random Forest, and Extra Trees are trained on the preprocessed data. The models learn the patterns and relationships between the features and the target variable (selling price) to make accurate predictions.

5. **Model Evaluation**: The trained models are evaluated using appropriate evaluation metrics such as mean squared error (MSE) or R-squared to measure their performance. The models are compared, and the best-performing model is selected based on its predictive accuracy and generalization ability.

6. **Model Deployment**: Once the best model is selected, it can be deployed in a production environment to predict the selling price of cars based on their characteristics. The model can be integrated into a web application or used as an API to provide real-time predictions.

## Repository Structure

The repository structure is as follows:

- `LICENSE`: The license file specifying the terms of use for the project.
- `README.md`: This file providing an overview, explanation, and instructions for the project.
- `Report.ipynb`: A Jupyter notebook containing a detailed report of the project, including data exploration, preprocessing, feature engineering, model development, and evaluation.
- `adverts.csv`: The dataset file in CSV format containing the car sale adverts data.
- `notebook.ipynb`: An alternative version of the Jupyter notebook, containing the code for data exploration, preprocessing, feature engineering, model development, and evaluation.

## Usage

To run the project, follow these steps:

1. Clone the repository to your local machine.
2. Install the necessary dependencies, including Python

 and Jupyter Notebook.
3. Open the Jupyter Notebook (`Report.ipynb` or `notebook.ipynb`) using Jupyter Notebook software.
4. Run each cell in the notebook sequentially to execute the code and generate the results.
5. Follow the instructions provided in the notebook for data preprocessing, model training, and evaluation.
6. Analyze the results, including visualizations and model performance metrics, to understand the predictions and choose the best model.

Note: Make sure to have the `adverts.csv` dataset file in the same directory as the notebook.

## Conclusion

This project aims to develop a regression model for predicting the selling price of cars based on their characteristics. By following the steps of data exploration, preprocessing, feature engineering, model development, and evaluation, we aim to build an accurate and reliable prediction model. The trained model can be used to predict car prices in real-world scenarios, aiding car sellers, buyers, and industry professionals in making informed decisions.

For more details, please refer to the complete report in the `Report.ipynb` notebook.

**Disclaimer**: The dataset used in this project is provided by AutoTrader and is for educational and non-commercial use only. Please adhere to the terms of use and avoid any commercial use without proper authorization.
