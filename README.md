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
  
3️⃣ Testing for stationarity first and secondly Unit Root
Many economic and financial time series (e.g., inflation, GDP, stock prices) are non-stationary because they exhibit trends, seasonality, or other time-dependent structures. Non-stationary data can lead to
Spurious Regression, thus we need to difference it. A time series is stationary if its statistical properties (mean, variance, and autocorrelation) remain constant over time, this is a key assumption in many time series models (e.g., ARIMA, VAR) because:
- Ensures that the relationships between variables are stable over time.
- It simplifies modeling and forecasting.

  
- By differencing, we ensure that your time series meets the stationarity assumption, leading to more reliable and interpretable models. Below is the visual differenced total inflation;
  ![differenced total inflation](https://github.com/user-attachments/assets/8ce139e8-db48-4af6-a264-28f088f888a7)

- As seen above, we can assume stationarity, but to confirm we need to test at 5% Significance level.

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
