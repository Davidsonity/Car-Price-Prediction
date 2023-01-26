### Car Price Prediction

### INTRODUCTION
#### Objectives
The objective of this project is to to produce a regression model for predicting the selling price given the characteristics of
the cars in the historical data given.

#### About Dataset
The dataset is a Car Sale Adverts dataset provided by AutoTrader(AT), one of our industry partners. The dataset contains 12 features and over 40,000 observations an anonymised collection of adverts with information on vehicles such as brand, type, colour, mileage, as well as the selling price.

The following are the description of each columns in the dataset:
- ***public_reference:*** key id of vehicle
- ***mileage:*** a number of miles travelled or covered
- ***reg_code:*** a sequence of letters and numbers assigned to a motor vehicle when it is registered
- ***standard_colour:*** colour of motor vehicle
- ***standard_make:*** vehicle automotive brand
- ***standard_model:*** specific model of a vehicle brand
- ***vehicle_condition:*** condition of the vehicle i.e used or new
- ***year_of_registration:*** the year a vehicle was registration
- ***price:*** the price of the vehicle
- ***body_type:*** body type of the vehicle
- ***crossover_car_and_van:*** A boolean (yes if the vehicle is a crossover car and van or No if its not)
- ***fuel_type:*** the type of fuel consumed by the vehicle

####  Analysis of Univariate Distributions

The image below shows the code and output which contains the columns, number of observations and datatype of each features

![info.jpg](attachment:99cd26d7-69f8-4c2a-a9a8-c0407fdcc96f.jpg)

##### Some Univariate visualization

![mileage.png](attachment:8364f72a-faef-410e-a82e-8e6071a8ce71.png)

**Insight:**
- Multiple outliers available
- Majority of car mileage are below 200,000

![reg_code.png](attachment:1422ee2b-8579-4b8d-baf2-3e83c29f8e50.png)

**Insight:** 17, 67, 66 respectively are the top 3 most popular registration code

![standard_color.png](attachment:b5776dfd-1d05-4de6-9a13-279bbd21d79c.png)

**Insight:** Black, White, Grey, Blue, Silver are the top 5 most popular color 

![standard_make.png](attachment:29b80540-21c6-4e81-9a3a-5b9387d094cf.png)

**Insight:**
BMW, Audi, Volswagwn, Vauxhall, Mercedes-Benz are the top 5 most popular vehicle brand

![vehicle_condition.png](attachment:1e3534e2-7fd9-4606-b029-c40576389528.png)

**Insight:**
Majority of the vehicles in the dataset are USED vehicles

![year_of_registration.png](attachment:66c9a342-c03d-434c-a4d1-b04063ea2457.png)

**Insight:**
Most of the vehicles were registarted in 2017

![price.png](attachment:c4e4aa66-9b9c-4920-a418-873fccca90a8.png)

**Insight:**
- Possible outliers approaching 10M
- Most cars are below 500,000

![body_type.png](attachment:887459bc-3c0a-4dec-b0d0-7399c5c14ee0.png)

**Insight:**
Hatchback and SUV are the most popular body type of vehicle in the dataset

![crossover_car_and_van.png](attachment:dab185ea-2520-49d6-a6c7-ba0b7371e78f.png)

**Insight:**
Majority of the vehicles are not crossover car and van

![fuel_type.png](attachment:10760a4d-4a6a-4437-a6fb-6e5f97caacb8.png)

**Insight:**
Petrol and Diesel are the top most popular fuel type used by vehicles in the dataset

####  Analysis of Predictive Power of Features

The column 'reg_code' is dropped because registration code is related to year of registration,
'public_reference' is dropped because it is just the id and has no predictive power.

The features chosen to predict the price are:
- mileage
- standard_make
- standard_model
- vehicle_condition
- year_of_registration
- body_type
- crossover_car_and_van
- fuel_type

##### mileage

![mileage_price.png](attachment:85d6dffc-6112-45dc-bcfb-84125589aad2.png)

**Insights:**
Highly priced vehicle has relatively low mileage and vice versa

##### year_of_registraion

![year_price.png](attachment:4c30abef-6331-4ee7-b5a5-d178d1e89d18.png)

#### Data Processing for Data Exploration and Visualisation

Plotly which is a python library was used to plot charts. The data in the exploration stage is not preprocessed but just assesed and analyzed using pandas and plotly.

Example of the code used to plot price distribution


`fig = px.scatter(df, y='mileage', x='price')`

`fig.update_layout(`

`    title = 'Mileage Against Price',`

`    xaxis_title = 'Price',`

