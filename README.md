# NPL_Forecast_TrinidadTobago
Using Predictive Analytics to forecast Non-Performing Loans Ratio in Trinidad and Tobago

----------------------------------------------------------------------------------------
## Executive Overview








---------------------------------------------------------------------------------------

### Regression Diagnostics ###

|           |  Model 1 |  Model 2 |
| --- | --- | --- |
| Equation | lm(NPL ~ GDP + U_RATE + CR_GROWTH + M2 + CEM_SALES + X_RATE + WTI + WA_LR) | lm(NPL ~ GDP + CR_GROWTH + M2 + N_RESV + WTI + LAG_NPL) |
| Regression Summary | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Summary.png" alt="drawing" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_Summary.png" alt="drawing" width="400"/> |
| Regression Summary | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Summary.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_Summary.png) |
| Mean Squared Error | 1.16 | 0.33 |
| Linearity | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Linearity.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_Linearity.png) |
| Normality of Error Terms | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Normality_Errors.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_Normality_Errors.png) |
| Shapiro-Wilk | p-value = 0.931 | p-value = 0.511 |
| Multicollinearity | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_VIF.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_VIF.png) |
| Homoscedasticity | Breusch-Pagan p-value = 0.0984 | Breusch-Pagan p-value = 0.1385 |





