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
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
~~~
~~~
dt=pd.read_csv("titanic_dataset.csv")
dt
~~~
![Screenshot 2024-04-01 142018](https://github.com/Dhanu654/EXNO2DS/assets/148514965/13922c7c-02df-44cb-ae9e-b4cdaf2aabb1)

~~~
dt.info()
~~~
![Screenshot 2024-04-01 142031](https://github.com/Dhanu654/EXNO2DS/assets/148514965/e8d326dd-02de-4de8-b1de-d719a0585874)

~~~
dt.set_index("PassengerId",inplace=True)
~~~
~~~
dt.shape
~~~
![Screenshot 2024-04-01 142037](https://github.com/Dhanu654/EXNO2DS/assets/148514965/378c6da5-d155-41ae-b2d5-8f1bb06079f8)

~~~
dt.nunique()
~~~
![Screenshot 2024-04-01 142043](https://github.com/Dhanu654/EXNO2DS/assets/148514965/dfbd6c2e-47e1-43f5-adb1-452bc45da9d4)

~~~
dt["Survived"].value_counts()
~~~
![Screenshot 2024-04-01 142050](https://github.com/Dhanu654/EXNO2DS/assets/148514965/905d2dac-0c87-471f-be7e-5ab44e52ef3e)

~~~
per=(dt["Survived"].value_counts()/dt.shape[0]*100).round(2)
per
~~~
![Screenshot 2024-04-01 142056](https://github.com/Dhanu654/EXNO2DS/assets/148514965/ae6fe782-6c61-47c7-b27a-6c962bedf8d6)

~~~
sns.countplot(data=dt,x="Survived")
~~~
![Screenshot 2024-04-01 142105](https://github.com/Dhanu654/EXNO2DS/assets/148514965/f2914510-5cc0-4769-b3c0-0a4f3532d58b)

~~~
dt.Pclass.unique()
~~~
![Screenshot 2024-04-01 142111](https://github.com/Dhanu654/EXNO2DS/assets/148514965/daafb2ad-e26a-4da6-8069-193d54c61b77)

~~~
dt.rename(columns={'Sex':'Gender'},inplace=True)
dt
~~~
![Screenshot 2024-04-01 142126](https://github.com/Dhanu654/EXNO2DS/assets/148514965/caf7b020-7cdc-486d-9c21-12c43a0c8ee9)


## BIVARIATE ANALYSIS

~~~
sns.catplot(x="Gender",col="Survived",kind="count", data=dt,height=5,aspect=.7)
~~~
![Screenshot 2024-04-01 142139](https://github.com/Dhanu654/EXNO2DS/assets/148514965/537140a1-50b5-43a6-8d8c-7dcb92ad02fc)

~~~
sns.catplot(x="Survived",hue="Gender",data=dt,kind="count"
~~~
![Screenshot 2024-04-01 142152](https://github.com/Dhanu654/EXNO2DS/assets/148514965/98904b6e-6069-4c97-a1ab-a99f94fe564e)

~~~
dt.boxplot(column="Age",by="Survived")
~~~
![Screenshot 2024-04-01 142201](https://github.com/Dhanu654/EXNO2DS/assets/148514965/bac18ead-b349-4c44-a78b-6c7a71fae17b)

~~~
sns.scatterplot(x=dt["Age"],y=dt["Fare"])
~~~
![Screenshot 2024-04-01 142209](https://github.com/Dhanu654/EXNO2DS/assets/148514965/5ff46d81-74a0-4bd1-9735-3b16217af504)

~~~
sns.jointplot(x=dt["Age"],y=dt["Fare"],data=dt)
~~~
![Screenshot 2024-04-01 142228](https://github.com/Dhanu654/EXNO2DS/assets/148514965/13c887f6-c071-44af-8e7b-f7644a72d7c6)


## MULTIVARIATE ANALYSIS

~~~
fig, ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=dt)
~~~
![Screenshot 2024-04-01 142239](https://github.com/Dhanu654/EXNO2DS/assets/148514965/065adddf-2696-4d7e-9e4e-ff4515319319)

~~~
sns.catplot(data=dt,col="Survived",x="Gender",hue="Pclass",kind="count")
~~~
![Screenshot 2024-04-01 142254](https://github.com/Dhanu654/EXNO2DS/assets/148514965/477f954b-6f92-48e0-bc1d-3d0feda36c2b)


~~~
corr=dt.corr()
sns.heatmap(corr,annot=True)
~~~
![Screenshot 2024-04-01 142331](https://github.com/Dhanu654/EXNO2DS/assets/148514965/50224e99-a7b5-40d6-8dc8-854c1dce2b79)


~~~
sns.pairplot(dt)
~~~
![Screenshot 2024-04-01 140825](https://github.com/Dhanu654/EXNO2DS/assets/148514965/9e87aaf2-b513-492a-80f3-dc34716b6c9d)




# RESULT
        Thus the  Exploratory Data Analysis on the given data set is successfully verified.

