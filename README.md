# EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
       # INCLUDE YOUR CODING AND OUTPUT SCREENSHOTS HERE
## FEATURE ENCODING:
### 1.Ordinal Encoding
```
import pandas as pd
df=pd.read_csv('/content/Encoding Data.csv')
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Blue','Green','Red']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["nom_0"]])
df['bo2']=e1.fit_transform(df[["nom_0"]])
df
```
![320215684-077d5518-ee17-43b4-85c6-fb6f454df195](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/60030bbd-3270-43ad-8410-95836fd205b9)
### 2.Label Encoding
```
le=LabelEncoder()
dfc=df.copy()
dfc['nom_0']=le.fit_transform(dfc['nom_0'])
dfc
```
![320215692-fc627ee4-c01e-45ec-b7ac-52b0b2699ca8](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/6b430907-a9d1-4f35-9f86-4ce5ef443aba)
### 3.Binary Encoding:
```
from category_encoders import BinaryEncoder
df=pd.read_csv("/content/data.csv")
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_1'])
df1=pd.concat([df,nd],axis=1)
df2=df.copy()
df1
```
![320215706-307186c2-73e4-4937-85b2-93eae41a9789](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/971a4c27-02a6-45be-99c8-bbdc23239c3b)
### 4.One Hot Encoding:
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=dfc.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['ord_2']]))
df2=pd.concat([df2,enc],axis=1)
pd.get_dummies(df2,columns=["ord_2"])
df2
```
![320215711-2ae779d7-e5cf-49ad-85fb-9ce9a067fd02](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/acdceb28-c8bf-40c1-be57-598215e52a47)
### Feature Transformation:
### Log Transformation:
```
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("/content/Data_to_Transform.csv")
df.skew()
np.log(df["Highly Negative Skew"])
```
![image](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/e3ebbfcc-e33d-4352-8e68-38d3e99d3d30)

### Reciprocal Transformation:
```
np.reciprocal(df["Moderate Positive Skew"])
```
![image](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/288ac7c7-7abe-464c-89f0-b7c2ec525096)
### Square Root Transformation:
```
np.sqrt(df1['Highly Positive Skew'])
```
![image](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/5cd4ca61-454f-4bca-9f2b-37d4b8a06e3b)
### Yeojohnson method:
```
df1['Highly Positive Skew_yeojohnson'], parameters=stats.yeojohnson(df1['Highly Positive Skew'])
df1.skew()
```
![image](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/995057de-0c9a-40c9-ac0a-79527b0d207a)
### Boxcox method"
```
df1['Highly Positive Skew_boxcox'], parameters=stats.boxcox(df1['Highly Positive Skew'])
df1
```
![image](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/25384c08-7013-4f75-95ca-5b7c76f02231)
### Quantile Transformation:
```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df1['Highly Positive Skew'],fit=True,line='45')
plt.show()
```
![image](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/b65151fe-1a4e-41f1-ba31-873293dd4fa8)
```
sm.qqplot(np.reciprocal(df1['Highly Positive Skew']),fit=True,line='45')
plt.show()
```
![image](https://github.com/Kowsalyasathya/EXNO-3-DS/assets/118671457/0b72642e-5a85-4f6b-8110-1ac997b365cc)

# RESULT:
Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

       
