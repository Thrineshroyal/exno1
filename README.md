# Exno:1
Data Cleaning Process
# Developed by:
```
NAME:Thrinesh Royal
REG.NO:212223230226
```
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

# Coding and Output:
# Reading the data set:
```
import pandas as pd
import seaborn as sns
import numpy as np

df=pd.read_csv("SAMPLEIDS.csv")
df
```
# Output:
![image](https://github.com/user-attachments/assets/5308aff5-e890-4ea3-802c-4d15603dc1a0)

# Initializing id=column
```
id=df['M4']
id
```
# Output:
![image](https://github.com/user-attachments/assets/2c6bbcca-5238-43e9-8142-8ddc68f4c770)

# sns graphs:
![image](https://github.com/user-attachments/assets/b7ae0e2b-9810-4652-af2c-30343abb8ef2)


![image](https://github.com/user-attachments/assets/e5126eef-5f24-4836-bc0e-6bbcafca9965)


![image](https://github.com/user-attachments/assets/893c0331-1acf-4be1-a5ae-3f40dad53adb)

# Quantile and IQR:
```
q1=id.quantile(0.25)
q2=id.quantile(0.5)
q3=id.quantile(0.75)
iqr=q3-q1
iqr
```
# Output:
![image](https://github.com/user-attachments/assets/7c1e35ad-f666-4df7-91a6-d6a2cde875c5)

# Declaring bounds:
```
lower_bound=q1-1.5*iqr
upper_bound=q3+1.5*iqr
lower_bound,upper_bound
```
# Output:
![image](https://github.com/user-attachments/assets/3bb1dd1a-fbbd-4718-a867-6d383b9555c6)

# Outliers:
```
outliers=[x for x in id if x<lower_bound or x>upper_bound]
print("Outliers:",outliers)
```

# Output:
![image](https://github.com/user-attachments/assets/52e1be41-f011-4f0e-93b0-38514d68a02d)

# Dropna function to remove any null values:
```
id.dropna()
```
# Output:
![image](https://github.com/user-attachments/assets/9786f80b-feea-45f8-8b83-e95d72d3734e)

# Printing all requird values:
```
print("Q1:",q1)
print("Q2:",q2)
print("Q3:",q3)
print("IQR:",iqr)
print("lower_bound:",lower_bound)
print("upper_bound:",upper_bound)
print("Outliers",outliers)

```
# Output:
![image](https://github.com/user-attachments/assets/fa35b17b-895e-4d68-bf15-c4feabd505e9)

# Checking for any outliers at the end:
```
sns.boxplot(id)
```
# Output:
![image](https://github.com/user-attachments/assets/c13b9b52-baec-450b-bfe8-b83560b47473)

# Calculating Z_score:
```
import scipy.stats as stats
import pandas as pd
import numpy as np


mean = df['M4'].mean()
std_dev = df['M4'].std()

df['z_score'] = (df['M4'] - mean) / std_dev

print(df)

z = np.abs(stats.zscore(df['M4']))
z
```

# Output:
![image](https://github.com/user-attachments/assets/868917ee-206d-4512-8933-2d6a83af95bc)


# Result:
Thus we have cleaned the data and remove the outliers by detection using IQR and Z-score method.
