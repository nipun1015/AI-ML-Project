# Predicting Server CPU Temperature using Machine Learning

## Overview

This project uses **Machine Learning regression models to predict server CPU temperature** from system performance parameters. The goal is to predict temperature changes in advance and support **proactive cooling management**, reducing overheating risks, energy consumption, and potential hardware damage.

## Problem Statement

Servers can generate high heat during heavy workloads, which may lead to hardware damage and reduced performance. Traditional cooling systems generally react after temperature reaches a fixed threshold. This project aims to predict CPU temperature before overheating occurs, enabling proactive cooling decisions.

## Dataset

The dataset contains **14,967 rows and 7 columns**.

The main input parameters include:

* CPU Utilization
* Memory Usage
* Clock Speed
* Ambient Temperature
* Voltage
* Current

**Target:** `Temperature`

## Data Preprocessing

The following preprocessing steps were performed:

* Handled missing numerical values using mean imputation.
* Created additional features:

  * `Power_Load = Voltage × Current`
  * `Workload = CPU_Utilization × Memory_Usage`
* Removed outliers using the **IQR method**.
* Split the data into **70% training and 30% testing** sets.
* Applied **StandardScaler** for feature normalization.

## Machine Learning Models

Three regression models were developed and compared:

1. **Linear Regression** – Used as a baseline model.
2. **Decision Tree Regression** – Captures non-linear relationships between system parameters and temperature.
3. **Random Forest Regression** – An ensemble of decision trees designed to improve prediction accuracy and stability.

## Results

| Model             |  R² Score |     RMSE |
| ----------------- | --------: | -------: |
| Linear Regression |     0.683 |    11.70 |
| Decision Tree     |     0.834 |     7.40 |
| **Random Forest** | **0.963** | **3.46** |

Random Forest achieved the best performance, with an **R² score of 0.963** and **RMSE of 3.46**.

5-fold cross-validation also showed that Random Forest provided the most stable performance among the three models.

## Conclusion

The project successfully developed a regression-based Machine Learning system for predicting server CPU temperature. **Random Forest performed best** among the tested models and can be used as a foundation for proactive server cooling and overheating prevention.

## Future Scope

* Real-time temperature prediction using live server data.
* Integration with IoT sensors for automated cooling control.
* Experimentation with advanced models such as XGBoost and Deep Learning.
* Deployment in cloud-based server monitoring systems.
