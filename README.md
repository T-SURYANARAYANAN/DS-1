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
```
Name : SURYANARAYANAN T
Reg No : 212224040341
```
import pandas as pd
import numpy as np
df = pd.read_csv("/content/SAMPLEIDS (1).csv")
df

![Screenshot 2025-04-21 094528](https://github.com/user-attachments/assets/e8e1cf9e-1a0f-4046-be8f-b560f96e63e7)

df.shape

![image](https://github.com/user-attachments/assets/0311a062-39f9-444b-a63e-aa2b2a584781)

df.describe()

![image](https://github.com/user-attachments/assets/474549cd-6b97-4025-a2e0-f1f200cefc31)

df.info()

![image](https://github.com/user-attachments/assets/92f9c487-da05-4741-9d0b-a652da21d117)

df.head(10)

![image](https://github.com/user-attachments/assets/c2533d0b-35b9-4247-aef2-e35bd2d78af5)

df.tail(10)

![image](https://github.com/user-attachments/assets/79c6ce56-abd0-43ce-a4c0-bcfe7270784c)

df.isna().sum()

![image](https://github.com/user-attachments/assets/b7992120-965b-45a5-81f3-2c99a4c07136)

df.dropna(how='any').shape
![image](https://github.com/user-attachments/assets/c6dc5d0f-c35a-40bc-8534-8423f50a33dc)

df.shape

![image](https://github.com/user-attachments/assets/5ee4c7e6-b14a-4286-95de-ffe3e0169326)

x = df.dropna(how='any')
x

![image](https://github.com/user-attachments/assets/e5eb0a74-e131-456e-80a0-9ec691346b86)

mn=df.TOTAL.mean()
mn

![image](https://github.com/user-attachments/assets/ae907e43-25c1-4826-acfb-d9c4e654a9f2)

df.TOTAL.fillna(mn,inplace=True)
df

![image](https://github.com/user-attachments/assets/f1efba75-d4bc-4dea-8f1c-056a8136791f)

df.isnull().sum()

![image](https://github.com/user-attachments/assets/67ecea13-8390-4b08-8201-5280885ef91f)

df.M1.fillna(method='ffill',inplace=True)
df

![image](https://github.com/user-attachments/assets/04c7dba7-00a3-46dc-8878-9332de86b7e1)

df.isnull().sum()
df.M2.fillna(method='ffill',inplace=True)
df

![image](https://github.com/user-attachments/assets/121dacd6-bb3e-4b1b-a796-5516c03efe00)

df.isna().sum()

![image](https://github.com/user-attachments/assets/863a01ee-1668-4547-ba64-ea4aafd30c1a)

df.M3.fillna(method='ffill',inplace=True)
df

![image](https://github.com/user-attachments/assets/48fabc1f-4edd-483d-8b65-62a44b349e52)

df.isnull().sum()

![image](https://github.com/user-attachments/assets/51457d8e-fa47-4ab7-9a1e-329e0c98e74f)

df.duplicated()

![image](https://github.com/user-attachments/assets/15c7a22a-2d14-4a0c-b4a3-b3c38d9fbcd0)

df.drop_duplicates(inplace=True)
df

![image](https://github.com/user-attachments/assets/64f94e6d-cada-4593-b40b-27ae53214717)

df.duplicated()

![image](https://github.com/user-attachments/assets/53f5d601-26de-4914-b898-ffb689e49635)

df['DOB']

![image](https://github.com/user-attachments/assets/e7f54ba4-1f8c-49b7-8065-36b34631aaed)

import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)

![image](https://github.com/user-attachments/assets/4f34f0a2-e9eb-4fa8-8b90-22e364f807c2)

df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)

![image](https://github.com/user-attachments/assets/9a718b90-24eb-4e8a-8e7b-e6c972e46ec7)

#0UTLIERS DETECTION AND REMOVAL USING IQR
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df

![image](https://github.com/user-attachments/assets/17fc9506-89fb-47dc-8ba6-2abeadad7d5c)

sns.boxplot(data=df)

![image](https://github.com/user-attachments/assets/d2dfab12-a3e8-431b-bcb1-b42318990175)

sns.scatterplot(data=df)

![image](https://github.com/user-attachments/assets/f23b0991-0200-4ee1-9905-3d4fc98e60c6)

q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr

![image](https://github.com/user-attachments/assets/c7adcc84-e02c-4049-8e09-c1fa44824603)

Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR

![image](https://github.com/user-attachments/assets/797eb855-25ce-43b4-9476-436346bb2f2b)

lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound

![image](https://github.com/user-attachments/assets/e047fa1f-3b7b-4fca-a33d-d64f8b609008)

upper_bound

![image](https://github.com/user-attachments/assets/175d767c-3e51-476a-91cb-7fd2a4daf047)

outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)

![image](https://github.com/user-attachments/assets/0059189f-19f9-4595-80fe-ae59ed5542cb)

df=df[((df>=lower_bound)&(df<=upper_bound))]
df

![image](https://github.com/user-attachments/assets/76c0a623-a336-4757-b1d2-ff9168546380)

df=df.dropna()
df

![image](https://github.com/user-attachments/assets/805620a3-f10f-449a-9376-e7fb34cfb48c)

sns.boxplot(data=df)

![image](https://github.com/user-attachments/assets/44bf09c7-0c5c-4e65-baa9-ebc4e8f593ca)

sns.scatterplot(data=df)

![image](https://github.com/user-attachments/assets/80ff3a13-bca3-4d5c-ac6e-1843482120d2)

data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)

![image](https://github.com/user-attachments/assets/7ca867f7-f55a-4e1e-833a-1394e112d1b9)

threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)

![image](https://github.com/user-attachments/assets/ba49ecb7-87e7-4fd1-837c-24f8d65c49c9)

import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
                66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df

![image](https://github.com/user-attachments/assets/fea7bba4-f611-4c5f-af45-5442888988b8)

z=np.abs(stats.zscore(df))
print(df[z['weight']>3])

![image](https://github.com/user-attachments/assets/42a9411c-c7f3-4629-ba9e-0e746ef2fb67)


# Result
    Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score
