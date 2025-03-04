# Ex-01_DS_Data_Cleansing

Name : NANDHIKA P
Reg no : 212223040125

## AIM
To read the given data and perform data cleaning and save the cleaned data to a file. 

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. 
Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information. 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Get the information about the data
### STEP 3
Remove the null values from the data
### STEP 4
Save the Clean data to the file

# CODE and OUTPUT

```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/cca2db3d-1805-48eb-834b-e959a0dde974)

```
df.head(6)
```

![image](https://github.com/user-attachments/assets/cc23c979-34f1-471c-bbc5-af1ee17e12de)

```
df.tail(5)
```

![image](https://github.com/user-attachments/assets/f573789f-c186-40e9-bb9a-4619e5fee2a2)

```
df.isnull()
```

![image](https://github.com/user-attachments/assets/cc7cc58d-c9f9-4575-9d83-d5d81f05c2d5)

```
df.isnull().sum()
```

![image](https://github.com/user-attachments/assets/f902577c-8140-4d5d-917d-53730e32c4e2)

```
df.isnull().any()
```

![image](https://github.com/user-attachments/assets/f03e6cad-2790-4d5e-9eb8-5a5152356fed)

```
df.dropna()
```

![image](https://github.com/user-attachments/assets/d81c43c3-df1a-475d-ab1c-bd6551e41915)

```
df.fillna(0)
```

![image](https://github.com/user-attachments/assets/e6bc8d1a-1e56-4322-8c66-c48c8c52ca24)

```
df.fillna(method = 'ffill')
```

![image](https://github.com/user-attachments/assets/1c84a3b2-151f-4dc7-b6a0-406bc670a5c1)

```
df.fillna(method = 'bfill')
```

![Screenshot 2025-03-04 110324](https://github.com/user-attachments/assets/f24a8b49-c7c9-4965-89d7-713f402d5735)

```
df_dropped=df.dropna()
df_dropped
```

![image](https://github.com/user-attachments/assets/ed7089ea-cb2d-42e5-8df0-321f42ecf4a4)

```
df.fillna({'GENDER':'FEMALE', 'NAME':'MATHI','ADDRESS':'KANCHIPURAM','M1':97,'M2':98.5,'M3':75,'M4':85,'TOTAL':315,'AVG':85.79999})
```

![image](https://github.com/user-attachments/assets/4f0225ec-adf7-44d4-a679-c4033c1a5a62)

## IQR (Inter Quartile Range)

```
import pandas as pd
ir=pd.read_csv("/content/iris.csv")
ir
```

![image](https://github.com/user-attachments/assets/c0958171-c2e3-46f2-b614-30f591e2e4b1)

```
df.describe()
```

![image](https://github.com/user-attachments/assets/b4617801-40ec-42c5-b452-2452b923aca0)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/a407b3e5-3ad8-4795-8ee8-5977e773f8ba)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

![image](https://github.com/user-attachments/assets/232ad118-8b7c-4ece-90d2-f66223b1b2f3)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

```

![image](https://github.com/user-attachments/assets/52c07ff3-a5d9-4741-b0a8-9b5c46154efe)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![image](https://github.com/user-attachments/assets/9f90afa0-9a94-46be-a6f5-249acf0ea11f)

```
sns.boxplot(x='sepal_width',data=delid)
```

![image](https://github.com/user-attachments/assets/33652adc-d3fd-4413-a455-e129aeb07d8a)

## Z-Score

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

ht=pd.read_csv("/content/heights.csv")
ht

```

![image](https://github.com/user-attachments/assets/c002ab92-d025-4d92-9b57-0e2d1bb7a83d)

```
df=pd.read_csv("/content/heights.csv")
q1=df['height'].quantile(0.25)
q2=df['height'].quantile(0.5)
q3=df['height'].quantile(0.75)

iqr=q3-q1
iqr
```

![image](https://github.com/user-attachments/assets/dfed64d3-65db-417f-835a-7ef4c449df7b)

```
low=q1-1.5*iqr
low
```

![image](https://github.com/user-attachments/assets/668349ef-9bb6-4ac5-bfed-3a90f1217283)

```
high=q3+1.5*iqr
high
```

![image](https://github.com/user-attachments/assets/5f6b2890-82da-4f73-b19c-17351f08d6a9)

```
df1=df[((df['height'] >=low) & (df['height'] <= high ))]
df1
```

![image](https://github.com/user-attachments/assets/572f383a-0096-48bc-be32-811a1e1906de)


```
z = np.abs(stats.zscore(ht['height']))
z
```

![image](https://github.com/user-attachments/assets/899666e4-378e-4e8d-ada5-e318f40793ff)

```
ht1=ht[z<3]
ht1
```

![image](https://github.com/user-attachments/assets/136e8860-e3e4-46ec-9fc4-455da4343e0e)


## RESULT 

Thus we have cleaned tha data and removed the outliners by detection using IQR and Z-score method.




