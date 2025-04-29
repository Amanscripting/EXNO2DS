# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

dt=pd.read_csv("/content/titanic_dataset (2).csv")

dt
```
![Screenshot 2025-04-15 143936](https://github.com/user-attachments/assets/3c11ec85-06c1-430f-94e1-24e22091d98d)
```
dt.info()
```
![Screenshot 2025-04-15 144047](https://github.com/user-attachments/assets/884e62ea-3fae-430e-85bd-46bc8c44a24d)
```
dt.shape
```
![Screenshot 2025-04-15 144128](https://github.com/user-attachments/assets/da8da925-2cac-4f2d-9a49-c76ea67b9765)
```
dt.set_index("PassengerId",inplace=True)
dt.describe()
```
![image](https://github.com/user-attachments/assets/c7ff99f3-3bb1-44fa-a425-b4abaa1531eb)
```
dt.nunique()
```
![Screenshot 2025-04-15 144156](https://github.com/user-attachments/assets/dbb34e71-9e99-4f8b-b6a4-fd05d5d6dc1d)
```
dt["Survived"].value_counts()
```
![Screenshot 2025-04-15 144222](https://github.com/user-attachments/assets/03fc427c-ddc8-4d81-866d-ba08251e3007)
```
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
```
![Screenshot 2025-04-15 144249](https://github.com/user-attachments/assets/b69139b9-abba-40a1-8ca4-202eae57d5bf)

```
sns.countplot(data=dt,x="Survived")
dt
```
![Screenshot 2025-04-15 144342](https://github.com/user-attachments/assets/97d4b11b-a36d-47d7-8a09-53038f20b85a)
```
dt.Pclass.unique()
```
![Screenshot 2025-04-15 144436](https://github.com/user-attachments/assets/67a48358-bc6d-487d-9a1a-59665217d8b2)
```
dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
```
![Screenshot 2025-04-15 144513](https://github.com/user-attachments/assets/a97760ff-00e6-4f56-9032-39adb0179d95)
```
sns.catplot(x="Gender",col="Survived",kind="count",data=dt,height=5,aspect=.7)
```
![Screenshot 2025-04-15 144616](https://github.com/user-attachments/assets/fc98cd36-5bb3-4529-a4b1-09b7c7c90500)
```
sns.catplot(x='Survived',hue="Gender",data=dt,kind="count")
```
![Screenshot 2025-04-15 144658](https://github.com/user-attachments/assets/b21b5612-dd5c-4ce9-a70b-4d48525074bb)
```
dt.boxplot(column="Age",by="Survived")
```
![Screenshot 2025-04-15 144808](https://github.com/user-attachments/assets/f23a26c4-0f72-4b22-aee2-c32aefea8534)
```
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
```
![Screenshot 2025-04-15 144936](https://github.com/user-attachments/assets/832d3135-d2cc-412f-a33c-716cc1cc4134)
```
sns.jointplot(x="Age",y="Fare",data=dt)
```
![Screenshot 2025-04-15 145003](https://github.com/user-attachments/assets/6904b3e7-a460-484c-9d9f-e42a6d3e9ea4)
```
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
```
![Screenshot 2025-04-15 145032](https://github.com/user-attachments/assets/abd153a4-ad73-434a-af09-315a52f88920)
```
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
```
![Screenshot 2025-04-15 145104](https://github.com/user-attachments/assets/69cd8bf5-72e3-4f16-bd60-9e5190e6e60b)
```
numeric_dt=dt.select_dtypes(include=['int64','float64'])
corr=numeric_dt.corr()
sns.heatmap(corr,annot=True)
```
![Screenshot 2025-04-15 145141](https://github.com/user-attachments/assets/9962a3f3-5e46-4443-835f-ad2b2205ed3a)
```
sns.pairplot(dt)
```
![Screenshot 2025-04-15 145330](https://github.com/user-attachments/assets/73c8179d-13f9-487c-9095-66e69126dec3)

# RESULT
        Exploratory Data Analysis on the given data set was performed successfully.
