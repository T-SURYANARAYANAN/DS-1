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
Register Number: 212224040341
```
```
import pandas as pd
df = pd.read_csv('/content/SAMPLEIDS (1).csv')
df
```
![image](https://github.com/user-attachments/assets/b6ad130f-2bf6-443e-8c7a-c49ea017fea2)
```
df.shape
```
![image](https://github.com/user-attachments/assets/1820582b-dc6d-4d72-b4ed-a70488ff2b36)
```
df.describe()
```
![image](https://github.com/user-attachments/assets/bf81c442-6347-41e2-9159-f2f26893934c)
```
df.info()
```
![image](https://github.com/user-attachments/assets/af3867fe-e74e-451e-9c28-55802c9a8d90)
```
df.head(10)
```
![image](https://github.com/user-attachments/assets/eebe6e99-3ed4-4c0d-b1ce-2741b6a498e8)
```
df.tail(10)
```
![image](https://github.com/user-attachments/assets/dca8c6b8-79bb-4876-acd2-b50374b26b41)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/39889440-740c-4197-8912-30961789468a)
```
df.dropna(how='any').shape
```
![image](https://github.com/user-attachments/assets/bbff146c-9e7b-4e54-ba89-7c2f49942cd5)
```
df.shape
```
![image](https://github.com/user-attachments/assets/168a1150-39d3-4e56-a6df-a049b1bda30d)
```
x = df.dropna(how='any')
x
```
![image](https://github.com/user-attachments/assets/0e420a44-9e3b-4ba8-b1d5-19740750aa5d)
```
mn = df.TOTAL.mean()
mn
```
![image](https://github.com/user-attachments/assets/fad7b0f2-6168-4608-9ccb-f49ccece3314)
```
df.TOTAL.fillna(mn,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/aaa69796-d9a9-4f6a-b71b-ea331c321002)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/12a85205-5fa8-4839-91f0-accd481b81ff)
```
df.M1.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/e40aa431-3de5-4cc1-b619-945ef79d44de)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/242a4048-d023-48e9-9366-21e4b19489e8)
```
df.M2.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/e51f2d3c-e3d6-4196-b1a7-b06493e9ecff)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/6dc01e18-f078-425e-b78e-fdf8532a01b4)
```
df.M3.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/28a74a95-e310-4da3-8c54-aecb3e3d97a7)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/21a82292-06b0-4be5-b4c4-c6be1e16e73e)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/910bc562-87b6-416d-8445-ff3b651fe361)
![image](https://github.com/user-attachments/assets/2052a9ff-3adc-48da-82f4-017dd2e0c68c)
```
df.drop_duplicates(inplace=True)
df
```
![image](https://github.com/user-attachments/assets/8090f90c-d930-4be3-98cb-5e65025dca51)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/28781ad1-b4b4-4bf9-a3d5-06574595f107)
![image](https://github.com/user-attachments/assets/7f72a230-b672-4b98-ab26-b62a63f38830)
```
df['DOB']
```
![image](https://github.com/user-attachments/assets/59228674-1fbe-46e3-bd7c-7cfab75a5b59)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/b80e0cf2-8ab9-4d93-8607-362e5f04b952)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/c266c266-a533-4fc6-8c80-ef2e48d2d85c)

```
# IMPLEMENTING OF DETECTION OF OUTLIER AND REMOVAL USING IQR.
age = [1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df = pd.DataFrame(age)
df
```
![image](https://github.com/user-attachments/assets/847d5154-4360-44f1-ac98-6ec22ac558be)
```
import seaborn as sns
import numpy as np
sns.boxplot(df)
```
![image](https://github.com/user-attachments/assets/cfc9aace-d5d9-47c2-aef3-f6bdb3f01476)
```
sns.scatterplot(df)
```
![image](https://github.com/user-attachments/assets/08eeff15-a7cc-47dd-b56d-2bfc15972548)
```
q1=df.quantile(0.25)
q2=df.quantile(0.50)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/12b12e14-6277-4cc0-a72e-aa22d7fbe510)
```
Q1 = np.percentile(df,25)
#Q2 = np.percentile(df,50)
Q3 = np.percentile(df,75)
IQR = Q3-Q1
print(IQR)
```
![image](https://github.com/user-attachments/assets/7472c3f8-e80b-4d24-8bd3-3a110f15b22e)
```
lower_bound = Q1-1.5*IQR
print(lower_bound)
```
![image](https://github.com/user-attachments/assets/b1c0dc03-18f9-4c71-b06f-1cffc5f8276c)
```
upper_bound = Q3+1.5*IQR
print(upper_bound)
```
![image](https://github.com/user-attachments/assets/82f62d3d-bbc4-4cd0-89c9-d34a0af0f313)
```
outliers = [x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/c493dd0b-a49c-468b-90a5-9e4e5c7b9306)
```
df = df[((df>=lower_bound) & (df<=upper_bound))]
df
```
![image](https://github.com/user-attachments/assets/590566c3-a536-40fa-8cb5-f5a7118183c8)
```
df.dropna()
```
![image](https://github.com/user-attachments/assets/7966f509-de0c-4142-8752-4c23ec35a391)
```
sns.boxplot(df)
```
![image](https://github.com/user-attachments/assets/f6f1c161-a013-48ae-902d-b5c34fb4ca37)
```
sns.scatterplot(df)
```
![image](https://github.com/user-attachments/assets/dd73ac21-a971-450e-894c-1571810cebe5)
```
# IMPLEMENTING OF DETECTION OF OUTLIER AND REMOVAL USING Z-SCORE.
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean = np.mean(data)
std = np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![image](https://github.com/user-attachments/assets/b8d2a28c-6441-4538-b796-6e4ec4146d24)
```
threshold = 3
outlier = []
for x in data:
  z = (x-mean)/std
  if(z >= threshold):
    outlier.append(x)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/fad2ffd3-d774-4f07-8192-2da56e214a68)
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/68cdb7c4-a68f-4f38-85cf-cb6ae499e3ee)
![image](https://github.com/user-attachments/assets/75eba5db-279c-4bc1-b7f3-737bd5c39523)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/user-attachments/assets/eefd4556-7181-4ce9-b666-c62143e2bc15)


# Result
          Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score Method