`    yaxis_title = 'Mileage'`

`)`
   
`fig.show(renderer='png')`


### Data Processing for Machine Learning

####  Dealing with Missing Values, Outliers and Noise

##### Missing Values

The following featues had missing values
- mileage
- standard_color
- year_of_registration
- body_type
- fuel_type

##### 1. mileage:
> rows with missing values were dropped.

##### 2. standard_color:
> replaced missing values with most frequent color(mode)

##### 3. year_of_registration:
> - replaced values of year_of_registration where vehicle_condition is NEW with '2020'. 
> - Then we obtain other values of year_of_registration from reg_code.
> - The rows with the missing values were dropped.
> - Example  of the code for cleaning year_of_registration

> ![year_code.jpg](attachment:a1f45637-9727-4b32-90ab-e62ccb0ce2c3.jpg)


##### 4. body_type:
> - replaced values with the mode of body_type for vehicles with similar standard_make and standard_model. 
> - The rows with the missing values were dropped.

##### 5. fuel_type:
> - replaced values with the mode of fuel_type for vehicles with similar standard_make and standard_model. 
> - The rows with the missing values were dropped.

##### Outliers and Noise
Outliers are present in the following features:
- mileage
- price

##### 1. mileage:
> set cap of mileage to 200,000.

##### 2. price:
> set cap of price to 800,000.

#### Feature Engineering, Data Transformations, Feature Selection

**STEP1:** The features were seperated into predictors(x) and target(y).

The predictors(x) includes:
- mileage
- standard_make
- standard_model
- vehicle_condition
- year_of_registration
- body_type
- crossover_car_and_van
- fuel_type

The target(y):
- price(target)

**STEP2:** Using sklearn's LabelEncoder module, Label encoding was done on categorical features
- standard_make
- standard_model
- body_type
- fuel_type.

**STEP3:** One hot encoding on binary features
- vehicle_condition
- crossover_car_and_van

**STEP4:** Convert boolean column crossover_car_and_van to int using ".astype(int)"

**STEP5:** Check to make sure the datatypes are numeric.

**STEP6:** Split the data into training and testing data by calling sklearn's train_test_split module

### Model Building

#### Algorithm Selection, Model Instantiation and Configuration

##### Algorithm Selection

For this project we made use of the follwoing algorithm:
- Linear Regression Algorithm
- Random Forest Algorithm
- Extra Trees Algorithm

##### Model Instantiation and Configuration

Model instantiation and configuration follows the samae pathern.

**STEP1:** Import the algorithm from sklearn with the syntax:
- from sklearn.linear_model import LinearRegression
- from sklearn.ensemble import RandomForestRegressor, ExtraTreesRegressor

**STEP2:** Instantiate the model by assigning it to a variable, i.e.
- model = LinearRegression()
- model = RandomForestRegressor() etc.

**STEP3:** Train model by calling '.fit' on the training data, i.e.
- model.fit(x_train, y_train)

#### Grid Search, and Model Ranking and Selection

##### Grid Search

Grid Search was applied on the Random Forest Agorithm and ExtraTrees Algorithm.
The parameters searched on include:

params_grid = {
'max_depth': [25, 50],
'n_estimators': [100, 200],
'min_samples_split': [2, 5]
}

The validation was done on 5 fold i.e.
cv = 5

The evaluation metric used in scoring the parameters is R2 i.e.
scoring = r2

> For Random Forest, the best parameter:
> - {'max_depth': 25, 'min_samples_split': 2, 'n_estimators': 100}

>For Extra Trees, the best paramter:
> - {'max_depth': 25, 'min_samples_split': 5, 'n_estimators': 200}

##### Model Ranking and Selection

### Model Evaluation and Analysis

#### Visual Evaluation

![linear_reg.png](attachment:c8e3bcac-6532-4400-8512-499f7de85ec4.png)

![random_forest.png](attachment:601787b0-b785-4610-8192-44b28642e59a.png)

![extra_trees.png](attachment:a6ed4368-01e4-43e9-b28a-7788d079b6cf.png)

#### Feature Importance
Using 'model.feature_importances_' from the Extra Trees model we obtained the level of importances of each features towards prediction the price.

![feature_import.png](attachment:a7ad6de7-e577-4cd5-a966-97f5b58460fd.png)

#### Final Result

![results.jpg](attachment:8eb35b49-0870-4096-9021-5670768bea7b.jpg)

From the above results and evaluations, the ExtraTrees model is the best for prediction the price of vehicles in the dataset.
# Car-Price_Prediction
