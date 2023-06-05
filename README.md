# Ex-08-Data-Visualization-

## AIM
To Perform Data Visualization on the given dataset and save the data to a file. 

# Explanation
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature generation and selection techniques to all the features of the data set
### STEP 4
Apply data visualization techniques to identify the patterns of the data.


# CODE
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import seaborn as sbn
df=pd.read_csv("Superstore.csv",encoding='windows-1252')
df.head()
df.info()
df.isnull().sum()

# [1Q]
sbn.barplot(x=df['Segment'],y=df['Sales'])
plt.title("Highest Sales of the segment")

# [2Q]
sbn.barplot(x=df['City'],y=df['Profit'])
plt.title("Highest Profit of cities")

City=df.loc[:,["City","Profit"]]
df.head(5)
City=City.groupby(by=["City"]).sum().sort_values(by="Profit")
plt.figure(figsize=(10,10))
sbn.barplot(x=City.index,y="Profit",data=City)
plt.xticks(rotation = 90)
plt.xlabel=("City")
plt.ylabel=("Profit")
plt.show()

# [3Q]
sbn.barplot(x=df['Ship Mode'],y=df['Profit'])
plt.title("Profitable Ship Mode")

# [4Q]
sbn.barplot(x=df['Sales'], y=df['Region'])
plt.title("Sales of Product based on Region")

# [5Q]
sbn.lineplot(x=df['Sales'], y=df['Profit'])
plt.title("Relation between Sales and Profit")

# [6Q] 

#[i]
grouped_data = df.groupby('Segment')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
ax.legend()
plt.show()

# [ii]
grouped_data = df.groupby('City')[['Sales', 'Profit']].mean()
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('City')
ax.set_ylabel('Value')
ax.legend()
plt.show()

# [iii]
grouped_data = df.groupby('State')[['Sales', 'Profit']].mean()
fig, ax = plt.subplots()
ax.bar(grouped_data.index, grouped_data['Sales'], label='Sales')
ax.bar(grouped_data.index, grouped_data['Profit'], bottom=grouped_data['Sales'], label='Profit')
ax.set_xlabel('State')
ax.set_ylabel('Value')
ax.legend()
plt.show()

# [iv]
grouped_data = df.groupby(['Segment', 'Ship Mode'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index='Segment', columns='Ship Mode', values=['Sales', 'Profit'])
# Create a bar chart of the grouped data
fig, ax = plt.subplots()
pivot_data.plot(kind='bar', ax=ax)
ax.set_xlabel('Segment')
ax.set_ylabel('Value')
plt.legend(title='Ship Mode')
plt.show()

# [v]
grouped_data = df.groupby(['Segment', 'Ship Mode','Region'])[['Sales', 'Profit']].mean()
pivot_data = grouped_data.reset_index().pivot(index=['Segment', 'Ship Mode'], columns='Region', values=['Sales', 'Profit'])
sns.set_style("whitegrid")
sns.set_palette("Set1")
pivot_data.plot(kind='bar', stacked=True, figsize=(10, 5))
plt.legend(title='Region')
plt.show()
```
# OUPUT
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/192863c9-aadf-41ff-8717-47617b505b9e)
# Data Cleaning:
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/91fa94b1-7a32-435b-ae04-3e135f6bd3a0)
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/4fbb23ca-396c-48f8-b29e-287206f63e2f)
# [1]
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/e33439e8-be46-49e4-a105-92c940595771)
# [2]
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/d6c5b745-002b-40da-bd04-4baf378edaa1)
# [3]
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/c6acd8c4-852a-471f-86c3-b71f33908b97)
# [4]
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/6b8115b1-46fc-4856-93ca-d949fea1b975)
# [5]
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/a3deefab-75e0-45d8-957d-e4d212bf6493)
# [6]
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/4b919251-d204-41ed-af54-8141c406409f)
# ii
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/bc33eaf3-ced2-4215-b78c-1d7f09e4685b)
# iii
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/629f80f2-174c-49ab-9d81-69d68418aae4)
# iv
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/3d75ec02-f25e-419d-88b7-6f451024a119)
# v
![image](https://github.com/R-Udayakumar/Ex-08-Data-Visualization-/assets/118708024/8490a297-3523-42ad-974d-a54e626d17df)
