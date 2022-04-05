# Ex-02_DS_Outlier

# AIM
To detect and remove the outliers in the given data set and save the final data.

# EXPLANATION
Outlier is a data object that deviates significantly from the rest of the data objects and behaves in a different manner. They can be caused by measurement or execution errors. The analysis of outlier data is referred to as outlier analysis or outlier mining. The box plot is a useful graphical display for describing the behavior of the data in the middle as well as at the ends of the distributions. The box plot uses the median and the lower and upper quartiles (defined as the 25th and 75th percentiles). If the lower quartile is Q1 and the upper quartile is Q3, then the difference (Q3 - Q1) is called the interquartile range or IQ.

# ALGORITHM
Step 1
Import the required packages(pandas,numpy,scipy)
Step 2
Read the given csv file
Step 3
Convert the file into a dataframe and get information of the data.
Step 4
Remove the non numerical data columns using drop() method.
Step 5
Detect the outliers in the data set using z scores method.
Step 6
Remove the outliers by z scores and list manupilation or by using Interquartile Range(IQR)
Step 7
Check if the outliersare removed from data set using graphical methods.
Step 8
Save the final data set into the file.

# PROGRAM
'''
Developed by: Dhivya Shri. B
Register number:212221230009
'''

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

# OUTPUT
# Initial data set:
![image](https://user-images.githubusercontent.com/94505585/161669809-0e3cf6be-6d6c-4950-9c80-4341a726cb00.png)
# Data set after removing non numerical sets:
![image](https://user-images.githubusercontent.com/94505585/161669877-93b79edc-7e05-4e30-ab06-1dcf14cbd4c0.png)
# Graph displaying initial dataset with outliers:
![image](https://user-images.githubusercontent.com/94505585/161669926-674f10f4-f5b7-49dd-bfed-b4f2badfad67.png)
# Z scores to detect outliers:
![image](https://user-images.githubusercontent.com/94505585/161669978-7b42cfb2-7133-4dc2-8eea-c2394b86a205.png)
# Data set after removing outliers in weight using z scores and list manipulation:
![image](https://user-images.githubusercontent.com/94505585/161670051-785858ae-a6a0-435b-976d-5dc83d37db17.png)
# Graph after removing outliers in weight:
![image](https://user-images.githubusercontent.com/94505585/161670088-8fd1c6d4-abe3-486d-838a-cfa2fdcc56fa.png)
# Data set after removing outliers in height using Interquartile Range(IQR):
![image](https://user-images.githubusercontent.com/94505585/161670141-54f6e41a-9a22-4de0-a8ec-93238099964c.png)
# Final graph after removing all outliers:
![image](https://user-images.githubusercontent.com/94505585/161670198-c258d7a1-c8d5-4d58-9901-df18a6db2db3.png)
# Final data set:
![image](https://user-images.githubusercontent.com/94505585/161670245-1dbb5980-fba7-4560-b788-04e7162c632d.png)

# RESULT
Thus the outliers are detected and removed in the given file and the final data set is saved into the file.



