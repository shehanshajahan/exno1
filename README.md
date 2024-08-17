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
Data Cleaning

import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
![image](https://github.com/user-attachments/assets/bcfec230-2858-4384-a146-6b425f51539c)

df.isnull()
![image](https://github.com/user-attachments/assets/37203415-a828-41ec-9780-13849620088a)

df.notnull()
![image](https://github.com/user-attachments/assets/5dab5d99-8541-43bb-b165-45f379d32625)

df.isnull().sum()
![image](https://github.com/user-attachments/assets/92e87ac0-1066-41a8-a925-180db8373e31)

df.isnull().any()
![image](https://github.com/user-attachments/assets/775bf6da-8c49-4f01-82c3-56c4fe204b51)

df.dropna()
![image](https://github.com/user-attachments/assets/775b3009-ae39-4535-9224-a335fca0455f)

df.fillna(0)
![image](https://github.com/user-attachments/assets/07eed205-7b65-4542-9926-c550e9c0ee63)

df.fillna(method = 'ffill')
![image](https://github.com/user-attachments/assets/e7f524cf-e21f-4fc2-8791-630dc23ce974)

df.fillna(method = 'bfill')
![image](https://github.com/user-attachments/assets/13f2b93d-d746-4305-abcf-c2fceb8648e1)

df_dropped = df.dropna()
df_dropped
![image](https://github.com/user-attachments/assets/fd70d6af-4cb6-43fc-9da1-69f3b9a99128)

df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':98,'M2':87,'M3':76,'M4':92,'TOTAL':305,'AVG':89.999999})
![image](https://github.com/user-attachments/assets/b45e5b96-1f59-4ac7-a39c-dc247c96fac5)

IQR(Inter Quartile Range)

import pandas as pd
ir=pd.read_csv('iris.csv')
ir
![image](https://github.com/user-attachments/assets/c98b25d3-25c9-47f0-bbae-7654311c2d29)

ir.describe()
![image](https://github.com/user-attachments/assets/5cfde0bf-d9ce-4c43-b93d-797198a7623b)

import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
![image](https://github.com/user-attachments/assets/ae8641a4-edfe-423c-bd6a-d48414ed6e17)

c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
![image](https://github.com/user-attachments/assets/a822285a-a229-4bdf-b043-8bb777316bda)

rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
![image](https://github.com/user-attachments/assets/0382dbf6-ceb6-49c3-98e5-4e5e220ca65f)

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
![image](https://github.com/user-attachments/assets/5c5d59b9-0259-474e-ae5e-45985e8c76b4)

sns.boxplot(x='sepal_width',data=delid)
![image](https://github.com/user-attachments/assets/775a823e-47d8-4874-aa08-f88323cd5ea0)

Z-Score

import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats

dataset=pd.read_csv("heights.csv")
dataset
![image](https://github.com/user-attachments/assets/c7bb5a57-4394-4372-99eb-6261a3a0120b)

z = np.abs(stats.zscore(df['height']))
z
![image](https://github.com/user-attachments/assets/d7c6bd18-9a7c-4e23-9493-2a1ca9e5ba14)

# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
