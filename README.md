# NPL_Forecast_TrinidadTobago
Using Predictive Analytics to forecast Non-Performing Loans Ratio in Trinidad and Tobago

----------------------------------------------------------------------------------------
## Executive Overview








---------------------------------------------------------------------------------------

### Regression Diagnostics ###

|           |  Model 1 |  Model 2 |
| --- | --- | --- |
| Equation | lm(NPL ~ GDP + WTI + X_RATE + CEM_SALES + M2_YYC + CR_GROWTH_YY) | lm(NPL ~ CR_GROWTH + M2 + LAG_NPL) |
| Regression Summary | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_Summary.png" alt="drawing" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_Summary.png" alt="drawing" width="525"/> |
| Mean Squared Error | 2.10 | 0.25 |
| Linearity | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Linearity.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_Linearity.png) |
| Normality of Error Terms | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_Normality_Errors.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_Normality_Errors.png) |
| Shapiro-Wilk | p-value = 0.931 | p-value = 0.511 |
| Multicollinearity | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model2_VIF.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images/Model4_VIF.png) |
| Homoscedasticity | Breusch-Pagan p-value = 0.0984 | Breusch-Pagan p-value = 0.1385 |





