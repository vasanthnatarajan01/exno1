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
# Reading the file:
            import pandas as pd
            df=pd.read_csv("SAMPLEIDS.csv")
            df    
            
# output:
<img width="1042" height="838" alt="Screenshot 2025-09-08 100048" src="https://github.com/user-attachments/assets/607f5147-c6ea-4778-a836-4122a13629a0" />     

# Head Command:
            df.head()      
            
# Output:
<img width="793" height="188" alt="image" src="https://github.com/user-attachments/assets/af159ae4-5a1f-4ea6-a122-df82e2fdea12" />      

# Tail Command:
            df.tail()     
            
# Output:
<img width="783" height="178" alt="image" src="https://github.com/user-attachments/assets/1b77b2ec-2389-4a7c-b753-20330000506e" />      

# IsNull Command:
            df.isnull()     
            
# Output:
<img width="470" height="499" alt="image" src="https://github.com/user-attachments/assets/9e1e44dd-9bed-4ce9-b86c-43b955d15e8d" />    

# Sum Command:
            df.isnull().sum()      
            
# Output:
<img width="172" height="682" alt="image" src="https://github.com/user-attachments/assets/f4be4c4a-60b5-4023-b861-19800a2fd772" />      

# Any Command:
            df.isnull().any()     
            
# Output:
<img width="213" height="712" alt="image" src="https://github.com/user-attachments/assets/485364a7-72f9-4ff9-b514-4c3317888857" />      

# Drop-Row Command:
            df.dropna(axis=0)      
            
# Output:
<img width="460" height="249" alt="image" src="https://github.com/user-attachments/assets/8fd20ac2-e764-41c3-9088-20b6a32c239e" />      

# Fill Command:
            df.fillna(2)      
            
# Output:
<img width="472" height="400" alt="image" src="https://github.com/user-attachments/assets/1d7e4641-8b7c-4caa-b04a-6d310747be38" />     

# Forward Fill Command:
            df.fillna(method='fill')     
            
# Output:
<img width="469" height="399" alt="image" src="https://github.com/user-attachments/assets/5f4418a5-2a48-4b19-8725-c9922609c43f" />     

# Backward Fill Command:
            df.fillna(method='bfill')      
            
# Output:
<img width="471" height="402" alt="image" src="https://github.com/user-attachments/assets/afc566da-368e-4d7a-827c-9f8a07459230" />     

# Read iris.csv data:
            ir = pd.read_csv("iris.csv")
            ir     
            
# Output:
<img width="466" height="356" alt="image" src="https://github.com/user-attachments/assets/50301231-9d65-4487-b4d1-8643f12c2c52" />      

# Describe Command:
            ir.describe()     
            
# Output:
<img width="463" height="275" alt="image" src="https://github.com/user-attachments/assets/b72b9498-8c29-465c-be72-563bc1b7f0aa" />     

# Box Plot Method:
            import seaborn as sns
            sns.boxplot(x='sepal_width',data=ir)     
            
# Output:
<img width="475" height="409" alt="image" src="https://github.com/user-attachments/assets/b761b830-ce7f-45c0-bc5e-e8eed36917a4" />      

# IQR Method:  
            q1=ir.sepal_width.quantile(0.25)
            q3=ir.sepal_width.quantile(0.75)
            iqr=q3-q1
            print(iqr)       
            
# Output:
<img width="161" height="59" alt="image" src="https://github.com/user-attachments/assets/355f12e2-1c72-4aad-aed6-a594682c5a65" />     

# Finding the Lower and Upper bound:
            bound=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
            bound['sepal_width']        
            
            
# Output:
<img width="207" height="242" alt="image" src="https://github.com/user-attachments/assets/f365e48d-bdd5-4a8e-b93a-1e8617ebe7b9" />       


# Removing Outliers:
            debound=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
            debound      
            
# Output:
<img width="452" height="356" alt="image" src="https://github.com/user-attachments/assets/2811e05c-f958-4b99-9e0f-cbc19e7a9101" />     

# Box Plot:
            sns.boxplot(x='sepal_width',data=debound)      
            
# Output:
<img width="473" height="391" alt="image" src="https://github.com/user-attachments/assets/63cb6b59-ccb0-4c93-8bf6-fbbff92d60e7" />     

# Z-Score Method:
            import scipy.stats as stats
            import numpy as np
            z=np.abs(stats.zscore(ir['sepal_width']))
            z        
            
# Output:
<img width="446" height="452" alt="image" src="https://github.com/user-attachments/assets/af841e11-9834-4ca3-bcc5-d3279081ea22" />     

# Removimg Outliers:
            ir1=ir[z<3]
            ir1      
            
# Output:
<img width="484" height="362" alt="image" src="https://github.com/user-attachments/assets/3296c57f-e25e-439c-86a2-2b195e5cf178" />     




# Result
    Thus, we have read the given data and performed data cleaning and saved the cleaned data to a file successfully      
