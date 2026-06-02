

Saudi Arabia Inflation Forecasting: A Univariate SARIMA Approach

This repository contains an econometric time series forecasting framework built to model and project the Consumer Price Index (CPI) / Inflation (inf) for Saudi Arabia. The project applies a univariate SARIMA (Seasonal Autoregressive Integrated Moving Average) state-space architecture to isolate localized stochastic shocks and map long-term year-over-year seasonal patterns.
📊 Project Overview

Forecasting inflation is essential for macroeconomic stability, monetary policy calibration, and fiscal planning. This project focuses entirely on the intrinsic history and cyclical memory of the inflation series itself. By stripping out deterministic trends, the model establishes a clean statistical baseline for monthly price updates.
Model Specification

Optimized via automated information criteria (AIC) selection, the underlying time series engine is specified as:
SARIMA(0,1,0)×(2,0,0)12​

    Non-Seasonal Order (0,1,0): The raw level data is non-stationary and is stabilized using a single first-difference (d=1), mapping month-on-month changes. No short-term autoregressive (p=0) or moving average (q=0) terms are required, showing that isolated monthly price innovations are rapidly absorbed.

    Seasonal Order (2,0,0)12​: The model captures a powerful cyclical memory repeating every s=12 months. A second-order seasonal Autoregressive component (P=2) regresses current inflation directly onto historical performance from exactly 12 and 24 months prior.

📈 Mathematical Equation

The structural forecasting equation estimated via Maximum Likelihood Estimation (MLE) is defined as:
ΔINFt​=c+Φ1​ΔINFt−12​+Φ2​ΔINFt−24​+εt​

Where:

    ΔINFt​ represents the first-differenced inflation rate at month t (INFt​−INFt−1​).

    c is the model constant/intercept.

    Φ1​ is the first-order seasonal autoregressive coefficient (lag 12).

    Φ2​ is the second-order seasonal autoregressive coefficient (lag 24).

    εt​ is the white noise residual error term.

🛠️ Tech Stack & Methodology

    Language: Python 3.x

    Core Libraries: pandas, numpy, matplotlib, seaborn

    Econometrics: statsmodels.api (State-space models) & pmdarima (Stepwise automated grid search)

Analytical Pipeline:

    Stationarity Analysis: Augmented Dickey-Fuller (ADF) tests to evaluate unit roots and establish the integration order (d=1).

    Identification: Autocorrelation (ACF) and Partial Autocorrelation (PACF) evaluation to identify seasonal constraints.

    Estimation: Maximum Likelihood Optimization using the state-space Kalman Filter.

    Diagnostics: Checking residual properties to ensure independent, identically distributed (i.i.d.) white noise errors.

    Out-of-Sample Forecasting: Generating future path projections (Targeting 2026M04).
