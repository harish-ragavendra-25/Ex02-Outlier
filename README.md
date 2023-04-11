# Ex02-Outlier

# AIM:

You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR 

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

    (i) Using IQR detect weight outliers and print them

    (ii) Using IQR, detect height outliers and print them
    
# ALGORITHM:
## STEP1:
import the required packages(pandas,numpy,scipy)
## STEP2:
read the csv file.
## STEP3:
convert the file into dataframe and get the information of the data.
## STEP4:
remove the outliers in the data set using z scores method.
## STEP5:
check if the iutliers are removed from data set using graphiv=calmethods.
## STEP6:
save the final data set into the file.

# PROGRAM:
```
DEVELOPED BY: HARISH RAGAVENDRA S
REFERENCE NO: 212222230045
import pandas as pd
import seaborn as sns
import numpy as np
from scipy import stats
df=pd.read_csv('bhp.csv')
print(df['price_per_sqft'])
sns.boxplot(x="price_per_sqft",data=df)
df.shape
```

```
q1=df['price_per_sqft'].quantile(0.25)
q3=df['price_per_sqft'].quantile(0.75)
iqr=q3-q1
print("FIRST QUANTILE=",q1,"\nSECOND QUANTILE=",q3)
low=q1-1.5*iqr
high=q3+1.5*iqr
df_filtered=df[((df['price_per_sqft']>=low)&(df['price_per_sqft']<=high))]
sns.boxplot(x="price_per_sqft",data=df_filtered)
```

```
from scipy import stats
import numpy as np
z=np.abs(stats.zscore(df['price_per_sqft']))
df_filtered=df_filtered[(z<3)]
sns.boxplot(x='price_per_sqft',data=df_filtered)
```

```
q1=df.quantile(0.25)
q3=df.quantile(0.75)
iqr=q3-q1
low=q1-1.5*iqr
high=q3+1.5*iqr
df_fil=df[((df<=high)&(df>=low))]
outliers=np.setdiff1d(df['weight'],df_fil['weight'])
print("THE OUTLIERS IN THE DATA SET WEIGHT:",outliers)
```

```
q1=df.quantile(0.25)
q3=df.quantile(0.75)
iqr=q3-q1
low=q1-1.5*iqr
high=q3+1.5*iqr
df_fil=df[((df<=high)&(df>=low))]
outliers=np.setdiff1d(df['height'],df_fil['height'])
print("THE OUTLIERS IN THE DATA SET height:",outliers)
```
# OUTPUT:

 
![Screenshot from 2023-03-26 12-57-06](https://user-images.githubusercontent.com/114852180/227761904-52b40b9a-2d29-46e5-9f2c-c068a813dd9a.png)

![Screenshot from 2023-03-26 13-03-00](https://user-images.githubusercontent.com/114852180/227761953-5575612a-eed0-4338-b485-53ff467c3c2b.png)

![Screenshot from 2023-03-26 13-07-30](https://user-images.githubusercontent.com/114852180/227762186-2648ee9c-535a-4460-bb36-c9b5029080ea.png)

![Screenshot from 2023-03-26 13-13-20](https://user-images.githubusercontent.com/114852180/227762244-ce9ea4bf-f246-4388-925c-0827534cd2ae.png)

![Screenshot from 2023-03-26 13-14-40](https://user-images.githubusercontent.com/114852180/227762294-6c55c869-e20e-4a48-85b4-5479461311d5.png)


# RESULT:
thus the experiment executed sucessfully.
