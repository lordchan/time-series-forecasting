# Time Series Forecasting

## Project Overview

This project focuses on time series forecasting for Ad Ease, an ads and marketing company aimed at optimizing ad placements for their clients. The dataset contains daily view counts of 145k Wikipedia pages over 550 days, including pages in different languages and access types. The goal of this project is to forecast page views for different languages and optimize ad placement by predicting future trends in page views.

The models applied in this project include ARIMA, SARIMA, SARIMAX, and Facebook Prophet, achieving a Mean Absolute Percentage Error (MAPE) of 6%. The project integrates an exogenous variable for English-language pages that identifies days with significant campaigns or events, further refining the forecast.

## Problem Statement

Ad Ease helps businesses elicit maximum clicks at minimum cost by utilizing an end-to-end three-step process involving AI modules: Design, Dispense, and Decipher. In this project, the focus is to understand the page view trends on Wikipedia pages across various languages, access types, and origins. The ultimate objective is to predict page views for the upcoming days to aid in the strategic placement of ads.

### Dataset Structure:
- **Page Name**: Encoded information in the format: `PAGE_TITLE_LANGUAGE.wikipedia.org_ACCESS_TYPE_ACCESS_ORIGIN`.
- **Exog_Campaign_eng**: Exogenous variable dataset, with binary values (1 for campaign days, 0 otherwise), used for training SARIMAX on English-language pages.

### Key Concepts:
- **Exploratory Data Analysis (EDA)**
- **Time Series Forecasting** using ARIMA, SARIMAX, and Prophet
- **Evaluation Criteria**: 100 points (importing data, EDA, stationarity checks, modeling, forecast accuracy)

## Project Steps

### 1. Exploratory Data Analysis (EDA)
- Imported the dataset and examined the structure, characteristics, and null values.
- Parsed the page name format to extract `page_title`, `language`, `access_type`, and `access_origin`.
- Visualized the time series data across different languages and access types, gaining key insights into the trends.

### 2. Stationarity Checks
- Performed stationarity checks using the Dickey-Fuller test.
- Applied decomposition to extract trend, seasonality, and noise components from the series.
- Differenced the time series at level 1 to achieve stationarity, as the original series was linearly increasing.

### 3. Time Series Modeling
- **ARIMA**: Trained on individual language time series data, achieving good performance with a simple model.
- **SARIMA**: Added seasonality to ARIMA to capture periodic variations in the data.
- **SARIMAX**: Trained on the English-language data with the `Exog_Campaign_eng` exogenous variable, achieving the best MAPE results.
- **Facebook Prophet**: Used to forecast views across all time series, especially handling non-linear trends effectively.
- Implemented grid search to find the optimal model parameters.

### 4. Model Comparison
- The SARIMAX model yielded the best performance for English-language data (with exogenous campaign data).
- ARIMA was effective for languages without significant seasonality or exogenous variables.
- Prophet provided flexible forecasts across different languages, especially for non-linear trends.

### 5. Inferences from Data Visualizations
1. Most page views come from English-language Wikipedia, while patterns in other languages vary.
2. Browser agents generated over 95% of the views compared to spider agents.
3. Pages accessed via "all-access" devices had the highest views, compared to desktop or mobile.

## Results

- Achieved a MAPE of 6% across all models after tuning the parameters via grid search.
- **Average views per language**:
  - English: 5145
  - Español: 1295
  - Russian: 1036
  - German: 945
  - French: 679
  - Japanese: 802
  - Other: 166
  - Chinese: <1

### Model Performance Summary:
- **ARIMA**: Best suited for datasets without seasonality.
- **SARIMA**: Captured seasonality but struggled without exogenous data.
- **SARIMAX**: Provided optimal results when external factors (campaign data) were included.
- **Prophet**: Useful for flexible and fast forecasting, especially when non-linear trends are present.

## Decomposition of Series
Decomposed the time series into its trend, seasonality, and noise components, providing insights into long-term patterns and short-term fluctuations.

## Conclusion

This project successfully forecasted Wikipedia page views using a variety of time series models. The SARIMAX model, enhanced by an exogenous variable, delivered the best results, highlighting the importance of external factors in time series forecasting. These predictions can be leveraged to optimize ad placement strategies across different regions and languages.

---

### Technologies Used:
- **Python**: Data processing and modeling
- **Pandas, NumPy**: Data manipulation and exploration
- **Matplotlib, Seaborn**: Data visualization
- **ARIMA, SARIMA, SARIMAX**: Time series forecasting
- **Facebook Prophet**: Time series forecasting
- **Grid Search**: Model parameter optimization

## Future Work:
- Explore advanced techniques like LSTM and XGBoost for time series forecasting.
- Integrate more granular exogenous variables for non-English pages.
- Improve model performance for non-English languages with sparse data.
  
Feel free to explore the code and reach out for any questions or improvements!

---

**Author**: [Chanakya G R]  
