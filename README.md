## EXNO-3-DS

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
```
import pandas as pd
import numpy as np
df=pd.read_csv('/content/Encoding Data.csv')
df
```

<img width="345" height="445" alt="image" src="https://github.com/user-attachments/assets/94359e0b-8ce2-4e4b-9852-0d1392ea3334" />

```

from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm_corrected])
e1.fit_transform(df[["ord_2"]])
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
enc=pd.DataFrame(ohe.fit_transform(df[['nom_0']]))
df=pd.concat([df,enc],axis=1)
df
```

<img width="524" height="427" alt="image" src="https://github.com/user-attachments/assets/5d0cdb22-5687-4ef9-9227-57b72ce4d701" />


```
pd.get_dummies(df,columns=["nom_0"])
```

<img width="792" height="449" alt="image" src="https://github.com/user-attachments/assets/9cdf8470-345e-4c1b-86c1-3377cc508ce7" />


```
pip install --upgrade category_encoders
```
```
from category_encoders import BinaryEncoder
df=pd.read_csv('/content/data.csv')
df

```

<img width="596" height="431" alt="image" src="https://github.com/user-attachments/assets/fe204454-136c-4e2a-9ac6-17468f826ea1" />


```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```

<img width="838" height="423" alt="image" src="https://github.com/user-attachments/assets/fa3d33aa-8509-41c3-90d8-ef1594f6d2e6" />


```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc["City"],y=cc["Target"])
cc=pd.concat([cc,new],axis=1)
cc
```

<img width="684" height="440" alt="image" src="https://github.com/user-attachments/assets/495c7cbe-fcd8-464f-aa5a-acd6d49ffd3f" />


```
import pandas as pd
import numpy as np
import scipy as stats
df=pd.read_csv("/content/Data_to_Transform.csv")
df
```

<img width="720" height="518" alt="image" src="https://github.com/user-attachments/assets/c6b4d891-8f37-4fe8-b1bf-4135882bcbe2" />


```
df.skew()
```

<img width="362" height="241" alt="image" src="https://github.com/user-attachments/assets/5e38307f-e1b6-4c1c-aa18-600ba3412726" />


```
np.log(df["Highly Positive Skew"])
```

<img width="323" height="554" alt="image" src="https://github.com/user-attachments/assets/2acb7129-d703-4aa8-9528-7693e2894b8d" />


```
np.reciprocal(df["Moderate Positive Skew"])
```

<img width="338" height="546" alt="image" src="https://github.com/user-attachments/assets/2b3ee705-ae41-4316-ad1c-db649a34b998" />


```
np.sqrt(df["Highly Positive Skew"])
```

<img width="291" height="548" alt="image" src="https://github.com/user-attachments/assets/27193657-43dd-41e6-afd6-f3c7971b25f3" />


```
np.square(df["Highly Positive Skew"])
```

<img width="300" height="566" alt="image" src="https://github.com/user-attachments/assets/8b9a0b43-6c66-4d8a-9333-ec584d776562" />


```
from scipy.stats import boxcox
df["Highly Positive Skew_boxcox"],parameters=boxcox(df["Highly Positive Skew"])
df
```

<img width="714" height="552" alt="image" src="https://github.com/user-attachments/assets/7c51315c-ef4b-415c-85fa-e5e7214a765a" />

```
from scipy.stats import yeojohnson
df["Highly Negative Skew_yeojohnson"],parameters=yeojohnson(df["Highly Negative Skew"])
df
```

<img width="724" height="557" alt="image" src="https://github.com/user-attachments/assets/eae116f6-7501-4c49-aee1-e2e9a62e3b1c" />


```
df.skew()
```

<img width="432" height="320" alt="image" src="https://github.com/user-attachments/assets/80a5a3a5-dfb4-4f2b-9d0a-5d173bbc971a" />


```
from scipy.stats import yeojohnson
df["Highly Negative Skew_yeojohnson"],parameters=yeojohnson(df["Highly Negative Skew"])
df
```

<img width="729" height="560" alt="image" src="https://github.com/user-attachments/assets/3396cb68-5287-41ba-b6eb-d3681f4dbf21" />


```
df.skew()
```

<img width="438" height="319" alt="image" src="https://github.com/user-attachments/assets/66b712da-4142-47fd-92e3-b28c636d28a2" />


```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
```
<img width="1679" height="520" alt="image" src="https://github.com/user-attachments/assets/0e29e947-c2bd-45cd-86c4-f9284d583316" />


```
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
```
<img width="744" height="568" alt="image" src="https://github.com/user-attachments/assets/882254c3-ac21-4ac3-888d-fbc5edb17b2e" />

```
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
```
<img width="736" height="560" alt="image" src="https://github.com/user-attachments/assets/51c08b26-7ee5-4e02-bf75-e0b5ab9bce34" />


```
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
```

<img width="730" height="554" alt="image" src="https://github.com/user-attachments/assets/cbebdd11-d08c-4ee1-8f73-d5e97963bfbd" />



# RESULT:
    Thus we read the given data and perform Feature Encoding and Transformation process and save the data to a file.

       
