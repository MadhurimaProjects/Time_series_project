# Time_series_project

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
```
#state DRF
d5=read.csv(file.choose(),head=T)
d5
head(d5)
state_cluster=d5[,-1]
fviz_nbclust(state_cluster,pam,method="silhouette")
k_med1=pam(state_cluster,k=2)
fviz_cluster(k_med1)
k_med1$medoids
k_med1$clustering
y1=state_cluster[k_med1$clustering==1,]
mean1=apply(y1,2,mean);mean1
sd1=apply(y1,2,sd);sd1
y2=state_cluster[k_med1$clustering==2,]
mean2=apply(y2,2,mean);mean2
sd2=apply(y2,s,sd);sd2
c1=cbind(d5[,1],k_med1$clustering);c1
```




