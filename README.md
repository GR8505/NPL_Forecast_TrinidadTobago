# Forecasting Non-Performing Loans in Trinidad and Tobago

<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/objects-on-workplace-BN2CQSC.jpg" alt="drawing" width="1200" height="400"/>

----------------------------------------------------------------------------------------
**Objective:** Using Predictive Analytics to forecast Non-Performing Loans Ratio (NPL) in Trinidad and Tobago.

----------------------------------------------------------------------------------------
## Executive Overview 
I developed two linear regression models to predict NPL.


**Model 1** : _lm(NPL ~ GDP + WTI + X_RATE +CEM_SALES + M2_YYC + CR_GROWTH_YY)_

**Model 2** : _lm(NPL ~ CR_GROWTH + M2 + LAG_NPL)_


| **Feature** | Description |
| --- | --- |
| **GDP** | Real GDP Growth Constant Prices - % Change (year-on-year) |
| **WTI** | West Texas Intermediate Oil Prices - US$ per barrel |
| **X_RATE** | Exchange Rate – TT$/US$ |
| **CEM_SALES** | Local Cement Sales - Tonnes |
| **M2_YYC** | M2 Money Supply Growth - % Change (year-on-year) |
| **CR_GROWTH_YY** | Private Sector Credit Growth - % Change (year-on-year) |
| **CR_GROWTH** | Private Sector Credit - TT$ Million |
| **M2** | Money Supply - TT$ Million |
| **LAG_NPL** | Non-Performing Loans Ratio Lagged by one (1) year |


---------------------------------------


Based on the Regression Diagnostics **(Check Below)**, Model 1 does not violate any **Ordinary Least Squares (OLS)** assumptions.  

- The model displays linearity
- Error terms are normally distributed.
The p-value for the Shapiro-Wilk test is greater than 0.05, therefore I failed to reject the Null Hypothesis: Data is normally distributed.
- No Multicollinearity Exists.
Correlation Matrix shows that there is no strong correlation among features.
Variance Inflation Factor (VIF) values for all features/independent variables are less than 5.
- The model is Homoscedastic.
There are no clear patterns in the Residuals over Time or Predicted values versus Residuals.
The p-value from the Breusch-Pagan Test is greater than 0.05, therefore, I failed to reject the Null Hypothesis: Homoscedasticity is present.


While Model 2 boasted a better goodness of fit **(See Adjusted R-Squared in Regression Diagnostics below)** and a lower **Akaike Information Criterion (AIC)** value, it violates just one of the OLS assumptions.  Multicollinearity is present in Model 2, as both CR_GROWTH and M2 are strongly correlated and both of these features have VIF values greater than 10.

**N.B** : VIF values below 10 are acceptable and any value below 5 is considered to be ideal.


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
Despite the one violation, Model 2 can still be used to provide forecasts.  However, I opted to use Model 1 as it upholds all OLS assumptions. While the statistical efficacy of Model 1 is more solid than that of Model 2, I still had to ensure that it made sense in accordance with real world occurences.  Are these variables good predictors for NPLs?  Below, I explained why I thought that these variables were important to this model. 


<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/gdp-text-2021-04-06-15-18-18-utc.jpg" alt="drawing" width="600" height="200"/>

This regression model shows that for every unit increase in GDP, the mean NPL ratio declines by 0.5969, holding all other variables constant, of course.  But from a macroeconomic perspective, is this a true reflection of what really occurs?

Economic growth can create new jobs and this equates to more wages earned by the working population.  Therefore, more people can now qualify for credit facilities and this increases the denominator (Total Loans) for the NPL ratio.

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/Ratio.png)

Furthermore, as people earn more money during periods of economic prosperity, they are able to make consistent loan payments and this helps to lower the rate of loan default. As a result, economic expansion can potentially lead to reduced NPL ratios.


### WTI ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/oil-prices-fall-concept-oil-barrel-against-declin-2021-06-01-23-09-43-utc.jpg" alt="drawing" width="600" height="200"/>

