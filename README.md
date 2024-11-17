# Statistical Analysis On State Disaster Response Fund (SDRF) And Forecasting

## Overview
Due to the climate of India, it is prone to many kinds of natural disaster at different times of
the year. For this the Government of India has allocated two types of funds -State Disaster
Response Fund (SDRF) and National Disaster Response Fund (SDRF). In this project we are
mostly interested in SDRF. For SDRF, the contribution is made by both the Central
Government and State Governments for all states. The SDRF shall be used only for meeting
the expenditure for providing immediate relief to the victims of cyclone, drought,
earthquake, fire, flood, tsunami, hailstorm, landslide, avalanche, cloud burst, pest attack
and frost & cold wave. Initially we do an exploratory analysis to find the insight of the
data,association and pattern.
Next, we try to see any particular factors like population, area and coastline length of the
states are affecting the allocation of SDRF. So we only focus on the 9 states with coastline
areas (West Bengal, Madhya Pradesh, Maharashtra, Tamil Nadu , Kerala, Karnataka, Goa,
Gujrat and Odisha). We also check the assumptions of our model and if any assumption is
violated(i.e if the data has heteroscedasticity or multicollinearity or autocorrelation) we will
take measures to remove any model inadequacies.
Lastly we would like to do a time series analysis on the data mainly to forecast the 2024
SDRF for the 28 states. Our entire analysis will be focused within the period 2011-2023 and
will check how close the forecasted SDRF values are for year 2024(the 2024 data has
released recently). We also want to do a bivariate time series to incorporate any possible
correlation between states and central to get better results

## Objective
1. Forecast of State Disaster Response Fund (SDRF), using time series analysis
2. To see if there is any influence of area, population and coastline length on the SDRF
allocation on certain states.

## Data Source
1. The State Disaster Response Fund data is collected from the following website:
https://ndmindia.mha.gov.in/response-fund
2. The population and density of states data is collected from
https://en.wikipedia.org/wiki/List_of_states_in_India_by_past_population
3.   The coastline length data is collected from:
https://testbook.com/ias-preparation/coastal-states-of-india


## ABOUT THE DATA
The following data consists of 13(+1) years of allocated State Disaster Response Fund
(SDRF) (including both central and states share) for 29 states from year 2011 to 2023.The
2024 SDRF data is also collected after the national budget is sanctioned.
Disaster (s) covered under SDRF: Cyclone, drought, earthquake, fire, flood, tsunami,
hailstorm, landslide, avalanche, cloudburst, pest attack, frost and cold waves.
The State Disaster Response Fund (SDRF), constituted under Section 48 (1) (a) of the
Disaster Management Act, 2005, is the primary fund available with State Governments for
responses to notified disasters. The Central government also contributes a significant
amount.

## Visualisation
We take the means SDRF for each state over 13 years and draw the doughnut
diagrams accordingly.The doughnut chart shows with the most fund gets allocated to Odisha
,Maharashtra,Gujrat ,Madhyapradesh, Haryana, Rajasthan and Tamil Nadu.

## Explorative Study using Cluster Analysis
Method used:  K-medoid clustering
Findings:
SDRF state share and central share is highly associated
among each other. This also indicate that there is no unfairness in SDRF
allocation to any state from central. . Each state has uniform allocation of funds with higher
disaster-prone state getting comparatively more fund than the low disaster -prone states. 

## Fitting of linear Regression for coastal area SDRF allocation
Method used: Multiple Linear Regression
Checking for model inaccuracies : Multicolinearity ,heteroscadasticity autocorrelation and outliars
Observations:
1. No heteroscadatiscity(using Gold_feld Quandt test)
2. No autocorrelation (using Durbin Watson test)
3. Presence of multicollinearity (using variance inflation factor)-removed using LASSO

Findings:
States with coastal areas (with larger area)are more prone to
disaster and should be allotted with higher SDRF for immediate relief of the casualties.. Also
this applies for central share.

## Time series Analysis & Forecasting
Method Used:

 Collecting the data and cleaning it
 Preparing Visualization with respect to time vs key feature
 Observing the stationarity of the series
 Developing charts to understand its nature.
 Model building – AR, MA, ARMA and ARIMA (VAR for bivariate time series forecasting)
 Extracting insights from prediction
 Forecasting.

Findings:
1. Central has allocated most of the funds during Corona pandemic.
2. Bivariate Time series model(variance autoregressive model) gives better forecasted values than univariate time series models.

## Summary
1. From the clustering we see the SDRF central share and state share have high positive
association. In other words ,the central and states allocates high SDRF for higher
disaster-prone states and lower SDRF for less disaster-prone state. The allocation is
fair. We confirm this by using Rank correlation which comes out to be positive
indicating high association between the two shares.
2.  Using regression it can be said that the length of coastline and area of each state also
have significance influence on the allocation of SDRF. Geometrically the coastline
plays a significant role in the natural disaster as the coastline area is more prone to
cyclone , hurricane, flood etc. Statistically it is also evident that the states with coastal
region are allocated with more SDRF.
 We also forecasted the SDRF (both state and central share) for year 2024. The VAR
model gives better values than the forecasted values by univariate time series model
by reducing the MSE significantly due to the consideration of correlation between the
2 sets of data(state share and central share).
3.  Another interesting find is that central allocated huge SDRF share during the corona
pandemic in 2019-2020.
