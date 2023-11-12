# Ex-08-Data-Visualization-
## AIM:
To Perform Data Visualization on a complex dataset and save the data to a file.

## Explanation:
Data visualization is the graphical representation of information and data. By using visual elements like charts, graphs, and maps, data visualization tools provide an accessible way to see and understand trends, outliers, and patterns in data.

## ALGORITHM:
### STEP 1
Read the given Data

### STEP 2
Clean the Data Set using Data Cleaning Process

### STEP 3
Apply Feature generation and selection techniques to all the features of the data set

### STEP 4
Apply data visualization techniques to identify the patterns of the data.

## CODE:
```
NAME : DELLI PRIYA L
REGISTER NUMBER : 212222230029

#Import required libraries

import pandas as pd

import seaborn as sns

import matplotlib.pyplot as plt

#Load the dataset

df = pd.read_csv('Superstore2.csv', encoding='unicode_escape')

#Data Cleaning: Drop unnecessary columns

df.drop(['Row ID', 'Order ID', 'Ship Date', 'Customer ID', 'Postal Code', 'Product ID'], axis=1, inplace=True)

#Feature Generation: Extract Year and Month from Order Date

df['Year'] = pd.DatetimeIndex(df['Order Date']).year

df['Month'] = pd.DatetimeIndex(df['Order Date']).month_name()

#1. Which Segment has Highest sales?

segment_sales = df.groupby('Segment')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales)

plt.title('Segment-wise Sales')

plt.show()

#2. Which City has Highest profit?

city_profit = df.groupby('City')['Profit'].sum().reset_index().sort_values(by='Profit', ascending=False)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Profit', data=city_profit.head(10))

plt.title('Top 10 Cities by Profit')

plt.show()

#3. Which ship mode is profitable?

shipmode_profit = df.groupby('Ship Mode')['Profit'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Ship Mode', y='Profit', data=shipmode_profit)

plt.title('Ship Mode-wise Profit')

plt.show()

#4. Sales of the product based on region

region_sales = df.groupby('Region')['Sales'].sum().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Region', y='Sales', data=region_sales)

plt.title('Region-wise Sales')

plt.show()

#5. Find the relation between sales and profit

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', data=df)

plt.title('Sales vs. Profit')

plt.show()

#6. Find the relation between sales and profit based on the following category.

#i) Segment

segment_sales_profit = df.groupby('Segment')['Sales', 'Profit'].mean().reset_index()

plt.figure(figsize=(8,5))

sns.barplot(x='Segment', y='Sales', data=segment_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='Segment', y='Profit', data=segment_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Segment-wise Sales and Profit')

plt.legend()

plt.show()

#ii) City

city_sales_profit = df.groupby('City')['Sales', 'Profit'].mean().reset_index().sort_values(by='Profit', ascending=False).head(10)

plt.figure(figsize=(12,8))

sns.barplot(x='City', y='Sales', data=city_sales_profit, color='blue', alpha=0.5, label='Sales')

sns.barplot(x='City', y='Profit', data=city_sales_profit, color='green', alpha=0.5, label='Profit')

plt.title('Top 10 Cities by Sales and Profit')

plt.legend()

plt.show()

#iii) States

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='State', data=df)

plt.title('Sales vs. Profit based on State')

plt.show()

#iv) Segment and Ship Mode

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', data=df)

plt.title('Sales vs. Profit based on Segment and Ship Mode')

plt.show()

#v) Segment, Ship mode and Region

plt.figure(figsize=(8,5))

sns.scatterplot(x='Sales', y='Profit', hue='Segment', style='Ship Mode', size='Region', data=df)

plt.title('Sales vs. Profit based on Segment, Ship Mode and Region')

plt.show()
```

## OUTPUT:

![241857438-3fd50ba0-7640-4f6e-82e5-60d0f67b4a7f](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/d38b8653-30bd-428c-a53e-963258f03999)
![241857485-d9adc176-4ecd-4077-970b-dcc1ed70f0fa](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/9d29075b-8b80-4a11-8555-94be9f80c3bf)
![241857526-423b351b-dca9-4cfd-bbe9-27dfaab2842e](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/3ab6e39b-35c0-4f08-8b48-506ee4351054)
![241857539-fb88de13-8ebf-447f-a0dd-b990f682dd54](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/94c9820e-7782-4f57-967c-9f1709131361)
![241857569-f026c081-3979-4e6d-98dd-8639e916221e](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/f6d1386c-c96d-4538-a5f1-3f5a2beaabb0)
![241857598-465e9f62-422c-4e46-ba6a-f2a31417d7be](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/d801e969-ef3d-418f-bcc4-84afab4360a2)
![241857624-216dea09-4170-4272-a0b3-ec307798788d](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/40ccd31b-b335-402c-835e-b5a7d4842c3c)
![241857639-32c9646f-1b00-436b-9b6d-cefce11458fb](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/5eab4d9f-227f-45ef-af0b-0e43e6dfa34b)
![241857695-62c526d4-27d9-4af4-af9f-e2afce1a6a88](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/a0141d9e-de69-4bb9-beac-6784e8bd6f35)
![241857721-ced98db3-bb81-410b-8007-ea44955eba2e](https://github.com/Priya-Loganathan/ODD2023-Datascience-Ex-08/assets/121166075/193eca95-8d0c-44ea-87ef-ffce6d5725cb)

## RESULT:
Hence the data visualization method for the given dataset applied successfully.
