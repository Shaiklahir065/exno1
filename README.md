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

```
NAME:Shaik Lahir
REG:212224240148
```

```c
import pandas as pd
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="797" height="617" alt="image" src="https://github.com/user-attachments/assets/7311480b-6c64-4b40-aef7-86912cd1fc46" />

```c
df.head()
```

<img width="766" height="184" alt="image" src="https://github.com/user-attachments/assets/68bcdf3a-b8da-450c-bc6c-1a476ee06c28" />

```c
df.tail()
```

<img width="784" height="171" alt="image" src="https://github.com/user-attachments/assets/98e7d098-78bd-436f-bbe8-b507d8f9fc87" />

```c
df.info()
```

<img width="401" height="358" alt="image" src="https://github.com/user-attachments/assets/f5a23ed8-5518-4045-b06e-35efb982a59d" />

```c
df.describe()
```

<img width="690" height="248" alt="image" src="https://github.com/user-attachments/assets/233af4ab-dc8e-4785-a08e-844bedb3e11a" />

```c
df.isnull().sum()
```

<img width="239" height="249" alt="image" src="https://github.com/user-attachments/assets/204a5298-61a4-41d9-a6e2-c19786203070" />

```c
df.isnull().any()
```

<img width="227" height="248" alt="image" src="https://github.com/user-attachments/assets/fee41fa6-6efd-4112-9603-379f28dc3657" />

```c
df.dropna()
```

<img width="805" height="414" alt="image" src="https://github.com/user-attachments/assets/564f5569-217c-4a40-b862-58820f7604e9" />

```c
df.fillna(0)
```

<img width="808" height="632" alt="image" src="https://github.com/user-attachments/assets/1bc67a80-e79e-4be4-beef-4ec69251e676" />

```c
df.fillna(method='ffill')
```

<img width="775" height="629" alt="image" src="https://github.com/user-attachments/assets/bfa4afc4-0b46-4bcc-9e37-64a355b5f9cc" />

```c
df.fillna({'GENDER':'MALE','NAME':'SRI'})
```

<img width="825" height="635" alt="image" src="https://github.com/user-attachments/assets/199285c8-aefe-480d-9f20-ceb909caeaad" />

```c
ir=pd.read_csv("iris.csv")
ir
```

<img width="528" height="382" alt="image" src="https://github.com/user-attachments/assets/3f67fc4e-8df4-4bae-b73e-d1b2c6c5a9ca" />

```c
ir.describe()
```

<img width="440" height="261" alt="image" src="https://github.com/user-attachments/assets/ec0412e3-c629-4763-b720-701862afe56e" />

```c
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

<img width="663" height="304" alt="image" src="https://github.com/user-attachments/assets/7639b03b-a2bd-48ce-95f2-78a3d1ede739" />

```c
Q1=ir.sepal_width.quantile(0.25)
Q3=ir.sepal_width.quantile(0.75)
(IQR)=Q3-Q1
print(IQR)
```

<img width="112" height="26" alt="image" src="https://github.com/user-attachments/assets/13a48141-70fd-4f6c-b878-3bc548d38697" />

```c
ran=ir[((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```

<img width="248" height="90" alt="image" src="https://github.com/user-attachments/assets/599d3390-7eb0-4edc-a9bc-2dc5c8d9c6f7" />

```c
ran=ir[~((ir.sepal_width<(Q1-1.5*IQR))|(ir.sepal_width>(Q3+1.5*IQR)))]
ran['sepal_width']
```

<img width="342" height="198" alt="image" src="https://github.com/user-attachments/assets/17a1fa86-c950-4179-b77a-7e3eea95fb47" />

```c
sns.boxplot(x='sepal_width',data=ran)
```

<img width="616" height="412" alt="image" src="https://github.com/user-attachments/assets/24710f8d-fb5e-4ebc-9c20-110d1797d9b6" />

```c
import numpy as np
import scipy.stats as stats

z=np.abs(stats.zscore(ir['petal_length']))
z
```

<img width="405" height="195" alt="image" src="https://github.com/user-attachments/assets/f948e776-7b3e-434f-825f-4adbc46958fc" />

```c
ir1=ir[z<3]
ir1
```

<img width="449" height="310" alt="image" src="https://github.com/user-attachments/assets/64461cbd-73e3-4558-957e-9ac28ea10fa1" />


# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file
