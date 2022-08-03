# TimeSeriesAnalysis-VAR-Modeling-for-U.S.-Economic-Indicators
We’ve explored how various U.S. economic indicators are related to each other. This is a classic application for the VAR modeling. U.S. Federal Reserve use these economic indicators to make monetary policy decision. Specifically, we will study the inter-dependence and Granger causality between the following indicators:

Gross Domestic Product (GDP) – Recorded quarterly, measuring the market value of the goods and services produced by labor and property located in the United States.

Real imports of goods and services (IMPGSC1) – Recorded quarterly, measuring the value of goods and services that are sold, given away, or otherwise transferred by foreign residents to U.S. residents.

Real exports of goods and services (EXPGS) – Recorded quarterly, measuring the value of goods and services that are sold, given away, or otherwise transferred by U.S. residents to foreign residents.

Personal Consumption Expenditure (PCE) – Recorded monthly, measuring household expenditures on durable and non-durable goods, as well as services.

Unemployment (UNRATE) – Recorded monthly, measuring the number of unemployed people as a percentage of the labor force (the labor force is the sum of the employed and unemployed).

The data was acquired from the U.S. Bureau of Economic Analysis, retrieved from FRED, Federal Reserve Bank of St. Louis (https://fred.stlouisfed.org/ (Links to an external site.)). The data cover the period starting 1959 until the 2nd quarter of 2021 or June 2021. The data were divided into two files, one including indicators recorded quarterly and another including indicators recorded monthly. The two datasets can be downloaded from the following files:

Quarterly Data Download Quarterly Data

Monthly Data Download Monthly Data

Note: Some indicators are recorded quarterly, and others are recorded monthly. To be able to analyze all indicators using multivariate time series analysis, we will need to bring all indicators to be measured quarterly.

The starter R Markdown template is provided below:

HW8_starter template.Rmd Download HW8_starter template.Rmd

Use this code to fill in your answers to the questions below. Submit the knitted file for this homework assignment.

Question 1: Univariate Analysis (12 points)

(2 points) 1a. Plot the time series of all indicators for comparison and discuss whether you find any similarities in terms of trend or other features. Plot also the 1st order difference plots and the corresponding ACF plots. Interpret in terms of stationarity and volatility.

(5 points) 1b. Divide the GDP data into training data including the data for years 1959 to 2020 with the last two quarters being the testing data. Fit the trend using the splines regression to the GDP training time series and apply ARMA to the residuals. Evaluate goodness of fit for the ARMA model. Forecast the first two quarters of 2021 (testing data) and compare to the observed one. Discuss why there are (or not!) significant differences between predicted vs observed.

(5 points) 1c. Perform a similar analysis as in (1b) but this time applying ARIMA to the GDP time series. Compare the forecast with those in (1b) and discuss why different or similar.

Question 2: Multivariate Analysis using VAR modeling (35 points)

For this question, divide the data into training data (excluding the first two quarters of 2021) and testing data (including the two quarters). You will apply the modeling to the training data, and we will forecast the first two quarters of 2021.

(6 points) 2a. Apply the VAR model to the multivariate time series including all five economic indicators observed quarterly. (Note that you will apply VAR to the training data.) Identify the VAR order using both AIC and BIC and compare. If the selected order using AIC is larger than the selected order than selected using BIC, apply the Wald test to evaluate whether a smaller order than the one selected with AIC would be a better choice, meaning the smaller order model would perform similarly than the larger order model. Interpret the order selection.

(7 points) 2b. Based on the analysis in 2a, select the VAR order using BIC and fit that model. Print out the model summary and comment on the statistical significance of the coefficients. Apply a model selection analysis using stepwise regression to select the models for each individual time series. What do you conclude from this model selection? Apply the restrict() command in R to restrict the model of order. How do the restrcited models compare?

(5 points) 2c. Evaluate the goodness of fit using the multivariate ARCH test, the Jarque-Bera test and the Portmanteau test. State which assumptions are satisfied, and which are violated. (Note: While we evaluate the residuals for the normality assumption, we don’t necessarily assume normality of the data. We use the normality assumption if we use the t-test to evaluate statistical significance.)

(10 points) 2d. Using the VAR model with the order selected using BIC, forecast the first two quarters of 2021 using the unrestricted and restricted VAR. Include 95% confidence intervals. Compare the predictions to the observed data. (You don't need to plot them (but can if you'd like).  Using mean absolute percentage error and the precision measure, compare the predictions for GDP derived from the univariate analysis (Question 1) and this multivariate analysis. Discuss on the differences or similarities.

(7 points) 2e. Perform a Granger Causality analysis using Wald test to evaluate whether any of the economic indicators lead GDP. Would any of the indicators help in predicting or explaining GDP for next quarters? Provide your interpretation based on the Granger causality as well as for forecasting comparison in (2d).

Question 3: VAR forecasting for Different Time Period (18 points)

For this question, consider the training data to include the time values up to December 2018 and the testing data to include the first two quarters of 2019.

(5 points) 3a. Apply the VAR modeling approach with the order selected using the BIC approach giving the unrestricted VAR model. Apply a model selection analysis using stepwise regression to select the models for each individual time series. Based on the selected models, form the restricted VAR model. Compare these two models in terms of coefficients and their statistical significance with the models derived in Question 2.

(8points) 3b. Forecast the first two quarters of 2019 using the unrestricted and restricted VAR derived at (3a). Include 95% confidence intervals. Compare the predictions to the observed data using mean absolute percentage error and the precision measure for GDP. Compare the predictions to those derived in (2d). Comment on the accuracy of the predictions.

(5 points) 3c. Perform a Granger Causality analysis using Wald test to evaluate whether any of the economic indicators lead GDP. Would any of the indicators help in predicting or explaining GDP for next quarters? Provide your interpretation based on the Granger causality as well as for forecasting comparison in (3b). Compare this analysis with the findings in (2e).

Question 4: Reflection (5 points)

From what you encountered above and your conceptual understanding of VAR modelling, reflect on the relative strengths and weaknesses of the modelling approach. Particularly, you will need to put this analysis into the perspective of the impact of the covid-19 pandemic on GDP.
