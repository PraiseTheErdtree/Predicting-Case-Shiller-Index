# Predicting-Case-Shiller-Index
Predicting Case Shiller Index Using Publicly available data from FRED

## Introduction
The primary objective of this study is to build a model to predict the nation-wide US house prices with national
Case -Shiller Index as a reference pointer for overall house price trend.

## Publicly available Data Used :
1. Consumer Price Index CPI - https://fred.stlouisfed.org/series/CPIAUCSL
2. Unemployment rate - https://fred.stlouisfed.org/series/UNRATE
3. 30-Year Fixed Rate Mortgage - https://fred.stlouisfed.org/series/MORTGAGE30US
4. Gross Domestic Product - https://fred.stlouisfed.org/series/GDP
5. Total Unit Labor Cost - https://fred.stlouisfed.org/series/LCULMN01USQ661S
6. Personal current taxes: State and local: Property taxeshttps://fred.stlouisfed.org/series/S210401A027NBEA
7. Employment-Population Ratio - https://fred.stlouisfed.org/series/EMRATIO
8. NASDAQ Composite Index - https://fred.stlouisfed.org/series/NASDAQCOM
9. Disposable Personal Income - https://fred.stlouisfed.org/series/DSPI
10. Rental Vacancy Rate - https://fred.stlouisfed.org/series/RRVRUSQ156N
11. Monthly Supply of New Houses - https://fred.stlouisfed.org/series/MSACSR
12. New Privately-Owned Housing Units Completed -
https://fred.stlouisfed.org/series/COMPUTSA


## DATA:
The above mentioned data was imported and the date was parsed and converted to panda datetime and used as the
index of the dataframe. The time-step of the target i.e. Case shiller index is a month thus all the data is preferably
collected in this format, if the frequency of the data is higher than monthly, monthly data is used and the rest is
discarded. However if the frequency is lower than monthly. Monthly data was filled in using linear interpolation.
Quarterly data like GDP were linearly interpolated.

## Regression Approach :
Lagged features expect for the past target variable itself. This will help analyse the target variables dependence on
the lagged features (past 1 month ).
Converting Timeseries forecasting problem to Supervised Learning.:

Target feature:
Inflation adjusted National Case Shiller index was used as the target variable in the regression approach as it
showed better results than using vanilla National CS index.

Lagged feature:
All the features used in the regression analysis were lagged features all shift by two months. That is second last
month’s features were used to predict the target variable. This will allow us to predict two months into the future.
The previous value of the target variable were not used so as to better study the
impact of the factors on the Case shiller index.

## Vector autoregression:
Vector Autoregression (VAR) is a forecasting algorithm that can be used when two or more time series influence
each other. That is, the relationship between the time series involved is bi-directional

Darts Library :
Darts is a Python library for easy manipulation and forecasting of time series. It contains a variety of models, from
classics such as ARIMA to deep neural networks.
