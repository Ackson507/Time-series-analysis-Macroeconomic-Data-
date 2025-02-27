# Time-series-analysis [Macroeconomic Data]
Univariate Time Series Analysis – Inflation Rate in Zambia [CASE OF DEVELOPING COUNTRIES]📊

📌 Introdcution and Objectives of the Project.

Inflation is a key macroeconomic indicator that directly impacts economic stability, business operations, and financial decision-making at either macroeconomic or macroeconomic level. In this project, we analyze Zambia’s inflation rate using time-series techniques to uncover trends, seasonality, and irregularities. The goal of this project is to carry out Exploratory Data Analysis, Building Econometric model around inflation forecasting future inflation rates. To carry out this we use Eviews 14 as our statistical software for econometric modelling alongside with MS Excel.

## 1️⃣ Inflation Rate [January 2013 to November 2024].

- What is inflation 💡??

Inflation refers to the general increase in the price of goods and services over time, leading to a decline in the purchasing power of money. It is typically measured by the Consumer Price Index (CPI). The causes of inflation are quite a number such as Demand-pull inflation, cost-push inflation, and monetary expansion, and its effect is higher cost of living, reduced purchasing power, and increased borrowing costs.
  
- Example Interpretation of Interest Rate:

The Bank of Zambia (BoZ) has set an inflation target bound of 6-8%. As of February 21, 2025, the overnight interbank interest rate in Zambia was 14.50%. This target was achieved earlier during the study period, particularly from the 1st Quarter of 2017 to the 2nd Quarter of 2019, as shown in the green region of the graph below.

