# Exno:1 Data Cleaning Process

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
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![image](https://github.com/22008837/exno1/assets/120194155/d7f9a752-ca02-477b-8b9c-c440e3d56e9a)

```
data.isnull().sum()
```
![image](https://github.com/22008837/exno1/assets/120194155/3059164f-37c6-4f58-aae1-06433ae66467)

```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![image](https://github.com/22008837/exno1/assets/120194155/0c93023d-feea-4e3f-8336-71b492f67b00)

```
median = data[column].median()
data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![image](https://github.com/22008837/exno1/assets/120194155/100c9c3a-5fe3-4236-947f-4b3e8007588a)

```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris.csv")
ir.head()
```
![image](https://github.com/22008837/exno1/assets/120194155/c3c46aa3-6c31-4a80-bb8d-cde5988e4186)

```
ir.describe()
```
![image](https://github.com/22008837/exno1/assets/120194155/b7eac783-6562-4ca2-826f-e17f292ad6c0)

```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/22008837/exno1/assets/120194155/4f893d92-7d40-48e7-94ee-89b3e7a0c81a)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/22008837/exno1/assets/120194155/f7483579-4871-4d58-b5a9-5c46821b8c81)

```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/22008837/exno1/assets/120194155/4e511018-e703-454e-9ba3-5f15ec2ae618)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/22008837/exno1/assets/120194155/32ed4105-6f9e-4dc9-8e62-0cf619a36751)

```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/22008837/exno1/assets/120194155/379ef4ef-2cc6-4e4a-908c-50b85804e881)

```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/22008837/exno1/assets/120194155/662b3fcf-f6c2-42cc-86a1-65abb30d7e25)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```
```
iqr = q3-q1
iqr
```
![image](https://github.com/22008837/exno1/assets/120194155/fd8e98a9-6a8f-421c-9b85-f5c05f2b8055)

```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/22008837/exno1/assets/120194155/618605f8-46ea-4344-905c-fb648569d092)

```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/22008837/exno1/assets/120194155/84c2f920-0365-4d8a-a9ae-3f9fe1bc0eb0)

```
df.duplicated()
```
![image](https://github.com/22008837/exno1/assets/120194155/d5446c96-a88f-42e5-9591-530ab684290e)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/22008837/exno1/assets/120194155/9a58bdb9-0b05-4bab-8f74-198f85a0af61)

```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/22008837/exno1/assets/120194155/d8285560-ae61-47fa-a65d-ef686e31a2b9)

# Result
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
