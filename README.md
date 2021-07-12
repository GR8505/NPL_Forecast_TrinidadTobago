# NPL_Forecast_TrinidadTobago
Using Predictive Analytics to forecast Non-Performing Loans Ratio in Trinidad and Tobago

----------------------------------------------------------------------------------------
## Executive Overview








---------------------------------------------------------------------------------------

## Model 1 - Backward Selection Process
**From**: _lm(NPL ~ GDP + U_RATE + CPI + CR_GROWTH + M2 + O_PROD + CEM_SALES + N_GAS + X_RATE + N_RESV + WTI + WA_LR + PRIME)_ 

**To**:   _lm(NPL ~ GDP + U_RATE + CR_GROWTH + M2 + CEM_SALES + X_RATE + WTI + WA_LR)_



### Regression Diagnostics ###

**Summary**

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Summary.png)
----------------------------------------------------------------------------------------------
**Linearity**

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Linearity.png)
----------------------------------------------------------------------------------------------
**Normality of Error Terms**

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Normality_Errors.png)

Shapiro-Wilk p-value = 0.931

----------------------------------------------------------------------------------------------
**Autocorrelation of the Error Terms**

Durbin-Watson value = 2.126

----------------------------------------------------------------------------------------------
**Multicollinearity of the Predictors**

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_VIF.png)
----------------------------------------------------------------------------------------------
**Homoscedasticity**

Breusch-Pagan Test

Lagrange Multiplier: 13.414

p-value: 0.0984

f-value: 1.808

f p-value: 0.0929

---------------------------------------------------------------------------------------------
**Mean Squared Error**

1.616

---------------------------------------------------------------------------------------------

## Model 2 - Backward Selection
**From**: _lm(NPL ~ 

