Bike Sharing Demand Forecasting using SARIMA and SARIMAX

Objective: Forecast short-term hourly bike rental demand using statistical time-series models and evaluate the impact of weather and calendar variables.

Dataset: UCI Bike Sharing Dataset (hour.csv); target variable is cnt (hourly rentals).

Environment Setup: Used pandas, numpy, matplotlib, seaborn, statsmodels (SARIMAX), and sklearn metrics; warnings suppressed and plotting style configured.

Data Preparation: Loaded dataset from ZIP file, converted date to datetime, constructed timestamp index, sorted chronologically, and extracted cnt as the target series.

Train-Test Split: Time-based split with 90 percent training data (15641 observations) and 10 percent testing data (1738 observations).

Exploratory Analysis: Identified long-term upward trend, strong daily seasonality (24-hour cycle), and clear commuter peaks; selected seasonal period s = 24.

Stationarity Handling: Applied first-order differencing (d=1) and seasonal differencing at lag 24 (D=1).

ACF and PACF Analysis: Lag 1 spikes suggested AR(1) and MA(1); seasonal spikes at lag 24 supported seasonal AR and MA terms.

SARIMA Model: Implemented SARIMA(1,1,1)(1,1,1,24) using SARIMAX class without exogenous variables; all AR and MA terms statistically significant.

SARIMA Performance: MAE 281.40, RMSE 343.61, MAPE 15.33 percent; model captures temporal structure but struggles during volatile periods.

SARIMAX Extension: Added exogenous features temp, hum, windspeed, workingday, and holiday to account for external demand drivers.

SARIMAX Results: Temperature and humidity showed statistical significance; model achieved MAE 258.68, RMSE 315.27, MAPE 13.26 percent.

Model Comparison: SARIMAX consistently outperformed SARIMA, demonstrating improved predictive accuracy when incorporating weather and calendar variables.

Interpretation: Demand is influenced not only by past rentals but also by environmental and calendar factors; errors increase during extreme weather and holidays.

Conclusion: Time-series models can effectively forecast hourly bike demand; SARIMAX provides superior performance by integrating exogenous variables, making it more suitable for operational forecasting in bike-sharing systems.


Key Terms:

Time-Series Properties: Non-stationary series with deterministic trend and strong 24-hour seasonality.

Transformation: Applied first-order differencing (d = 1) and seasonal differencing (D = 1, s = 24) to achieve stationarity.

Model Identification: Used ACF (Autocorrelation Function) and PACF (Partial Autocorrelation Function) plots to determine AR and MA orders.

Model Structure: SARIMA (Seasonal AutoRegressive Integrated Moving Average) (1,1,1)(1,1,1,24).

SARIMA Performance: Evaluated using MAE (Mean Absolute Error), RMSE (Root Mean Squared Error), and MAPE (Mean Absolute Percentage Error); MAPE 15.33 percent.

SARIMAX Extension: SARIMAX (Seasonal AutoRegressive Integrated Moving Average with eXogenous variables) incorporated temperature, humidity, windspeed, workingday, and holiday.

SARIMAX Performance: Achieved improved MAPE 10.52 percent, demonstrating better predictive accuracy.

Key Insight: Temperature and calendar effects significantly influence hourly demand.

Conclusion: SARIMAX outperforms SARIMA by modeling both  exogenous demand drivers.
