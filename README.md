# Forecasting Non-Performing Loans in Trinidad and Tobago

<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/objects-on-workplace-BN2CQSC.jpg" alt="drawing" width="1200" height="400"/>

----------------------------------------------------------------------------------------
**Objective:** Using Predictive Analytics to forecast Non-Performing Loans Ratio (NPL) in Trinidad and Tobago.

----------------------------------------------------------------------------------------
## Executive Overview 
I developed a linear regression models to predict NPL.


**Model** : _lm(NPL ~ GDP + WTI + X_RATE +CEM_SALES + M2_YYC + CR_GROWTH_YY)_


| **Feature** | Description |
| --- | --- |
| **GDP** | Real GDP Growth Constant Prices - % Change (year-on-year) |
| **WTI** | West Texas Intermediate Oil Prices - US$ per barrel |
| **X_RATE** | Exchange Rate – TT$/US$ |
| **U_RATE** | LUnemployment Rate - Average % |
| **M2_YYC** | M2 Money Supply Growth - % Change (year-on-year) |
| **CR_GROWTH_YY** | Private Sector Credit Growth - % Change (year-on-year) |


---------------------------------------


Based on the Regression Diagnostics **(Check Below)**, the Model does not violate any **Ordinary Least Squares (OLS)** assumptions.  

- The model displays linearity
- Error terms are normally distributed.
The p-value for the Shapiro-Wilk test is greater than 0.05, therefore I failed to reject the Null Hypothesis: Data is normally distributed.
- No Multicollinearity Exists.
Correlation Matrix shows that there is no strong correlation among features.
Variance Inflation Factor (VIF) values for all features/independent variables are less than 5.
**N.B** : VIF values below 10 are acceptable and any value below 5 is considered to be ideal.
- The model is Homoscedastic.
There are no clear patterns in the Residuals over Time or Predicted values versus Residuals.
The p-value from the Breusch-Pagan Test is greater than 0.05, therefore, I failed to reject the Null Hypothesis: Homoscedasticity is present.


Looking at the performance of the model, it performs better on the test set compared to the training set.
Initially, I used Cement Sales as one of the independent variables but on closer introspection, changes in cement sales does not directly affect Non-Performing Loans.
Cement Sales is often a good proxy for construction sector activity and this industry is a major employer in the Trinidad and Tobago economy.

Therefore, I swapped Cement Sales for Unemployment Rate.


---------------------------------------------------------------------------------------

## Regression Diagnostics ##

|           |  Train |  Test |
| --- | --- | --- |
| Regression Summary | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/train_summary.png" alt="drawing" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/test_summary.png" alt="drawing" width="400"/> |
| Mean Squared Error | 1.61 | 1.03 |
| Root Mean Squared Error | 1.27 | 1.02 |
| Linearity | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/train_linearity.png" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/test_linearity.png" alt="drawing" width="325"/> |
| Normality of Error Terms | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/train_normality1.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/test_normality1.png) |
| Normality of Error Terms | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/train_normality2.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/test_normality2.png) |
| Shapiro-Wilk | p-value = 0.533 | p-value = 0.276 |
| Multicollinearity - Correlation Matrix | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/train_corr.png" alt="drawing" width="400"/> | <img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/test_corr.png" alt="drawing" width="400"/> |
| Multicollinearity - Variance Inflation Factor | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/train_VIF.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/test_VIF.png) |
| Homoscedasticity - Predicted vs Residuals | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/train_pred_residuals.png) | ![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/test_pred_residuals.png) |
| Homoscedasticity - Breusch-Pagan Test |  p-value = 0.184 |  p-value = 0.438 |

---------------------------------------------------------------------------

## Conclusion ##
While the statistical efficacy of this model is solid, I still had to ensure that it lined up with real-world developments.  Are these variables good predictors for NPLs?  Below, I explained why I thought that these variables were important to this model. 


<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/gdp-text-2021-04-06-15-18-18-utc.jpg" alt="drawing" width="600" height="200"/>

This regression model shows that for every unit increase in GDP, the mean NPL ratio declines by 0.5969, holding all other variables constant, of course.  But from a macroeconomic perspective, is this a true reflection of what really occurs?

Economic growth can create new jobs and this equates to more wages earned by the working population.  Therefore, more people can now qualify for credit facilities and this increases the denominator (Total Loans) for the NPL ratio.

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/Ratio.png)