Given that Trinidad and Tobago’s economy is driven mainly by its hydrocarbon sector, global energy prices may have a strong impact on the country’s economic welfare and thus, people’s ability to make timely payments on their loans.  However, according to this regression model, global oil prices have a positive relationship with NPLs in Trinidad and Tobago. For every one(1) US$ increase in WTI, the average NPL ratio increases by 0.8818.  

This is quite interesting because the common notion is that the expansion of the energy sector creates a positive spill-over effect for other sectors like, construction, manufacturing and other services.  So, why does this model imply that there is a positive realtionship between energy prices and the NPL ratio?  
My only explanation for this is as follows:
- Both Prime and Weighted Average Lending Rates have inverse relationships with WTI. But, lower lending rates encourage higher levels of private sector credit growth. Initially, this will be a good thing as total loans increase, thus lowering the NPL ratio.  However, as loan growth increases, the risk of default also increases.  Therefore, it is highly likely that the loan growth experienced during periods of favourable energy prices, crosses a particular "risk-averse" lending threshold.  As a result, we begin to witness an increasing number of "bad loans" on the books beyond this point.  
- Also, the extremely high level of economic prosperity that comes with favourable energy prices can also create a false sense of security among citizens.  As economists, we cannot ignore the psychological aspect and yes, as energy is the backbone of Trinidad and Tobago's economy, complacency among citizens can begin to take hold during periods of high global oil prices. Consequently, this complacency can possibly manifest itself via poor management of finances, which can sometimes lead to delayed loan installments or loan defaults.


### X_RATE ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/close-up-fragment-of-currency-exchange-rates-board-2021-04-06-13-43-15-utc.jpg" alt="drawing" width="600" height="200"/>
The model illustrates that for every one (1) dollar increase in the exchange rate, the mean NPL ratio declines by 1.476.


### CEM_SALES ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/supply-of-cement-2021-04-03-14-01-07-utc.jpg" alt="drawing" width="600" height="200"/>
This predictor makes economic sense as an uptick in cement sales is often an indicator of increased construction sector activity. As expected, the construction sector is a major contributor to jobs in the domestic economy and it also creates positive spill-over effects for other businesses like hardwares and steel retailers. In addition, more construction projects stimulate activity in transportation and other service-related industries.  Therefore, it comes as no surprise that local cement sales has an inverse relationship with NPL.  According to this regression model, for every sale of 1 Tonne of cement, the average NPL ratio declines by 1.4694.


### M2_YYC ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/tumbler-on-a-vault-door-2021-04-05-08-15-25-utc.jpg" alt="drawing" width="600" height="200"/>
The growth in M2 money is often seen as a good proxy for heightened economic activity and generation of wealth. M2 is a broader measure of money which includes cash, checking deposits and easily convertible ‘near money’. The regression model reveals that for every 1 percent (year-on-year) increase in M2 money, the mean NPL ratio declines by 0.3973, holding all other variables constant.  This is possible as higher M2 money is indicative of a stronger economy, healthier business profits and an uptick in job creation, which all translate to a lower probability of loan delinquency. Also, a stronger job market is often linked to higher levels of private sector credit, which lowers the NPL ratio due to a higher "denominator-effect".


### CR_GROWTH_YY ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/estate-agent-are-presenting-home-loan-to-client-an-45QXF26.jpg" alt="drawing" width="600" height="200"/>
The NPL ratio is non-performing loans as a percentage of total loans.  Given that private sector credit growth can lead to a higher total loans value, this will definitely have a negative effect on NPL. 

If non-performing loans remain constant and the denominator increases, then this will result in a lower NPL ratio.  In this model, a 1 percent increase in private sector credit growth will result in a decline in the average NPL ratio by 0.6199.

------------------------------------------------------------------------------

Thus, these features seem to be logical in accordance with real world economic occurences.

Going forward, my goal is to develop a similar model for tourism-dependent economies in the Caribbean.  I suspect that tourist arrivals will probably be a main predictor in the model.

-------------------------------------------------------------------------------


