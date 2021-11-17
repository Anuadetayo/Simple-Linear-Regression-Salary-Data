# Simple-Linear-Regression-Salary-Data
#import relevant libaries
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import statsmodels.api as sm

#import data
data= pd.read_csv('Salary_Data.csv')

data.head()

data.describe()

#define the independent and dependent variable
y= data['Salary']
x1= data['YearsExperience']

#explore the data
plt.scatter(x1,y)
plt.ylabel('Salary')
plt.xlabel('YearsExperience')
plt.show()

#Regression itself
x=sm.add_constant(x1)
results=sm.OLS(y,x).fit()
results.summary()

#Summary of the Result
#The R-squared is a value of 0.957 which translates to the regression explains a lot about the variability of the data. Also means that the model fits well with the data.
#The P-value for the constant of the intercept shows is 0.000. This shows that the variable is signigicant
#The P-value for the dependent varaible is also 0.000 , which also means that the variable is signigicant

plt.scatter(x1,y)
yhat= 9449.9623*x1 + 25790
fig = plt.plot(x1,yhat, lw=4, c='orange', label ='regression line')
plt.xlabel('Salary', fontsize = 20)
plt.ylabel('YearsExperience', fontsize = 20)
plt.show()