Furthermore, as people earn more money during periods of economic prosperity, they are able to make consistent loan payments and this helps to lower the rate of loan default. As a result, economic expansion can lower the value of non-performing loans and also increase the value of total loans, and thus potentially lead to reduced NPL ratios.


### WTI ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/oil-prices-fall-concept-oil-barrel-against-declin-2021-06-01-23-09-43-utc.jpg" alt="drawing" width="600" height="200"/>

Given that Trinidad and Tobago’s economy is driven mainly by its hydrocarbon sector, global energy prices may have a strong impact on the country’s economic welfare and thus, people’s ability to make timely payments on their loans.  However, according to this regression model, global oil prices have a positive relationship with NPLs in Trinidad and Tobago. For every one(1) US$ increase in WTI, the average NPL ratio increases by 0.8818.  

This is quite interesting because the common notion is that the expansion of the energy sector creates a positive spill-over effect for other sectors like, construction, manufacturing and other services.  So, why does this model imply that there is a positive relationship between energy prices and the NPL ratio?  
My only explanation for this is as follows:
- Both Prime and Weighted Average Lending Rates have inverse relationships with WTI and lower lending rates encourage higher levels of private sector credit growth. Initially, this will be a good thing as total loans increase, thus lowering the NPL ratio.  However, as loan growth increases, the risk of default also increases.  Therefore, it is possible that the loan growth experienced during periods of favourable energy prices, crosses a particular threshold that encourages more "bad loans" on the books. 
- Also, is it possible that the economic prosperity that comes with favourable energy prices creates a false sense of security among citizens?  As economists, we cannot ignore the psychological aspect and yes, as energy is the backbone of Trinidad and Tobago's economy, complacency among citizens can begin to take hold during periods of high global oil prices. Consequently, this complacency may manifest itself via poor management of finances, which can sometimes lead to delayed loan installments and/or even loan defaults.


### X_RATE ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/close-up-fragment-of-currency-exchange-rates-board-2021-04-06-13-43-15-utc.jpg" alt="drawing" width="600" height="200"/>
This model illustrates that for every one (1) dollar increase in the exchange rate, the mean NPL ratio declines by 1.476.  More investigation is required on this variable but some studies have shown that a depreciation of the currency can lead to lower NPLs in financial systems with low foreign currency-denominated loans.


### U_RATE ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/termination-of-employment-RHBTVY4.jpg" alt="drawing" width="600" height="200"/>



### M2_YYC ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/tumbler-on-a-vault-door-2021-04-05-08-15-25-utc.jpg" alt="drawing" width="600" height="200"/>
The growth in M2 money is often seen as a good proxy for heightened economic activity and generation of wealth. M2 is a broader measure of money which includes cash, checking deposits and easily convertible ‘near money’. The regression model reveals that for every 1 percent (year-on-year) increase in M2 money, the mean NPL ratio declines by 0.3973, holding all other variables constant.  This is possible as higher M2 money is indicative of a stronger economy, healthier business profits and an uptick in job creation, which all translate to a lower probability of loan delinquency. 

In a healthy business environment, higher profits mean that corporate and commercial loan payments are upheld, which translates to lower delinquency rates.  Also, companies that plan to expand its operations, possess requisite leverage to obtain credit facilities.  This will result in higher loan balances and thus lower the NPL ratio, as the denominator in the formula increases.

![](https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/Ratio.png)

A healthier business environment also leads to more hiring in Trinidad and Tobago and as previously discussed a stronger job market is often linked to higher levels of loan balances, which lowers the NPL ratio due to a higher "denominator-effect". As people make more money, they make apply for loans to purchase a car, furniture, or even mortgages and home renovation loans.


### CR_GROWTH_YY ###
<img src="https://github.com/GR8505/NPL_Forecast_TrinidadTobago/blob/main/Images1/estate-agent-are-presenting-home-loan-to-client-an-45QXF26.jpg" alt="drawing" width="600" height="200"/>
The NPL ratio is non-performing loans as a percentage of total loans.  Given that private sector credit growth can lead to a higher total loans value, this will definitely have a negative effect on NPL. 

If non-performing loans remain constant and the denominator increases, then this will result in a lower NPL ratio.  In this model, a 1 percent increase in private sector credit growth will result in a decline in the average NPL ratio by 0.6199.

------------------------------------------------------------------------------

Thus, these features seem to be logical and move in accordance with real world economic occurences.

Going forward, my goal is to develop a similar model for tourism-dependent economies in the Caribbean.  I suspect that tourist arrivals will probably be a main predictor in the model.

-------------------------------------------------------------------------------


