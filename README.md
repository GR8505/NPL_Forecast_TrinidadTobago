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

**Linearity**

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Linearity.png)
