# 🚕 New York Taxi Fare Prediction

## 📌 Project Overview

This project focuses on predicting **taxi fare amounts** for New York City taxi trips using trip information such as pickup and drop-off locations, pickup time, passenger count, and engineered distance-based features.

The dataset contains **50,000 records and 8 original columns**. Since `fare_amount` is a continuous numerical target, this project is formulated as a **supervised regression problem**.

The project covers data exploration, feature engineering, preprocessing, regression modeling, model comparison, hyperparameter tuning, and final evaluation on unseen test data.

---

## 🎯 Objective

The main objective is to develop a regression model that can accurately estimate the fare of a taxi trip based on the available trip information.

The project also compares different regression algorithms to determine which model provides the best predictive performance.

---

## 📊 Dataset

The original dataset contains the following columns:

| Feature             | Description                         |
| ------------------- | ----------------------------------- |
| `key`               | Unique identifier for the taxi trip |
| `fare_amount`       | Target taxi fare                    |
| `pickup_datetime`   | Date and time of pickup             |
| `pickup_longitude`  | Pickup longitude                    |
| `pickup_latitude`   | Pickup latitude                     |
| `dropoff_longitude` | Drop-off longitude                  |
| `dropoff_latitude`  | Drop-off latitude                   |
| `passenger_count`   | Number of passengers                |

---

## 🔧 Feature Engineering

Several features are extracted and engineered to provide the models with more useful information.

### Date-Time Features

The `pickup_datetime` feature is expanded into:

* Year
* Month
* Day
* Weekday
* Hour

These features help capture temporal patterns in taxi fares, such as differences between weekdays, weekends, peak hours, and different periods of the year.

### Distance Feature

The **Haversine formula** is used to calculate the straight-line distance between pickup and drop-off coordinates.

This provides the model with a direct measure of trip distance, which is an important factor in estimating taxi fares.

### Landmark-Based Features

Distances from the drop-off location to several major New York landmarks are also calculated:

* JFK Airport
* LaGuardia Airport
* Newark Airport
* Metropolitan Museum
* World Trade Center

These features help capture location-based patterns that may influence taxi fares.

---

## 🗂️ Data Splitting

The dataset is split **chronologically** to better represent real-world prediction:

* **Before 2014:** Training data
* **2014:** Validation data
* **After 2014:** Test data

This approach helps evaluate how the model performs when predicting future taxi trips.

---

## 📏 Evaluation Metric

### Root Mean Squared Error (RMSE)

RMSE measures the difference between predicted and actual taxi fares while giving greater importance to larger prediction errors.

**Lower RMSE indicates better performance.**

---

## 🤖 Models

The following regression models are evaluated:

1. Mean Regressor
2. Linear Regression
3. Ridge Regression
4. Random Forest Regression
5. Gradient Boosting Regression

Hyperparameter tuning is also performed for the Gradient Boosting model using `GridSearchCV`.

---

## 📈 Model Results

| Model                   | Validation RMSE |
| ----------------------- | --------------: |
| Mean Regressor          |           11.54 |
| Linear Regression       |           11.54 |
| Ridge Regression        |            9.35 |
| Random Forest           |            5.32 |
| **Gradient Boosting**   |        **5.13** |
| Tuned Gradient Boosting |            5.28 |

The original **Gradient Boosting Regressor** provides the best validation performance with an RMSE of **5.13**.

Although hyperparameter tuning reduces the training error, the validation RMSE increases slightly to **5.28**, indicating increased overfitting. Therefore, the original Gradient Boosting model is selected as the final model.

---

## 🏆 Final Model Performance

The selected Gradient Boosting model is evaluated on the unseen test dataset.

**Final Test RMSE: 4.48**

The test RMSE is lower than the validation RMSE, indicating that the selected model performs well on the unseen test data.

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Jupyter Notebook

### Machine Learning Techniques

* Exploratory Data Analysis
* Feature Engineering
* Haversine Distance Calculation
* Date-Time Feature Extraction
* Regression
* Model Evaluation
* Hyperparameter Tuning
* GridSearchCV
* RMSE

---

## 📁 Project Structure

```text
New-York-Taxi-Fare-Prediction/
│
├── New_York_Taxi_Fare_Prediction.ipynb
├── README.md
└── dataset/
    └── taxi_fare.csv
```

---

## 🚀 Project Workflow

```text
Data Loading
     ↓
Data Exploration
     ↓
Chronological Train/Validation/Test Split
     ↓
Missing Value Handling
     ↓
Feature Engineering
     ↓
Date-Time Features
     ↓
Distance Features
     ↓
Landmark Distance Features
     ↓
Model Training
     ↓
Model Comparison
     ↓
Hyperparameter Tuning
     ↓
Final Model Selection
     ↓
Test Evaluation
```

---

## 💡 Key Findings

* Simple baseline models provide limited predictive performance.
* Ridge Regression performs substantially better than standard Linear Regression after feature engineering.
* Tree-based models capture the non-linear relationships in taxi fare data more effectively.
* Random Forest achieves a validation RMSE of **5.32**.
* Gradient Boosting performs slightly better with a validation RMSE of **5.13**.
* Hyperparameter tuning does not improve the validation performance in this experiment.
* The final Gradient Boosting model achieves a **test RMSE of 4.48**.

---

## 📌 Conclusion

The project demonstrates how **feature engineering and non-linear regression algorithms** can substantially improve taxi fare prediction. Among the tested models, Gradient Boosting provides the best validation performance and is selected as the final model. With a **test RMSE of 4.48**, the final model demonstrates good predictive performance on unseen taxi trips.
