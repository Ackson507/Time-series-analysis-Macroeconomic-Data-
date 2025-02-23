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

- As seen above after differencing, we can assume stationarity because the mean seem to revolve on a costanttly by Zero, but to confirm we need to test at 5% Significance level.Setting up our Hypothesis of unit root test we have that; 
- NULL HYPOTHESIS: Total Inflation is Stationery
- ALTERNATIVE HYPOTHESIS: REJECT THE NULL HYPOTHESIS
![Screenshot_23-2-2025_1763_](https://github.com/user-attachments/assets/b7d85697-c70e-4b2f-a779-e6def6cb9a43)
- Using ADF to test for UNIT ROOT we have the following result above.

- 💡INTERPRETATION:An ADF (Augmented Dickey-Fuller) test is a statistical method used to determine whether a time series is stationary by testing for the presence of a "unit root," which indicates non-stationarity. Since our t-statistic Probality is 0.1977 which is greater than our significance level 0.05. We fail to reject NULL HYPOTHESIS, which confirms our initial assumption that the trend is Non-Stationary.This suggests that our time series has a unit root and is non-stationary at the 5% significance level. This means the series exhibits trends, seasonality, or other time-dependent structures that need to be addressed before modeling.

4️⃣ Building a forecasting model
- In particular (ARIMA) model to predict future values.The AutoRegressive Integrated Moving Average (ARIMA) model is a powerful tool for inflation forecasting.

📊 Steps:
- Identify optimal parameters (p, d, q) using ACF/PACF plots.

- Train ARIMA model on historical inflation data.

- Evaluate forecasting accuracy using RMSE and MAPE.

- Generate inflation forecasts for the quater 4 months of 2025.
  
5️⃣ Evaluate economic implications on:
- SME's [Small and Medium Enterprises
- Overal Wages.
