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

## 3️⃣ Initial Step for our Modeling: Testing for stationarity using Unit Root Test
Many economic and financial time series (e.g., inflation, GDP, stock prices) are non-stationary because they exhibit trends, seasonality, or other time-dependent structures. Non-stationary data can lead to
Spurious Regression. A time series is stationary if its statistical properties (mean, variance, and autocorrelation) remain constant over time, this is a key assumption in many time series models (e.g., ARIMA, VAR) because:
- Ensures that the relationships between variables are stable over time and it simplifies modeling and forecasting.
  
- By differencing Inflation data, we will ensure that the time series meets the stationarity assumption.
  ![differenced](https://github.com/user-attachments/assets/72e8596c-9e59-4131-9e79-532d8b1b45f9)


We can assume stationarity because the mean seem to revolve on a costant mean zero, but to confirm we need to test at 5% Significance level. Setting up our Hypothesis of unit root test we have that;
- Null Hypthesis: INFLATION HAS A UNIT ROOT
- Alternative Hypothesis: NO UNIT ROOT
  
![Screenshot 2025-02-27 103743](https://github.com/user-attachments/assets/4c44256b-73a2-43b7-b9ba-9e7e3afdb834)

- 💡INTERPRETATION:

ADF (Augmented Dickey-Fuller) test is a statistical method used to determine whether a time series is stationary by testing for the presence of a "unit root," which indicates non-stationarity. At level (Raw Data) we failed to reject  Null Hypothesis because our t-statistic is 0.0753 greater than our significance level meaning original data was non-stationary as ealier assumed. Since our t-statistic Probality is 0.0000 which is less than our significance level 0.05 when we take first-difference the data, this suggests that our time series has a no unit root and is stationary at the 5% significance level.

## 4️⃣ Modeling: Testing for Autocorrelation.

- Additional Structure: Before  we proceed further, we need to examine the autocorrelation function (ACF) and partial autocorrelation function (PACF) of the first differenced series to identify potential AR (autoregressive) or MA (moving average) terms for an ARIMA model which will be used for forecasting and determine the appropriate ARIMA model.
ACF (Autocorrelation Function):

📊 Steps: After generating the Correlogram of Residuals (ACF and PACF plots) for the first differenced series;
![Screenshot 2025-02-27 105417](https://github.com/user-attachments/assets/5dad2116-851e-46ed-a8eb-a6cd6f113348)

- 💡INTERPRETATION:

The ACF values start high at lag 1 (0.264) and decay slowly but remain significant up to lag 12. After lag 12, the ACF values become smaller and oscillate around zero, but some lags (e.g., lag 11, 12) remain significant. The ACF does not cut off sharply, which suggests the presence of an AR component. The PACF has a significant spike at lag 1 (0.264) and smaller spikes at lags 2 and 3. After lag 3, the PACF values become smaller and oscillate around zero, but some lags (e.g., lag 11, 12) remain significant. The PACF cuts off after lag 1, which suggests an AR(1) process.

Based on the ACF and PACF patterns: This indicates that the series likely follows an ARIMA(p, 1, q) model, where:

- p (AR term): Likely 1 or 2 (based on the PACF).
- d (differencing): 1 (since we are working with the first differenced series).
- q (MA term): Likely 0 (since the ACF does not cut off sharply).

Therefore, we will start with a simple ARIMA(1, 1, 0) and ARIMA(1, 1, 0) model, pick the most efficient, and refine it if necessary using AIC OR BIC process before doing any forecast in the next project.

## REFERENCE:

- 1: International Monetary Fund.
https://www.imf.org/external/datamapper/NGDPDPC@WEO/ZMB?zoom=ZMB&highlight=ZMB

- 2: WORLD BANK
https://data.worldbank.org/indicator/SL.UEM.TOTL.ZS?locations=ZM

- 3: Bank of Zambia
https://www.boz.zm/statistics.htm


