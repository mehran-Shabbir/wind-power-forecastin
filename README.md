# Research-Grade Wind Power Forecasting Pipeline

An academic portfolio project focused on high-precision renewable energy forecasting using SCADA wind turbine datasets. This repository implements an end-to-end Machine Learning pipeline including rigorous data preprocessing, anomaly removal, multi-model benchmarking, feature importance extraction, and real-time live power output estimation.

---

## 📊 Project Overview
Accurate wind power prediction is essential for grid integration and power system management. This project addresses SCADA data anomalies (such as wind turbine downtime where wind speed is high but active power output drops to zero) and benchmarks multiple regression algorithms to maximize prediction accuracy.

---

## 🛠️ Technical Pipeline
1. **Data Preprocessing & Cleaning:** Filtered false operational states and turbine downtime anomalies.
2. **Feature Engineering:** Utilized key environmental and operational features (`wind_speed`, `theoretical_power`, `wind_direction`).
3. **Model Benchmarking:** Evaluated Linear Regression, Random Forest Regressor, and XGBoost Regressor using an 80/20 train-test split.
4. **Live Inference:** Built real-time power prediction capability to estimate active power generation ($kW$) based on live meteorological inputs.

---

## 📈 Performance Comparison

| Model | R2 Score (%) | RMSE (kW) |
| :--- | :---: | :---: |
| **Linear Regression** | 96.59% | 242.18 |
| **Random Forest** | 96.74% | 236.85 |
| **XGBoost** | **97.20%** | **219.59** |

* **Key Takeaway:** **XGBoost** outperformed other models, achieving a peak **R2 Score of 97.20%** and the lowest prediction error (**RMSE: 219.59 kW**).

---

## 🚀 Live Prediction Example
```python
# Real-time power output estimation using the trained XGBoost model
sample_wind_data = [[12.5, 3400.0, 180.0]]  # [Wind Speed, Theoretical Power, Wind Direction]
predicted_power = xgb_model.predict(sample_wind_data)[0]
# Output: ~3289.70 kW generated power
