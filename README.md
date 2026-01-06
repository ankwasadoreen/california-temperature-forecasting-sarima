Time Series Analysis and Forecasting of Monthly Average Temperature in California Using SARIMA 

# Project Overview

This project analyzes and forecasts monthly average temperatures in California using historical NOAA NCEI ClimGrid data spanning 1895–2023.

The study focuses on identifying long-term trends, seasonal patterns, and stationarity, and evaluates the performance of SARIMA time series models for short- and medium-term forecasting. A classical Simple Exponential Smoothing (SES) model is included as a baseline for comparison.

# Objective

The objectives of this study are to:

Analyze trends and seasonality in California’s monthly temperature series

Test and achieve stationarity using appropriate differencing

Fit and compare SARIMA models based on information criteria and diagnostics

Produce temperature forecasts for the next 36 months

Evaluate forecast reliability and uncertainty

# Data Description

Source: NOAA NCEI ClimGrid

Variable: Monthly average temperature (°C)

Time Span: 1895–2023

Frequency: Monthly

Spatial Scope: California

Why California?

Clear and stable annual seasonality

Policy relevance (climate, energy, agriculture)

Lower noise compared to national aggregates

Long, complete historical record

# Exploratory Data Analysis & Stationarity

Initial analysis shows that;

Strong annual seasonality

A gradual long-term warming trend

Stationarity Tests

Two complementary tests were applied:

Augmented Dickey–Fuller (ADF): tests for unit roots

KPSS: tests for stationarity

Results indicated non-stationarity in the original series.

Differencing Strategy

First-order differencing → removes trend

Seasonal differencing (lag = 12) → removes annual seasonality

After differencing:

ADF test: p < 0.05 → stationary

KPSS test: p > 0.05 → stationary

The series was therefore suitable for SARIMA modeling.

# Model Selection & Fitting

ACF and PACF diagnostics suggested:

Non-seasonal AR terms

Strong seasonal AR components at lag 12

Automatic model selection using auto.arima() (AICc criterion) and manual diagnostics led to evaluation of multiple candidate models.

#  Final Model Selection

The final selected model is:

SARIMA(2,0,0)(2,1,0)[12] with drift

Reasons for Selection

Lowest AICc

Clear interpretability of autocorrelation structure

Stable parameter estimates

Consistency with ACF and PACF diagnostics

Strong representation of annual seasonality and long-term trend

# Forecasting (Next 36 Months)

Forecast horizon: 36 months

Short-term forecasts (≤12 months) show higher reliability

Long-term forecasts exhibit widening confidence intervals

Forecast Characteristics

Seasonal peaks: May–July

Seasonal troughs: January–February

Gradual upward drift consistent with warming trends

Increasing uncertainty with forecast horizon

# Model Diagnostics

Residuals are approximately zero-mean and homoskedastic

Residual ACF shows mostly insignificant autocorrelations

Ljung–Box test indicates some remaining dependence, which is common in climate time series

No evidence of major model misspecification

Overall diagnostics confirm that the model captures the dominant temporal structure.

# Comparison with Simple Exponential Smoothing

Simple Exponential Smoothing (SES) was included as a baseline classical model.

Findings

SES assumes no trend or seasonality

Forecasts converge toward a constant mean

Fails to capture annual temperature cycles

# Conclusion

SARIMA significantly outperforms SES by explicitly modeling:

Seasonal differencing (D = 1, s = 12)

Short-term autocorrelation

Long-term behavior via drift

#  Model Performance

RMSE: 1.62

MAPE: 32%

The relatively high MAPE reflects the small absolute scale of temperature values. Performance is appropriate for climate trend analysis rather than high-precision short-term prediction.

#  Key Findings

California temperatures exhibit strong and consistent annual seasonality

Seasonal differencing is essential for stationarity

SARIMA models effectively capture temperature dynamics

Short-term forecasts are more reliable than long-term projections

Forecast uncertainty increases with horizon length

# Limitations

Assumes linear trend and seasonality

Does not capture abrupt structural or nonlinear climate shifts

Long-term forecasts have high uncertainty

#  Future Work

Incorporate external climate drivers (ENSO, global anomalies)

Explore hybrid or ensemble time series models

Extend to regional or county-level analysis

Compare with machine learning–based forecasting approaches

#  Tools & Technologies

Language: R

Methods: Time series analysis, SARIMA, exponential smoothing

Techniques: Stationarity testing, differencing, ACF/PACF diagnostics
