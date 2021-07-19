# NPL_Forecast_TrinidadTobago
Using Predictive Analytics to forecast Non-Performing Loans Ratio in Trinidad and Tobago

----------------------------------------------------------------------------------------
## Executive Overview
In Trinidad and Tobago, Real GDP Growth – Constant Prices (GDP), West Texas Intermediate Oil Prices (WTI), Exchange Rate – US$/TT$ (X_RATE), Local Cement Sales – Tonnes (CEM_SALES), M2 Money Supply Growth (M2_YYC) and Private Sector Credit Growth (CR_GROWTH_YY) are good predictors for Non-Performing Loans (NPL).

In Trinidad and Tobago, Real GDP Growth – Constant Prices (GDP), West Texas Intermediate Oil Prices (WTI), Exchange Rate – US$/TT$ (X_RATE), Local Cement Sales – Tonnes (CEM_SALES), M2 Money Supply Growth (M2_YYC) and Private Sector Credit Growth (CR_GROWTH_YY) are good predictors for Non-Performing Loans (NPL).

_lm(NPL ~ GDP + WTI + X_RATE +CEM_SALES + M2_YYC + CR_GROWTH_YY)_

Based on the Regression Diagnostics, this model (Model 1) does not violate any OLS assumptions.  
- The model displays linearity
- Error terms are normally distributed.
The p-value for the Shapiro-Wilk test is not less than 0.05, therefore we fail to reject the Null Hypothesis: Data is normally distributed.
- No Multicollinearity Exists.
Correlation Matrix shows that there is no strong correlation among features.
Variance Inflation Factor values for all features/independent variables are less than 5.
- The model is Homoscedastic.
There are no clear patterns in the Residuals over time or Predicted values versus Residuals.
The p-value from the Breusch-Pagan Test is not less than 0.05, therefore, we fail to reject the Null Hypothesis: Homoscedasticity is present.

Model1 was compared with another model (Model2) which used Lagged Non-Performing Loans (LAG_NPL), M2 Money Supply – TT$ Million (M2) and Private Sector Credit – TT$ Million (CR_GROWTH) as predictors for NPL.  While Model2 boasted a better goodness of fit (Adjusted R-Squared) and a lower Akaike Information Criterion (AIC) value compared to Model1, it violates just one of the OLS assumptions, which is no multicollinearity.  


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

Despite this violation, Model2 can still be used as a forecasting tool.  

While the statistical efficacy of Model1 is better than Model2, we must ensure that this makes sense in the real world.  Are these variables good predictors for NPL?


### GDP ###
This regression model shows that for every unit increase in GDP, the mean NPL ratio declines by 0.5969, holding all other variables constant of course.  But from a macroeconomic perspective, is this a true reflection of what really occurs.  Probably, as the economy improves, the job market improves and this equates to more wages earned by the working population.  Therefore, borrowers are less inclined to default on their loan payments during periods of economic prosperity.


### WTI ###
Given that Trinidad and Tobago’s economy is mainly driven by its hydrocarbon sector, global energy prices may have a strong impact on the country’s economic welfare and thus, people’s ability to make timely payments on their loans.  However, according to this regression model, higher global oil prices causes NPL ratios in Trinidad and Tobago to increase. For every US$ increase in WTI, the average NPL ratio increases by 0.8818.  This is quite interesting because the common notion is that the expansion of the energy sector creates a positive spill-over effect into other sectors like, construction, manufacturing and services.  So, why do higher energy prices cause more default?  My only explanation for this is that during periods of high global energy prices, there are some slight shifts in the workforce from lower paying jobs in the non-energy sub-sectors to more lucrative employment opportunities in the energy sector and other energy-sector related jobs.  Also, whenever global energy prices become more favourable, there are shifts in government policy and as a result, there are fewer incentives for citizens to take up jobs in agriculture and local manufacturing.  


### X_RATE ###
When the exchange rate increases, our domestic currency is devalued, which means that its purchasing power is diminished.  With this devaluation, imported goods and services are more expensive and due to the nation’s high food import bill, citizens have less money for savings and loan payments.  Furthermore, as Trinidad and Tobago’s exchange rate is handled on a ‘managed float’ system, a devaluation of the local currency rarely occurs during periods of economic prosperity.  Based on our history, the exchange rate is often increased only when it is absolutely necessary and this is mostly during periods of economic challenges.  And as previously discussed, economic challenges tend to come with job losses and reduced sales and business profits, which can all lead to missed loan payments and loan defaults.  The model illustrates that for every unit increase in the exchange rate, the mean NPL ratio declines by 1.476.


### CEM_SALES ###
This predictor makes economic sense as an uptick in cement sales is often an indicator of increased construction sector activity. As expected, the construction sector is a major contributor to jobs in the domestic economy and it also creates positive spill-over effects for other businesses like hardwares and steel retailers. In addition, more construction projects tend to spur more activity in transportation and other service-related industries.  Therefore, it comes as no surprise that local cement sales has an inverse relationship with NPLs.  According to this regression model, for every sale of 1 Tonne of cement in Trinidad and Tobago, the average NPL ratio declines by 1.4694.


### M2_YYC ###
The growth in M2 money is often seen as a good proxy for heightened economic activity and generation of wealth. M2 is a broader measure of money which includes cash, checking deposits and easily convertible ‘near money’. The regression model reveals that for every 1 percent (year-on-year) increase in M2 money, the mean NPL ratio declines by 0.3973, holding all other variables constant.  This is possible as higher M2 money is indicative of a stronger economy, increase in business profits and job creation, which all translate to a lower probability of persons defaulting on their loans.


### CR_GROWTH_YY
The NPL ratio is non-performing loans as a percentage of total loans.  Given that private sector credit growth can lead to a higher total loans value, this will definitely have a negative effect on NPL.  

NPL Ratio = 


