# 🍔 Food Delivery Demand Prediction System

## Problem Statement
Food delivery platforms must accurately anticipate customer demand to ensure efficient rider allocation, reduce delivery delays, and optimize operational costs. Poor demand estimation can lead to rider shortages, excess idle capacity, and customer dissatisfaction.

This project aims to **forecast daily food order demand across delivery zones** by analyzing historical order data, temporal patterns, and weather conditions. The objective is to support **data-driven planning and operational decision-making** for food delivery services.

---

## Objective

- Analyze past food order trends  
- Identify peak demand times and locations  
- Understand factors affecting order volume  
- Predict future food delivery demand  

---

## Tools and Technologies Used
- **Programming Language:** Python  
- **Libraries:**  
  - Pandas, NumPy (data cleaning and processing)  
  - Matplotlib (visualization)  
  - Scikit-learn (machine learning models and evaluation)  
  - Meteostat (weather data integration)  
- **Dataset:** Kaggle Food Delivery Order History Dataset  
- **External Data:** Historical weather data (temperature, rainfall, wind speed)

---

## Dataset Description

The dataset contains historical records of food delivery orders including:

- Order timestamps  
- Delivery zones or locations  
- Restaurant categories  
- Order counts or volumes  
- Other operational features affecting demand  

Each row represents food delivery activity during a specific time period and area.

---

## Project Workflow / Methodology

### 1. Data Loading and Initial Exploration
- Loaded historical food order data from CSV files.
- Examined dataset structure, dimensions, data types, and summary statistics.
- Identified missing values and duplicate records.

### 2. Data Cleaning and Preprocessing
- Dropped irrelevant and high-missing-value columns such as reviews, discounts, and complaints.
- Filled missing numerical values using median imputation.
- Converted order timestamps into proper datetime format.
- Extracted date-level information for time-series aggregation.

### 3. Zone Standardization
- Cleaned and standardized delivery zone names to ensure consistency.
- Removed formatting inconsistencies such as extra spaces, symbols, and case differences.

### 4. Demand Aggregation
- Aggregated order data to compute **daily order counts per zone**.
- Performed basic validation to confirm date ranges, zone counts, and record consistency.

### 5. Weather Data Integration
- Retrieved daily weather data (temperature, rainfall, wind speed) using Meteostat.
- Cleaned and selected relevant weather variables.
- Merged weather data with daily demand data.
- Created rainfall and heat indicators relevant to local climate conditions.

### 6. Feature Engineering
- Generated calendar-based features to capture seasonality:
  - Day of week, month, weekend indicator
- Created lag-based demand features:
  - Previous day demand (lag-1)
  - Demand from 7 days ago (lag-7)
- Computed rolling averages to capture short-term trends.
- Handled missing values caused by lag and rolling operations.

### 7. Zone Selection and Dataset Preparation
- Identified high-demand zones based on total order volume.
- Created zone-specific datasets for focused modeling.
- Defined input features and target variable (daily orders).

### 8. Model Development
- Applied time-based train-test split to preserve temporal order.
- Built and evaluated multiple models:
  - Baseline Lag Model
  - Linear Regression
  - Decision Tree Regressor
  - Random Forest Regressor

### 9. Model Evaluation and Comparison
- Evaluated models using **Mean Absolute Error (MAE)** and **Root Mean Squared Error (RMSE)**.
- Compared model performance visually and numerically.
- Visualized actual vs predicted demand trends for selected zones.

### 10. Forecast Generation
- Generated demand forecasts for **all delivery zones** using Random Forest.
- Created a **next-day demand forecast file** for operational planning.
- Saved final datasets and forecast outputs for reproducibility.

---

## Results
- Accurate daily demand forecasts at the zone level.
- Random Forest consistently outperformed baseline and simpler models.
- Weather and lag-based features significantly improved prediction accuracy.
- Generated output files:
  - `final_df_model.csv`
  - `all_zones_demand_forecast.csv`
  - `next_day_zone_forecast.csv`

---

## Key Learnings and Conclusion
- Demand forecasting benefits strongly from lag and rolling-window features.
- Weather conditions influence food ordering behavior and should be incorporated.
- Time-based train-test splits are essential for realistic forecasting.
- Ensemble models like Random Forest handle non-linear demand patterns effectively.
- This project demonstrates how data analytics can enhance operational efficiency in food delivery platforms.


## 🚀 Future Improvements

- Use time-series forecasting models (ARIMA, Prophet, LSTM)  
- Include weather and festival data  
- Real-time demand monitoring dashboard  
- City-level and restaurant-level demand prediction  

---
