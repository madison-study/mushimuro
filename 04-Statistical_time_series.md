# ARMA
- basic autoregressive model
- <img src="./resource/arma_expression.png" width="300px">

# ARIMA - Autoregressive Integrated Moving Average
- simpler model with fewer parameters to estimate
  - powerful in capturing trends and short-term dependencies in data.
- 3 key components
  - Autoregression (AR) : captures the influence of series' past values on its future values. (aka, how past values affect current value)
  - Differencing (I) : it involves subtracting a previous value from the current value, often required to achieve stationarity.
    - Stationarity refers to the statistical properties of a time series, such as its mean, variance, and autocorrelation, remaining constant over time
    - Stationarity is crucial assumption for many time series analysis
  - Moving Average (MA) : accounts for the effect of past forecast errors on the current prediction. (to improve forecast accuracy)
- Use cases
  - Financial forecasting, Demand forecasting, Economic analysis, Traffic and transportation management

# SARIMA - Seasonal Autoregressive Integrated Moving Average
- builds upon ARIMA's strengths by incorporationg seasonality.
  - beneficial for data exhibiting recurring patterns at fixed intervals
  - has additional parameters for seasonality, which makes it less flexible.
  - using techniques like grid search or statistical tests can help identify best configuration for the data (optimizing params)
- 3 key components
  - Seasonal Autoregression : similar to AR
  - Seasonal Differencing : focuses on removing seasonal patterns from the data to acheive stationarity.
  - Seasonal Moving Average : similar to MA
- Use cases
  - Retail sales forecasting, Energy consumption prediction, Weather forecasting

# ARIMAX / SARIMAX
- ARIMA + eXogenous inputs(external factors)
- used to get deeper insights and make more accurate predictions

# Vector Autoregression
- **multivariate** extension of AR models
- VAR model considers multiple variable simultaneously, unlike traditional AR models
- assumption of : linearity, stationarity
<img src="./resource/var_expression.png" width="300px">

---

### Pros of ARIMA
- Simplicity : simple to understand and implement
- Versatility : applicable in various domains

### Cons of ARIMA
- Assumption of Linearity : not always the case in real-world scenario
- Parameter selection
- Risk of overfitting (SARIMA trying to fit multiple seasonal params)

---

#### References
https://www.geeksforgeeks.org/machine-learning/arima-vs-sarima-model/  
https://www.geeksforgeeks.org/machine-learning/arima-vs-lstm/  
https://www.geeksforgeeks.org/artificial-intelligence/what-is-an-arimax-model/  
https://www.geeksforgeeks.org/machine-learning/vector-autoregression-var-for-multivariate-time-series/  

