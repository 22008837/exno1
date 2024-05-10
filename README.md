# Ex.no:1 Data Cleaning Process

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
![image](https://github.com/22008837/exno1/assets/120194155/fd3c6cca-6e23-438e-9472-4023c2ff513f)
```
data.isnull().sum()
```
![image](https://github.com/22008837/exno1/assets/120194155/b96050db-2cd4-4d6e-9ff6-bb04b74253e0)
```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![image](https://github.com/22008837/exno1/assets/120194155/cc44b0eb-0cc9-47a6-8df0-0add6c14f39b)
```
median = data[column].median()
data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![image](https://github.com/22008837/exno1/assets/120194155/c2567409-7bb4-4705-a745-d32ab89ac972)
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris.csv")
ir.head()
```
![image](https://github.com/22008837/exno1/assets/120194155/949772bd-ef88-46e0-a388-ffcdf6351721)
```
ir.describe()
```
![image](https://github.com/22008837/exno1/assets/120194155/19bf22a6-98a2-454e-911f-be7109a26e3c)
```
sns.boxplot(x='sepal_width',data=ir)
```
![image](https://github.com/22008837/exno1/assets/120194155/0ecdaa97-9e90-40df-8380-ebbfe2c00ffa)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/22008837/exno1/assets/120194155/05fbd862-0405-40f9-9121-8f652eb4fc22)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/22008837/exno1/assets/120194155/b1305c3a-6017-46d7-8148-cf878315a59c)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/22008837/exno1/assets/120194155/bd0c8b26-f8a6-46f9-a2c4-1f9061f91423)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/22008837/exno1/assets/120194155/5f7abd44-3312-4223-ad6b-2a7da6f6dcbb)
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/22008837/exno1/assets/120194155/84673890-4b51-4655-a26b-f238734b4f4a)
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
![image](https://github.com/22008837/exno1/assets/120194155/1a31fe0b-4acb-44c1-a638-1c680805b055)
```
low = q1 - 1.5*iqr
low
```
![image](https://github.com/22008837/exno1/assets/120194155/6366d5fd-75c8-4323-89f2-c083548b153b)
```
high = q3 + 1.5*iqr
high
```
![image](https://github.com/22008837/exno1/assets/120194155/b0109de2-e8c3-4232-ad79-da9868e577f5)
```
df.duplicated()
```
![image](https://github.com/22008837/exno1/assets/120194155/52013485-fb4e-4f90-9095-6f2d969abe58)
```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```
![image](https://github.com/22008837/exno1/assets/120194155/5ecb3cac-4e80-4715-be77-26efbd76e531)
```
z = np.abs(stats.zscore(df['height']))
z
```
![image](https://github.com/22008837/exno1/assets/120194155/e03d2f2e-536d-4d09-91a9-2a5941ae4bcd)

# Result
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.
