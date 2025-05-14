# Hourly Taxi Demand Forecasting

This project was built for **Sweet Lift Taxi Company** to predict the number of taxi orders at an airport for the upcoming hour. Accurate forecasts will help the company optimize driver distribution during peak hours and reduce passenger wait times.

---

## Table of Contents

- [Objective](#-objective)
- [Dataset](#-dataset)
- [Key Steps](#-key-steps)
- [Results](#-results)
- [Visualization](#-visualization)
- [Conclusion](#-conclusion)
- [Tech Stack](#-tech-stack)
- [Folder Structure](#-folder-structure)
- [Author](#-author)

---

## Objective

> Build a predictive model to forecast hourly taxi order volume using historical data.

The model should:
- Use time series features like lag values and rolling averages
- Generalize well to unseen data
- Achieve **RMSE ≤ 48** on the test set

---

## Dataset

- Source: `taxi.csv`
- Target column: `num_orders`
- Frequency: Hourly timestamps over ~6 months

---

## Key Steps

1. **Data Cleaning & Exploration**
   - Handled missing values (no duplicates dropped)
   - Verified time index integrity (no missing hours)
   - Analyzed trends, seasonality, and distribution

2. **Feature Engineering**
   - Extracted calendar features (`hour`, `dayofweek`)
   - Generated 24 lag features
   - Computed 24-hour rolling mean

3. **Model Training & Validation**
   - Linear Regression
   - Random Forest
   - Gradient Boosting (default + tuned)
   - XGBoost

4. **Hyperparameter Tuning**
   - Grid search on Gradient Boosting and Random Forest
   - Validation split used to avoid test leakage

5. **Final Evaluation**
   - Best model retrained on full training data
   - Evaluated once on test set

---

## Results

| Model                   | Validation RMSE | Test RMSE |
|--------------------------|------------------|------------|
| Tuned Random Forest      | **32.80**         | **43.68**  
| Linear Regression        | 33.04             | —  
| Tuned Gradient Boosting  | 33.12             | —  
| XGBoost                  | 33.46             | —  

---

## Visualization

The final tuned Random Forest model tracked daily demand cycles well and reacted reasonably to spikes. A 7-day slice of the test set confirmed the model’s forecasting accuracy.

---

## Conclusion

- The model met the business requirement (RMSE < 48)
- Random Forest was the most robust performer across both validation and test sets
- Feature engineering and proper validation strategy were key to success

---

## Tech Stack

- Python 3
- pandas, NumPy
- matplotlib, seaborn
- scikit-learn
- XGBoost
- statsmodels
