# Ex02 Outlier Detection
### AIM:  
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,
- (1) Remove outliers using IQR
- (2) After removing outliers in step 1, you get a new dataframe.
- (3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result
- (4) for the data set height_weight.csv find the following
  - (i) Using IQR detect weight outliers and print them
  - (ii) Using IQR, detect height outliers and print them
### Explanation:
An Outlier is an observation in a given dataset that lies far from the rest of the observations. That means an outlier is vastly larger or smaller than the remaining values in the set.
An outlier is an observation of a data point that lies an abnormal distance from other values in a given population. (odd man out).
Outliers badly affect mean and standard deviation of the dataset. These may statistically give erroneous results.
### Algorithm:
- Step1: Read the given Data.
- Step2: Get the information about the data.
- Step3: Detect the Outliers using IQR method and Z score.
- Step4: Remove the outliers.
- Step5: Plot the datas using Box Plot.
```

212222230073
LATHISH KANNA.M
```
### Code:
##### bhp.csv:
```Python
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('bhp.csv')
df.info()
print(df.describe())
df.head()
#BEFORE REMOVING OUTLIER
sns.boxplot(y='price_per_sqft',data=df)

# PERFORMING IQR METHOD
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
IQR=q3-q1
low=q1-1.5*IQR
high=q3+1.5*IQR
new=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]

#AFTER REMOVING OUTLIER using IQR method
sns.boxplot(y='price_per_sqft',data=new)

# PERFORMING Zscore METHOD
z=np.abs(stats.zscore(df['price_per_sqft']))
new2=df[(z<3)]

#AFTER REMOVING OUTLIER using Zscore method
sns.boxplot(y="price_per_sqft",data=new2)
```
##### height_weight.csv:
```Python
import pandas as pd
import seaborn as sns
from google.colab import files
uploaded=files.upload()
df=pd.read_csv('height_weight.csv')
df.info()
df.describe()
df.head()

#BEFORE REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
height_q1 = df['height'].quantile(0.25)
height_q3 = df['height'].quantile(0.75)
height_IQR = height_q3 - height_q1
height_low = height_q1 - 1.5 * height_IQR
height_high = height_q3 + 1.5 * height_IQR
height_new=df[((df['height']>=height_low)&(df['height']<=height_high))]
#AFTER REMOVING OUTLIER in HEIGHT
sns.boxplot(y='height',data=height_new)

#BEFORE REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=df)
#PERFORMING IQR METHOD ON HEIGHTS
weight_q1 = df['weight'].quantile(0.25)
weight_q3 = df['weight'].quantile(0.75)
weight_IQR = weight_q3 - weight_q1
weight_low = weight_q1 - 1.5 * weight_IQR
weight_high = weight_q3 + 1.5 * weight_IQR
weight_new=df[((df['weight']>=weight_low)&(df['weight']<=weight_high))]
#AFTER REMOVING OUTLIER in WEIGHT
sns.boxplot(y='weight',data=weight_new)
```
### Output:
## bhp.csv:

<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/5768615e-246e-4320-8f09-aa5765346efa">

<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/3bdef95e-fae0-47c1-b7b3-68f79bcceb30">

<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/6409d819-3af9-4a82-87fb-e9b92af337d1">

<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/c29237f2-9267-432c-84c4-6362f1d148af">

## weight_height.csv:

<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/b1382ef8-6c0e-4484-ae5f-00847ea61599">


<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/9bcbd4ae-a194-4773-9925-be6e19db3fd4">


<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/a6cb741b-1abe-4db2-9666-4ba8319b4cc9">

<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/f95aa03a-90ec-47ca-9415-3bcd1c847ca7">

<img height=30% width=70% src="https://github.com/abinayasangeetha/ODD2023---Datascience---Ex-02/assets/119393675/57e6a181-650d-45d7-8e79-adb323a64334">


### Result:
Hence the given set of data is read and the outliers are removed using the IQR method and Zscore method.
