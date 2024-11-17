data=read.csv(file.choose())
data

#forecasting
library(tseries)
library(forecast)
data_ts <- ts(data[,30], start = 2011, frequency=1);data_ts
head(data)
plot(data_ts)
data_cen=read.csv(file.choose())
data_cen
data_ts_cen <- ts(data_cen[,30], start = 2011, frequency=1);data_ts_cen
par(mfrow = c(1, 2)) 
plot(data_ts_cen,main="SDRF central share")
plot(data_ts,main="SDRF state share")
adf.test(data_ts)

#here we can see tha adf test tells us the process is  stationary
acf(data_ts)
pacf(data_ts)



data_ts <- ts(data[,8], start = 2011, frequency=1);data_ts
fit=auto.arima(data_ts)

forecast=forecast(fit,level = c(95),h=1);forecast


#multivariate time series


library(lubridate)
head(data)

install.packages("AICcmodavg")
library(AICcmodavg)
library(vars)
d1=read.csv(file.choose())
d2=read.csv(file.choose())
m_tim=ts((cbind(d1[,2],d2[,2])), start = 2011, frequency=1);m_tim
Var=VAR(y=m_tim,p=2)
forecast=forecast(Var,level = c(95),h=1);forecast
AIC(Var)
?VAR



#exploratory data analysisS
# clustering

library(cluster)
library(factoextra)

#state share SDRF
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


#central Share SDRF
d6=read.csv(file.choose(),head=T)
d6
central_cluster=d6[,-1]


fviz_nbclust(central_cluster,pam,method="silhouette")
k_med2=pam(central_cluster,k=2)
fviz_cluster(k_med2)
k_med2$medoids
k_med2$clustering
y3=central_cluster[k_med2$clustering==1,]
mean3=apply(y3,2,mean);mean3
sd3=apply(y3,2,sd);sd3
y4=central_cluster[k_med2$clustering==2,]
mean4=apply(y4,2,mean);mean4
sd4=apply(y4,s,sd);sd4
c2=cbind(d6[,1],k_med2$clustering);c2
c2[,2]

c3=cbind(c1,c2[,2]);c3


# rank correlation
da_corr=read.csv(file.choose())
da_corr
head(da_corr)
da1=da_corr[c(1:10),];da1

#rank correlation
x=as.matrix(da1$statemean)
y=as.matrix(da1$centralmean)
result1=cor(x,y,method="spearman");result1
res_test1=cor.test(x,y,method="spearman");res_test1

da2=da_corr[c(11:29),];da2
w=as.matrix(da2$statemean)
z=as.matrix(da2$centralmean)
result2=cor(w,z,method="spearman");result2
res_test2=cor.test(x,y,method="spearman");res_test2

#regression
 #coastal area
cos_data=read.csv(file.choose())
cos_data
head(cos_data)
c_d=cos_data[,c(2:6)];c_d
mod1=lm(statemean~est.population + area.in.sq.km.+ density+coastline.km. ,data=c_d)
summary(mod1)
car::vif(mod1)
car::durbinWatsonTest(mod1)
library(glmnet)

y_train=cos_data[,6]
x_train=cos_data[,c(2,3,4,5)]
cv_mod=cv.glmnet(x_train,y_train,alpha=1);cv_mod#k-fold cross validation
best_lambda_ridge=cv_mod$lambda.min #0.06993278
best_lambda_ridge
plot(cv_mod)

#best ridge model fit
best_model_ridge=glmnet(x_train,y_train,alpha=1,lambda=best_lambda_ridge)
coef(best_model_ridge)
car::vif(best_model_ridge)
library(lmtest)
gqtest(mod1, order.by =~est.population + area.in.sq.km.+ density+coastline.km., data = c_d,fraction=2)

ceiling(29/3
)
mtcars

#regression for coastal data 
dt=read.csv(file.choose())
dt
dt1=dt[c(1:10),];dt1
dt2=dt[c(11:29),];dt2

lm1=lm(statemean~population+ density + area,data=dt1)
summary(lm1)
lm2=lm(centralmean~population+ density + area,data=dt1)
summary(lm2)
lm3=lm(statemean~population+ density + area,data=dt2)
summary(lm3)
lm4=lm(centralmean~population+ density + area,data=dt2)
summary(lm4)
car::vif(lm4)
dt3=dt2[,-c(1,6,7)];dt3
gqtest(lm3,order.by=~population+density+area,data=dt3,fraction=6) 
