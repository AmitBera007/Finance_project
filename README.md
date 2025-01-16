# Predictive Hedging Strategies Using LSTM for Automated Trading

This project explores predictive hedging strategies using Long Short-Term Memory (LSTM) models for automated trading. By leveraging time-series forecasting and technical indicators, the framework provides actionable BUY, SELL, and HOLD decisions to optimize trading strategies.

## Introduction
Financial markets exhibit high volatility and non-linear patterns, which traditional methods like ARIMA and GARCH struggle to model effectively. LSTM models, designed to capture these complexities, excel in time-series forecasting.

## Objectives:
1. Accurately forecast stock Close Prices.
2. Generate robust trading signals (BUY, SELL, HOLD) to inform hedging strategies.

## Data Preprocessing
- **Data Source**: Daily stock data for SBI.
- **Steps**:
  - Handled missing values (forward/backward fill).
  - Removed duplicates.
  - Standardized numerical features: `Open`, `High`, `Low`, `Close`, `Volume`.
  - Engineered features:
    - Rolling mean and standard deviation (7-day window).
    - Lagged Close Prices (`lag1`).
    - Day-of-week indicator.


## Exploratory Data Analysis
- Analyzed feature distributions, time-series trends, and autocorrelations.
- Visualized relationships using:
  - Correlation Matrix
  - Trend and Seasonality Decomposition
  - Moving Averages
  - RSI, Bollinger Bands, and MACD Charts.


## Derived Trading Strategies
### Key Indicators:
1. **Bollinger Bands**: Trend reversals.
2. **RSI**: Overbought/oversold signals.
3. **MACD**: Momentum signals.
4. **Moving Averages**: Short- and long-term trends.
5. **Volume Analysis**: Breakout confirmations.

### Combined Strategy:
By integrating these indicators, we achieve robust trading signals, reducing false positives.


## Feature Selection
### Methods:
- Correlation Analysis
- Recursive Feature Elimination (RFE)
- Mutual Information

### Final Features:
`lag1 close`, `Lower Bollinger Band`, `rolling mean close`, `High`, `Open`, `Upper Bollinger Band`, `wk close`, `Low`.


## LSTM Model Development
- **Input Sequence Length**: 50 days.
- **Tuning**:
  - LSTM Units: 32-128
  - Dropout: 0.2-0.5
  - Learning Rates: 0.001, 0.0001
- **Performance**:
  - RMSE: 0.1097
  - MAE: 0.0804
  - MAPE: 11.66%
- **Output**: Predicted Close Prices.


## Trading Signal Generation
Change = (P̂t - Pt-1) / Pt-1

### Signals:
- **BUY**: Change > 1%
- **SELL**: Change < -1%
- **HOLD**: Otherwise


## Conclusion and Future Work
- **Achievements**:
  - Accurate price trend forecasting.
  - Actionable trading signals with strong performance metrics.

- **Future Work**:
  - Integrate macroeconomic indicators and sentiment analysis.
  - Develop ensemble models.
  - Deploy in a real-time trading environment.
  - Explore blockchain-based smart contracts for automation.
