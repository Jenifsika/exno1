# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
  import pandas as pd
  
  df=pd.read_csv("heights.csv")
  
  print(df.info())
  
  print(df.describe()) 
  
![image](https://github.com/user-attachments/assets/e2d25788-a2d2-42bb-b82a-ca6bcdc6493b)

print(df.isnull().sum())

![image](https://github.com/user-attachments/assets/d35b5b1c-7652-4fad-8a80-0441c0970e2e)

print(df.isnull().sum(axis=1))

![image](https://github.com/user-attachments/assets/20d17656-a9cc-44b8-82fe-79ff1a4ac527)

df=df.dropna()

df=df.fillna("O")

df=df.ffill()

df=df.bfill()

df.fillna(df.select_dtypes(include=['number']).mean(),inplace=True)

df=df.dropna()

print(df.head())

![image](https://github.com/user-attachments/assets/d522d9c8-0d72-4478-b31a-e0c8110500e2)

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

from scipy import stats

age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]

af=pd.DataFrame(age,columns=['Age'])

sns.boxplot(data=af,x='Age')

plt.show()

![image](https://github.com/user-attachments/assets/7ea430f1-f455-4319-a1ab-ef33f1eb33fe)

Q1=af['Age'].quantile(0.25)

Q3=af['Age'].quantile(0.75)

IQR=Q3-Q1

lower_bound=Q1-1.5*IQR

upper_bound=Q3+1.5*IQR

outliers=af[(af['Age']<lower_bound)| (af['Age']>upper_bound)]

print("Outliers detected using IQR:")

print(outliers)

![image](https://github.com/user-attachments/assets/03fa2e91-e472-48fc-9459-62d7617e8ed5)

af_cleaned=af[(af['Age']>= lower_bound)&(af['Age']<= upper_bound)]

sns.boxplot(data=af_cleaned,x='Age')

plt.show()

![image](https://github.com/user-attachments/assets/5e1d8182-c04c-4e81-a4d5-4b097cfeba38)

data=[1,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81,84,87,90,93,96,99,158]

df=pd.DataFrame(data,columns=['Values'])

sns.boxplot(data=df,x='Values')

plt.show()

     ![image](https://github.com/user-attachments/assets/40ce3c2d-bf21-4e97-9f1b-b8f0e933f02a)
     
z_scores=stats.zscore(df)

outliers_z=df[(z_scores>3)|(z_scores<-3)].dropna()

print(outliers_z)

![image](https://github.com/user-attachments/assets/2f4a7334-a138-4334-92af-d9879aa15e13)

df_cleaned =df[(z_scores <3)& (z_scores >-3)].dropna()

sns.boxplot(data=df_cleaned,x='Values')

plt.show()
![image](https://github.com/user-attachments/assets/05f24e1b-5124-43e1-9bfd-9238e9451610)

# Result

          Thus the program to read the given data and perform data cleaning and save the cleaned data to a file was written and executed successfully.
