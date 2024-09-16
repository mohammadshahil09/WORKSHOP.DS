## Workshop:
```PY
## NAME: K KESAVA SAI
## REGISTER NUMBER: 212223230105
```
## AIM:
 Data Cleaning and Data Analysis 
## EXPLANATION:

Data Cleaning involves detecting and correcting errors, inconsistencies, and inaccuracies in datasets to ensure high-quality, reliable data.
Data Analysis is the process of examining, interpreting, and deriving meaningful insights from cleaned data to support decision-making or reveal patterns and trends.

## ALGORITHM:
1.Collect Data: Gather raw data from various sources, ensuring it aligns with the objectives of the analysis.

2.Clean Data: Detect and handle missing values, outliers, duplicates, and correct inconsistencies (e.g., typos, wrong formats).

3.Transform Data: Normalize, scale, or encode data as needed to prepare it for analysis.

4.Analyze Data: Apply statistical methods, visualizations, or machine learning algorithms to uncover trends, relationships, or patterns.

5.Interpret Results: Summarize findings, draw insights, and report conclusions or recommendations based on the analysis.

## CODING AND OUTPUT:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

```py
dt=pd.read_csv('iottemp.csv')
dt
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/b3adba2c-d9f9-4d96-b807-5e5395ac3218)

```py
dt.shape
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/efd5f88f-d0da-4267-bd45-647d8ae990ee)

```py
dt.rename(columns={'out/in':'status'},inplace=True)
dt
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/335490ae-2fd9-46e1-bc6f-ae36753bf9e0)

```PY
dt.isna().sum()
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/0fa3f278-2d18-4244-b140-e5b3a346e100)

```PY
dt.info()
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/013a6df4-b367-47b8-8839-78506b102a6c)

```PY
dt.describe()
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/b0133042-ef9d-4e5b-821c-3032a0b204ec)

```PY
dt.status.dropna(inplace=True)
```

```PY
dt.dtypes
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/25392f10-977a-49dd-8ce4-deb17e6b57f7)

```PY
dt.room_id.fillna(method='ffill',inplace=True)
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/cacd9ff8-d172-44fa-a7cc-28166365b34c)

```PY
dt.noted_date.fillna(method='ffill',inplace=True)
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/b1591a17-4f82-43ca-b5ff-b26006d27e5a)

```PY
dt.status.unique()
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/0fc50e76-9503-4ead-8919-8ae9494fa69f)

```PY
dt.status.fillna(0,inplace=True)
```

```PY
dt.head(4)
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/1f06cf91-f39c-4b90-8ae2-b1c7bfd84970)

```PY
dt.tail(4)
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/29b985a0-b9ca-4b93-b7b7-9b3f3f193fb0)

```PY
tp=dt.temp.median()
tp
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/51702853-1e38-494f-88d4-690f6b2a6e2c)

```PY
dt.temp.fillna(tp,inplace=True)
```

```PY
dt.nunique()
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/cba7d92a-3ee4-484f-988a-fa334fc49a86)

```PY
sns.boxplot(data=dt['temp'])
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/59b4631b-ca46-475e-b611-5d76fee892f7)

```PY
sns.scatterplot(data=dt['temp'])
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/3be56e37-e5d2-4439-acd3-4673414b843a)

```PY
q1 = np.percentile(dt['temp'],25)
q3 = np.percentile(dt['temp'],75)
iqr = q3-q1
iqr
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/07537a91-a5a6-4785-9ef8-5cb266f6f8e8)

```PY
lower_bound = q1 - 1.5*iqr
upper_bound = q3 + 1.5*iqr
```

```PY
lower_bound
```
## OUTPUT:
![image](https://github.com/user-attachments/assets/c6e67217-72ac-4f22-89ff-b5c1042d4079)

```PY
upper_bound
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/2dd5a0f9-1bf6-41b2-a41b-a1fcccde5289)

```PY
outliers = [x for x in dt['temp'] if x<lower_bound or x>upper_bound]
outliers
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/295665ad-c7b5-4095-b691-eed257c6117c)

```PY
print("Q1:", q1)
print("Q3:",q3)
print("IQR:",iqr)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/7b0e2f5a-1e95-48a2-aacb-d20595ec0296)

```PY
dt['temp'].value_counts()
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/f22e3425-3825-448e-a2b7-0c93882cf66d)
![image](https://github.com/user-attachments/assets/5c450e0c-9d8f-4b87-98c0-9590811352d1)

```PY
dt=dt[(dt['temp']>=lower_bound) & (dt['temp']<=upper_bound)]
dt
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/02a7e701-3d7c-4980-a8f9-6c242d7dad35)

```PY
dt['temp'].value_counts()
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/5f81d82d-a308-48a1-ba14-684956eb979e)
![image](https://github.com/user-attachments/assets/242d8238-c089-403b-a8ed-737b111d30f7)

```PY
sns.boxplot(data=dt['temp'])
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/bfc08d66-cf19-4d57-ae58-5c4e167ae8cc)

```PY
sns.scatterplot(data=dt['temp'])
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/b06b6849-f29a-4063-81bd-1a89c1303a2f)

## RESULT:
Hence, The Data Cleaning and Data Analysis of an given sample has been analised successfully.
