# WORKSHOP
## NAME: K KESAVA SAI
## REGISTER NUMBER: 212223230105
AIM:
Data Cleaning and Data Analysis

EXPLANATION:
Data Cleaning involves detecting and correcting errors, inconsistencies, and inaccuracies in datasets to ensure high-quality, reliable data. Data Analysis is the process of examining, interpreting, and deriving meaningful insights from cleaned data to support decision-making or reveal patterns and trends.

ALGORITHM:
1.Collect Data: Gather raw data from various sources, ensuring it aligns with the objectives of the analysis.

2.Clean Data: Detect and handle missing values, outliers, duplicates, and correct inconsistencies (e.g., typos, wrong formats).

3.Transform Data: Normalize, scale, or encode data as needed to prepare it for analysis.

4.Analyze Data: Apply statistical methods, visualizations, or machine learning algorithms to uncover trends, relationships, or patterns.

5.Interpret Results: Summarize findings, draw insights, and report conclusions or recommendations based on the analysis.

CODING AND OUTPUT:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
dt=pd.read_csv('iottemp.csv')
dt
OUTPUT:
image

dt.shape
OUTPUT:
image

dt.rename(columns={'out/in':'status'},inplace=True)
dt
OUTPUT:
image

dt.isna().sum()
OUTPUT:
image

dt.info()
OUTPUT:
image

dt.describe()
OUTPUT:
image

dt.status.dropna(inplace=True)
dt.dtypes
OUTPUT:
image

dt.room_id.fillna(method='ffill',inplace=True)
OUTPUT:
image

dt.noted_date.fillna(method='ffill',inplace=True)
OUTPUT:
image

dt.status.unique()
OUTPUT:
image

dt.status.fillna(0,inplace=True)
dt.head(4)
OUTPUT:
image

dt.tail(4)
OUTPUT:
image

tp=dt.temp.median()
tp
OUTPUT:
image

dt.temp.fillna(tp,inplace=True)
dt.nunique()
OUTPUT:
image

sns.boxplot(data=dt['temp'])
OUTPUT:
image

sns.scatterplot(data=dt['temp'])
OUTPUT:
image

q1 = np.percentile(dt['temp'],25)
q3 = np.percentile(dt['temp'],75)
iqr = q3-q1
iqr
OUTPUT:
image

lower_bound = q1 - 1.5*iqr
upper_bound = q3 + 1.5*iqr
lower_bound
OUTPUT:
image

upper_bound
OUTPUT:
image

outliers = [x for x in dt['temp'] if x<lower_bound or x>upper_bound]
outliers
OUTPUT:
image

print("Q1:", q1)
print("Q3:",q3)
print("IQR:",iqr)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
OUTPUT:
image

dt['temp'].value_counts()
OUTPUT:
image image

dt=dt[(dt['temp']>=lower_bound) & (dt['temp']<=upper_bound)]
dt
OUTPUT:
image

dt['temp'].value_counts()
OUTPUT:
image image

sns.boxplot(data=dt['temp'])
OUTPUT:
image

sns.scatterplot(data=dt['temp'])
OUTPUT:
image

RESULT:
Hence, The Data Cleaning and Data Analysis of an given sample has been analised successfully.