Let’s assume that during this period, the cost of a mealie meal was 120 ZMK, with an interest rate of 7.5%. As of this writing, inflation stands at 14.5%, holding other factors affecting the price of mealie meal constant. The purchasing power of the currency has decreased by 14.5%, meaning that to buy the same mealie meal, we now need: 120ZMK + (120ZMK×0.145) = 137.4 ZMK
This illustrates how inflation erodes the value of money over time, requiring more currency to purchase the same goods and services.
![inflation trend](https://github.com/user-attachments/assets/cd972a7b-0ecc-4add-8a5d-65d40e4b3658)


## 2️⃣ Insights from the Trend.

- Seasonality:

In 2015 4th quarter to 2017 first quarter is a season of interest to study what transpired and what intervention was made. During this period, we had a sudden surge increase in the inflation rate spiked as high as 22.9% and reverted to normal within this period. According to the Bank of Zambia (BoZ) data, the inflation rate in 2016 significantly declined throughout the year, peaking at around 22.9% in early 2016 and falling to single digits by the end of the year, with the average inflation rate for the second half of 2016 being around 14.5% due to base effects and a tightening monetary policy. The sudden increase was mainly due to increase in Food, drought affected agricultural output, Zambian Kwacha experienced a severe depreciation in late 2015, losing significant value against the US dollar due to:
Falling copper prices (Zambia’s main export and source of forex), Reduced foreign investment and lower inflows from mining and Increased government debt and fiscal deficits.

- Seasonality Intervention by BoZ: BoZ increased the policy rate to 15.5% in 2016, raised the Statutory Reserve Ratio (SRR), requiring commercial banks to hold more reserves and limiting their ability to lend and the central bank intervened in forex markets by selling US dollars to stabilize the Kwacha.

- Trend:  It is observable to see that during the period of 2011 4th quarter to 2015 3rd quarter, we had a constant rate of overall inflation ranging within the Bank of Zambia target of 6-8%.
  
- ### RECOMMENDATION
Since Zambia is highly dependent on imports, exchange rate depreciation fuels imported inflation. To mitigate this: Increase Foreign Exchange Reserves meaning BoZ should accumulate higher forex reserves during economic booms (when copper prices are high) to intervene more effectively during currency crises.

The Food Reserve Agency (FRA) should maintain adequate maize reserves to stabilize food prices during droughts or supply shocks which is major contributor to food inflation, and last but not least increase investment in irrigation systems, drought-resistant crops, and commercial farming to reduce dependency on rain-fed agriculture.

## 3️⃣ Initial Step to for our Modeling: Testing for stationarity using Unit Root Test
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

- 💡INTERPRETATION: ADF (Augmented Dickey-Fuller) test is a statistical method used to determine whether a time series is stationary by testing for the presence of a "unit root," which indicates non-stationarity for the raw data (at level) without applying any difference. Since our t-statistic Probality is 0.1977 which is greater than our significance level 0.05. We fail to reject NULL HYPOTHESIS, which confirms our initial assumption that the trend is Non-Stationary. This suggests that our time series has a unit root and is non-stationary at the 5% significance level. This means the series exhibits trends, seasonality, or other time-dependent structures that need to be addressed before modeling. If no modeling is involved we can end here, but since we will apply modeling techniques later in this project we will need to convert our time series to stationarity.

- 📌 How do we achive statioarity: We need to do the ADF unit root test but perform the UNIT ROOT test on first difference. We use this option since our series is non-stationary at level and we want to test whether the first differenced series is stationary.
![Screenshot 2025-02-23 222213](https://github.com/user-attachments/assets/4e355673-d436-441e-843a-59288a0c87eb)


- 💡INTERPRETATION: Since our t-statistic Probality is 0.0000 which is less than our significance level 0.05, we reject NULL HYPOTHESIS, which implies that at first difference the time series is stationary. This means our time series required one round l(1) of differencing to achieve stationarity.

## 4️⃣ Building a forecasting model.

- Additional Structure: Before  we proceed further, we need to examine the autocorrelation function (ACF) and partial autocorrelation function (PACF) of the first differenced series to identify potential AR (autoregressive) or MA (moving average) terms for an ARIMA model which will be used for forecasting and determine the appropriate ARIMA model.
ACF (Autocorrelation Function):

📊 Steps: After generating the Correlogram of Residuals (ACF and PACF plots) for the first differenced series;
![Screenshot_24-2-2025_932_](https://github.com/user-attachments/assets/9eac1182-f1bf-4539-bd1f-1683bf5e17e1)

- The ACF values start high at lag 1 (0.264) and decay slowly but remain significant up to lag 12. After lag 12, the ACF values become smaller and oscillate around zero, but some lags (e.g., lag 11, 12) remain significant. The ACF does not cut off sharply, which suggests the presence of an AR component. The PACF has a significant spike at lag 1 (0.264) and smaller spikes at lags 2 and 3. After lag 3, the PACF values become smaller and oscillate around zero, but some lags (e.g., lag 11, 12) remain significant. The PACF cuts off after lag 1, which suggests an AR(1) process.

Based on the ACF and PACF patterns: This indicates that the series likely follows an ARIMA(p, 1, q) model, where:

- p (AR term): Likely 1 or 2 (based on the PACF).
- d (differencing): 1 (since we are working with the first differenced series).
- q (MA term): Likely 0 (since the ACF does not cut off sharply).

💡Therefore, we will start with a simple ARIMA(1, 1, 0) and ARIMA(1, 1, 0) model,pick the most efficient, and refine it if necessary using AIC OR BIC process. Then we can use it for forecasting emediate future inflationary values.

![Screenshot 2025-02-25 174747](https://github.com/user-attachments/assets/464f408d-9595-4eb0-9797-de4c7632680c)


## REFERENCE:

- 1: International Monetary Fund.
https://www.imf.org/external/datamapper/NGDPDPC@WEO/ZMB?zoom=ZMB&highlight=ZMB

- 2: WORLD BANK
https://data.worldbank.org/indicator/SL.UEM.TOTL.ZS?locations=ZM

- 3: Bank of Zambia
https://www.boz.zm/statistics.htm


