# Time-series-analysis [Macroeconomic Data]
Univariate Time Series Analysis – Inflation Rate in Zambia [CASE OF DEVELOPING COUNTRIES]📊

📌 Introdcution and Objectives of the Project.

Inflation is a key macroeconomic indicator that directly impacts economic stability, business operations, and financial decision-making. In this project, we analyze Zambia’s inflation rate using time-series techniques to uncover trends, seasonality, and irregularities. The goal in this project is to forecast future inflation rates and evaluate economic impact , particularly for Small and Medium Enterprises (SMEs) borowing capacity and influence with other macroeconomic indicators. To carry out this we use entirely utilize Eviews as our statistical software for Statistical analysis and visualization.

1️⃣ Explore and visualize trends in a key macroeconomic variable (Inflation Rate).
- What is inflation 💡?? Inflation refers to the general increase in the price of goods and services over time, leading to a decline in the purchasing power of money. It is typically measured by the Consumer Price Index (CPI). The causes of inflation are quite a number such as Demand-pull inflation, cost-push inflation, monetary expansion, and its effect is higher cost of living, reduced purchasing power, increased borrowing costs. In zambia, inflation is measure at National and provincial level, we will look at Total, Non-Food and Food Inflation from January 2011 upto January 2025. 

Let us visualize these trends and cary out descriptive statistics for all three inflation categories. Data is already in foreign file [xlsv] we need to import in Eview to begin the analysis.

![trend](https://github.com/user-attachments/assets/7c044b4c-b2ac-4b1c-baa4-6a3a23032b14)


2️⃣ Insights from the Trend.

- Seasonlity
- Trend
  
3️⃣ Testing for stationarity using Unit Root Test
Many economic and financial time series (e.g., inflation, GDP, stock prices) are non-stationary because they exhibit trends, seasonality, or other time-dependent structures. Non-stationary data can lead to
Spurious Regression. A time series is stationary if its statistical properties (mean, variance, and autocorrelation) remain constant over time, this is a key assumption in many time series models (e.g., ARIMA, VAR) because:
- Ensures that the relationships between variables are stable over time.
- It simplifies modeling and forecasting.
  
- By differencing Total Inflation data, we will ensure that the time series meets the stationarity assumption. Below is the visual differenced Total Inflation;
  ![differenced total inflation](https://github.com/user-attachments/assets/8ce139e8-db48-4af6-a264-28f088f888a7)

- As seen above after differencing, we can assume stationarity because the mean seem to revolve on a costanttly by Zero, but to confirm we need to test at 5% Significance level. Setting up our Hypothesis of unit root test we have that; 
- NULL HYPOTHESIS: Total Inflation is Stationery
- ALTERNATIVE HYPOTHESIS: REJECT THE NULL HYPOTHESIS
![Screenshot_23-2-2025_1763_](https://github.com/user-attachments/assets/b7d85697-c70e-4b2f-a779-e6def6cb9a43)
- Using ADF to test for UNIT ROOT we have the following result above.

- 💡INTERPRETATION: ADF (Augmented Dickey-Fuller) test is a statistical method used to determine whether a time series is stationary by testing for the presence of a "unit root," which indicates non-stationarity for the raw data (at level) without applying any difference. Since our t-statistic Probality is 0.1977 which is greater than our significance level 0.05. We fail to reject NULL HYPOTHESIS, which confirms our initial assumption that the trend is Non-Stationary.This suggests that our time series has a unit root and is non-stationary at the 5% significance level. This means the series exhibits trends, seasonality, or other time-dependent structures that need to be addressed before modeling. If no modelling is involved we can end here, but since we will apply  modelling techniques later in this project we will need to convert our time series to stationarity.

- 📌 How do we achive statioarity: We need to do the ADF unit root test but perform the UNIT ROOT test on first difference. We use this option since our series is non-stationary at level and we want to test whether the first differenced series is stationary.
![Screenshot 2025-02-23 222213](https://github.com/user-attachments/assets/4e355673-d436-441e-843a-59288a0c87eb)


- 💡INTERPRETATION: Since our t-statistic Probality is 0.0000 which is less than our significance level 0.05, we reject NULL HYPOTHESIS, which implies that at first difference the time series is stationary. This means our time series required one round l(1) of differencing to achieve stationarity.

4️⃣ Building a forecasting model.

- Additional Structure: Before  we proceed further, we need to examine the autocorrelation function (ACF) and partial autocorrelation function (PACF) of the first differenced series to identify potential AR (autoregressive) or MA (moving average) terms for an ARIMA model which will be used for forecasting and determine the appropriate ARIMA model.
ACF (Autocorrelation Function):

📊 Steps: After generating the Correlogram of Residuals (ACF and PACF plots) for the first differenced series;
![Screenshot_24-2-2025_932_](https://github.com/user-attachments/assets/9eac1182-f1bf-4539-bd1f-1683bf5e17e1)

- The ACF values start high at lag 1 (0.264) and decay slowly but remain significant up to lag 12. After lag 12, the ACF values become smaller and oscillate around zero, but some lags (e.g., lag 11, 12) remain significant. The ACF does not cut off sharply, which suggests the presence of an AR component. The PACF has a significant spike at lag 1 (0.264) and smaller spikes at lags 2 and 3. After lag 3, the PACF values become smaller and oscillate around zero, but some lags (e.g., lag 11, 12) remain significant. The PACF cuts off after lag 1, which suggests an AR(1) process.

Based on the ACF and PACF patterns: This indicates that the series likely follows an ARIMA(p, 1, q) model, where:

- p (AR term): Likely 1 or 2 (based on the PACF).
- d (differencing): 1 (since we are working with the first differenced series).
- q (MA term): Likely 0 (since the ACF does not cut off sharply).

💡Therefore, we will start with a simple ARIMA(1, 1, 0) model and refine it if necessary using AIC OR BIC process.

  
5️⃣ Evaluate economic implications on:
- SME's [Small and Medium Enterprises] and Purchasing Power of the Currency
