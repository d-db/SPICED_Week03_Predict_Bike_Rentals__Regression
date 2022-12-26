# SPICED Week03: Predicting the amount of rented bikes using a regression model

## Project Summary

In this project I built and trained a regression model on the [Capital Bike Share (Washington, D.C.)](https://www.kaggle.com/c/bike-sharing-demand/data) data set, in order to predict demand for bicycle rentals at any given hour, based on time and weather, e.g.:
“Given the forecasted weather conditions, how many bicycles can we expect to be rented out (city-wide) this Saturday at 2pm?”

Steps to achive the desired goal:
- split the data into a training and validation set and create time related features
- conduct an exploratory data analysis
- train a regression model
- iteratively optimize the model by expanding or selecting features
- regularize the model to avoid overfitting
- calculate a RMSLE for the training and validation set

The competition on Kaggle was already closed, but I submitted my result anyway and ended up with a decent result:

![latest](https://user-images.githubusercontent.com/61935581/209571550-3ebe0669-caf1-4551-990d-9de03e73c1d4.png)

## Project Milestones

### 1_WP_EDA.ipynb

Plot total count against season and year

![Bildschirmfoto 2022-12-26 um 18 29 32](https://user-images.githubusercontent.com/61935581/209571825-784ec278-d51c-40f3-adee-1a6eb2ab1d40.png)

- There is an overall trend towards higher usage over the observed period
- There are usually low "count" numbers in winter
- Highest "count" numbers are archieved in spring and summer

Plot temperature against count depending on season

![Bildschirmfoto 2022-12-26 um 18 31 11](https://user-images.githubusercontent.com/61935581/209571914-57c37367-f2d6-40f0-9a23-d4b03be416f2.png)

- High "count" numbers are especially achieved in spring and summer
- Low "count" numbers are recoreded in winter

Plot season against count and distinguish depending on weather

![Bildschirmfoto 2022-12-26 um 18 32 45](https://user-images.githubusercontent.com/61935581/209571959-16346196-8db5-47f6-aadf-e5778e9355ea.png)

- Especially in spring good weather affects the amount of rented bikes
- In summer and autumn the the difference between weather condition 1 and 2 is not very big
- Weather condition 3 results in every season in a much lower amount of rented bikes

Plot count against datetime.hour and distinguish depending on season

![Bildschirmfoto 2022-12-26 um 18 33 41](https://user-images.githubusercontent.com/61935581/209572010-0fa6a553-1a02-42dd-9fa1-5e917d6a009f.png)

- Highest “count” values are reached at 8:00 and between 17:00 - 19:00
- Lowest values are recorded between 9:00 and 11:00

Which factors contribute most to the number of bicycles being checked out over the course of a given day?

- Weather
- Season (month)
- Time of the day

### 2_WP_RegressionModel.ipynb

Apply a data preprocessing pipeline

![Bildschirmfoto 2022-12-26 um 18 35 45](https://user-images.githubusercontent.com/61935581/209572148-db53f107-bd24-4e46-ba44-39ee64cccf2a.png)

- Use FunctionTransformer() to apply a custom function
- Use StandardScaler() on numeric features
- Use OneHotEncoder(handle_unknown="ignore") on categorical features

Using np.log1p in order to avoid negative numbers and train the model

![Bildschirmfoto 2022-12-26 um 18 39 56](https://user-images.githubusercontent.com/61935581/209572370-ab187e70-70cc-42ff-8bef-7144a489bd98.png)

- R2 score of the model is 0.89

### 4_WP_Feature_Expansion.ipynb

Usage of 'Feature Expansion' on particular features ('atemp', 'hour') did not improve the R2 score.

### 5_WP_HP_Optimization.ipynb

Usage of 'Hyperparameter Optimization' through CrossValidation and GridSearch did not improve the R2 score.

## License

[MIT](https://choosealicense.com/licenses/mit/)
