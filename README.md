# NPL_Forecast_TrinidadTobago
Using Predictive Analytics to forecast Non-Performing Loans Ratio in Trinidad and Tobago

----------------------------------------------------------------------------------------
## Executive Overview
In Trinidad and Tobago, Real GDP Growth – Constant Prices (GDP), West Texas Intermediate Oil Prices (WTI), Exchange Rate – US$/TT$ (X_RATE), Local Cement Sales – Tonnes (CEM_SALES), M2 Money Supply Growth (M2_YYC) and Private Sector Credit Growth (CR_GROWTH_YY) are good predictors for Non-Performing Loans (NPL).

In Trinidad and Tobago, Real GDP Growth – Constant Prices (GDP), West Texas Intermediate Oil Prices (WTI), Exchange Rate – US$/TT$ (X_RATE), Local Cement Sales – Tonnes (CEM_SALES), M2 Money Supply Growth (M2_YYC) and Private Sector Credit Growth (CR_GROWTH_YY) are good predictors for Non-Performing Loans (NPL).

_lm(NPL ~ GDP + WTI + X_RATE +CEM_SALES + M2_YYC + CR_GROWTH_YY)_

Based on the Regression Diagnostics, this model (Model 1) does not violate any OLS assumptions.  
- The model displays linearity
- Error terms are normally distributed
  •	The p-value for the Shapiro-Wilk test is not less than 0.05, therefore we fail to reject the Null Hypothesis: Data is normally distributed
- No Multicollinearity Exists
  •	Correlation Matrix shows that there is no strong correlation among features
  •	Variance Inflation Factor values for all features/independent variables are less than 5
- The model is Homoscedastic
  •	There are no clear patterns in the Residuals over time or Predicted values versus Residuals
  •	The p-value from the Breusch-Pagan Test is not less than 0.05, therefore, we fail to reject the Null Hypothesis: Homoscedasticity is present






---------------------------------------------------------------------------------------

### Regression Diagnostics ###

|           |  Model 1 |  Model 2 |
| --- | --- | --- |
| Equation | lm(NPL ~ GDP + WTI + X_RATE + CEM_SALES + M2_YYC + CR_GROWTH_YY) | lm(NPL ~ CR_GROWTH + M2 + LAG_NPL) |
| Regression Summary | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_Summary.png" alt="drawing" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_Summary.png" alt="drawing" width="550"/> |
| Mean Squared Error | 2.10 | 0.25 |
| Linearity | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_Linearity.png" alt="drawing" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_Linearity.png" alt="drawing" width="600"/> |
| Normality of Error Terms | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_NormalityErrors.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_NormalityErrors.png) |
| Shapiro-Wilk | p-value = 0.921 | p-value = 0.791 |
| Multicollinearity - Correlation Matrix | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_Multicollinearity.png" alt="drawing" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_Multicollinearity.png" alt="drawing" width="300"/> |
| Multicollinearity - Variance Inflation Factor | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_VIF.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_VIF.png) |
| Homoscedasticity - Residuals over Time | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_Residuals_Time.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_Residuals_Time.png) |
| Homoscedasticity - Predicted vs Residuals | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelA1_Residuals_Predicted.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/ModelB2_Residuals_Predicted.png) |
| Homoscedasticity - Breusch-Pagan Test |  p-value = 0.4131 |  p-value = 0.1038 |

---------------------------------------------------------------------------



