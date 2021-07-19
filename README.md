# NPL_Forecast_TrinidadTobago
Using Predictive Analytics to forecast Non-Performing Loans Ratio in Trinidad and Tobago

----------------------------------------------------------------------------------------
## Executive Overview
The following list of independent variables were used to predict Non-Performing Loans (NPL) in Trinidad and Tobago:
- Real GDP Growth Constant Prices **(GDP)**
- West Texas Intermediate Oil Prices **(WTI)**
- Exchange Rate – US$/TT$ **(X_RATE)**
- Local Cement Sales Tonnes **(CEM_SALES)**
- M2 Money Supply Growth **(M2_YYC)** and 
- Private Sector Credit Growth **(CR_GROWTH_YY)** 

<mark>_lm(NPL ~ GDP + WTI + X_RATE +CEM_SALES + M2_YYC + CR_GROWTH_YY)_</mark>

Based on the Regression Diagnostics, this model (Model 1) does not violate any OLS assumptions.  
- The model displays linearity
- Error terms are normally distributed.
The p-value for the Shapiro-Wilk test is greater than 0.05, therefore we fail to reject the Null Hypothesis: Data is normally distributed.
- No Multicollinearity Exists.
Correlation Matrix shows that there is no strong correlation among features.
Variance Inflation Factor values for all features/independent variables are less than 5.
- The model is Homoscedastic.
There are no clear patterns in the Residuals over time or Predicted values versus Residuals.
The p-value from the Breusch-Pagan Test is greater than 0.05, therefore, we fail to reject the Null Hypothesis: Homoscedasticity is present.

Model 1 was compared with another model (Model 2) which used the following list of features/independent variables:
- Lagged Non-Performing Loans (LAG_NPL)
- M2 Money Supply – TT$ Million (M2) and 
- Private Sector Credit – TT$ Million (CR_GROWTH) as predictors for NPL

While Model 2 boasted a better goodness of fit (See Adjusted R-Squared in Regression Diagnostics below) and a lower Akaike Information Criterion (AIC) value compared to Model 1, it violates just one of the OLS assumptions, which is no multicollinearity.  


---------------------------------------------------------------------------------------

## Regression Diagnostics ##

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

## Conclusison ##
Despite this one violation, Model 2 can still be used for the purpose of forecasting.  

While the statistical efficacy of Model 1 is more solid than that of Model 2, we must ensure that it makes sense in the real world.  Are these variables good predictors for NPL?


### GDP ###
This regression model shows that for every unit increase in GDP, the mean NPL ratio declines by 0.5969, holding all other variables constant of course.  But from a macroeconomic perspective, is this a true reflection of what really occurs?

From my understanding, economic growth can spur hiring and this equates to more wages earned by the working population.  Therefore, borrowers are more likely to consistently pay their monthly loan installments and are less inclined to default on their credit facilities during periods of economic prosperity.


### WTI ###
Given that Trinidad and Tobago’s economy is mainly driven by its hydrocarbon sector, global energy prices may have a strong impact on the country’s economic welfare and thus, people’s ability to make timely payments on their loans.  However, according to this regression model, higher global oil prices causes NPL ratios in Trinidad and Tobago to increase. For every US$ increase in WTI, the average NPL ratio increases by 0.8818.  

This is quite interesting because the common notion is that the expansion of the energy sector creates positive spill-over effects for other sectors like, construction, manufacturing and other services.  So, why do higher energy prices cause more default?  My only explanation for this is that possibly during these periods of high global energy prices, there are some slight shifts in the workforce as citizens trnasition from lower paying jobs in the non-energy sub-sectors to more lucrative employment opportunities in the energy sector and other energy-sector related jobs.  Also, due to the high volatility of global energy prices, the Trinidad and Tobago government moves swiftly to ensure maximum benefit from the hydrocarbon sector.  Thus, there is reduced investment and fewer government incentives for the local agriculture and manufacturing sectors.  


### X_RATE ###
When the exchange rate increases, our domestic currency is devalued, which means that its purchasing power is diminished.  With this devaluation, imported goods and services are more expensive and due to the nation’s high food import bill, citizens have less available funds for savings and loan payments.  Furthermore, as Trinidad and Tobago’s exchange rate is handled on a ‘managed float’ system, a devaluation of the local currency rarely occurs during periods of economic prosperity.  Based on our history, the exchange rate is often increased only when it is absolutely necessary and this most likely occurs during periods of economic uncertainty.  

And as previously discussed, economic challenges tend to come with job losses and reduced sales/business profits, which can all lead to missed loan payments and loan defaults.  The model illustrates that for every unit increase in the exchange rate, the mean NPL ratio declines by 1.476.


### CEM_SALES ###
This predictor makes economic sense as an uptick in cement sales is often an indicator of increased construction sector activity. As expected, the construction sector is a major contributor to jobs in the domestic economy and it also creates positive spill-over effects for other businesses like hardwares and steel retailers. In addition, more construction projects stimulate activity in transportation and other service-related industries.  Therefore, it comes as no surprise that local cement sales has an inverse relationship with NPL.  According to this regression model, for every sale of 1 Tonne of cement, the average NPL ratio declines by 1.4694.


### M2_YYC ###
The growth in M2 money is often seen as a good proxy for heightened economic activity and generation of wealth. M2 is a broader measure of money which includes cash, checking deposits and easily convertible ‘near money’. The regression model reveals that for every 1 percent (year-on-year) increase in M2 money, the mean NPL ratio declines by 0.3973, holding all other variables constant.  This is possible as higher M2 money is indicative of a stronger economy, healthier business profits and an uptick in job creation, which all translate to a lower probability of delinquent loan payments.


### CR_GROWTH_YY
The NPL ratio is non-performing loans as a percentage of total loans.  Given that private sector credit growth can lead to a higher total loans value, this will definitely have a negative effect on NPL. 

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/Ratio.png)

If non-performing loans remain constant and the denominator increases, then this will result in a lower NPL ration.  In this model, a 1 percent increase in private sector credit growth will result in a decline in the average NPL ratio by 0.6199.

------------------------------------------------------------------------------

Thus, these features seem to be logical in accordance with real world economic occurences.

Going forward, my goal is to develop a similar model for tourism-dependent economies in the Caribbean.  I suspect that tourist arrivals will probably be a main predictor in the model.

-------------------------------------------------------------------------------


