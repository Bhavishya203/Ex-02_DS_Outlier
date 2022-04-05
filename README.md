# Ex-02_DS_Outlier

# AIM
To detect and remove the outliers in the given data set and save the final data.

# EXPLANATION
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM
# Step 1
Import the required packages(pandas,numpy,scipy)
# Step 2
Read the given csv file
# Step 3
Convert the file into a dataframe and get information of the data.
# Step 4
Remove the non numerical data columns using drop() method.
# Step 5
Detect the outliers in the data set using z scores method.
# Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
# Step 7
Check if the outliersare removed from data set using graphical methods.
# Step 8
Save the final data set into the file.

# PROGRAM
```
Developed by: Bhavishya Reddy
Register number:212221230061

import pandas as pd
df=pd.read_csv('weight.csv')
df

#removing non numerical columns
df=df.drop("Gender",axis=1)
print('After removing Non numeric columns:')
df

#graph to display outliers
df.boxplot()

#calculating z scores to detect outliers
import numpy as np
from scipy import stats
z=np.abs(stats.zscore(df))
print(z)

#removing outliers from weight
df1=df.copy()
df1=df1[(z<3).all(axis=1)]
df1

#checking if outliers are removed through graph
df1.boxplot()

#removing outliers from height
df2=df.copy()
q1=df2.quantile(0.25)
q3=df2.quantile(0.75)
IQR=q3-q1
df_new=df2[((df2>=q1-1.5*IQR)&(df2<=q3+1.5*IQR)).all(axis=1)]
df_new

#checking if outliers are removed through graph
df_new.boxplot()

#final dataset
df_new

#saving data file
df.to_csv('weight.csv', index=False)
```

# OUTPUT

# Initial data set:
![image](https://user-images.githubusercontent.com/94679395/161672518-a8eacae8-c5cb-464e-ada8-9f96bb5a505a.png)
# Data set after removing non numerical sets:
![image](https://user-images.githubusercontent.com/94679395/161672552-56e54501-15a2-44a9-81a2-862ec2492d3a.png)
# Graph displaying initial dataset with outliers:
![image](https://user-images.githubusercontent.com/94679395/161672578-4bf9b76c-dd84-428d-bca1-d778eca9fbd5.png)
# Z scores to detect outliers:
![image](https://user-images.githubusercontent.com/94679395/161672609-3dc99c58-1066-47b7-97e6-25d396581895.png)
# Data set after removing outliers in weight using z scores and list manipulation:
![image](https://user-images.githubusercontent.com/94679395/161672658-dba12d3b-c77f-44f3-a6c5-3465cd1114f9.png)
# Graph after removing outliers in weight:
![image](https://user-images.githubusercontent.com/94679395/161672688-d113b8ba-8f13-49ae-8520-e01926eac12e.png)
# Data set after removing outliers in height using Interquartile Range(IQR):
![image](https://user-images.githubusercontent.com/94679395/161672731-ea7dbed2-530a-43bd-a3ab-372fe931925a.png)
# Final graph after removing all outliers:
![image](https://user-images.githubusercontent.com/94679395/161672778-da9eba45-a31d-4e96-91b6-c931d2b12e61.png)
# Final data set:
![image](https://user-images.githubusercontent.com/94679395/161672826-d077aa86-f0df-43f5-834d-448befacb8d1.png)

# RESULT
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.


