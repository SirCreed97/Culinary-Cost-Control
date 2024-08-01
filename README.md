# Culinary-Cost-Control


### Executive Summary

The objective of this project is to  analyze and provide a comprehensive understanding of customer behavior, spending patterns, and the impact of discounts and offers on order values. This was done with the aid of python libraries like pandas, seaborn, numpy and matplotlib for data manipulation and visualization.

### Table of content

- [Executive Summary](#executive-summary)
- [Table of content](#table-of-content)
- [Introduction](#introduction) 
- [Methodology](#methodology)
- [Result](#result)
- [Finding](#finding)
- [Discussion](#discussion)
- [Conclusion](#conclusion)
- [References](#references)
- [Q & A](#q-&-a)

### Introduction

This project involves  exploratory and descriptive data analysis of Culinary Cost Control, which aimed at uncovering insights into customer behavior, spending patterns, and operational efficiency. The problem focuses on understanding how different factors influence order values and identifying opportunities for optimization. The key questions address the impact of payment methods, discounts, and offers on order values, the distribution of order values, and potential improvements in operational efficiency and customer segmentation.

### methodology

The dataset used for this analysis was gotten from [https://statso.io/optimizing-cost-and-profitability-case-study/]
The data was cleaned to make it suitable for analysis. We conducted a descriptive study to get the insights , for visualization, we used python libraries seaborn and matplotlib.

### Result

```` python libriaries

- import pandas as pd
- import numpy as np
- import matplotlib.pyplot as plt
- import seaborn as sns 

df=pd.read_csv('food_orders.csv')

df.head(100)
df.tail(100)
df.info()
#convert order date and time, delivery date and time from object to time
df['Order Date and Time']=pd.to_datetime(df['Order Date and Time'])
df['Delivery Date and Time']=pd.to_datetime(df['Delivery Date and Time'])
df.dtypes
df.shape
df.describe()
df.isna().sum()
#drop all the null value in discount and offers
df=df.dropna(subset=['Discounts and Offers'])

#plotting distribution of order values using histogram
plt.figure(figsize=(10, 6))
plt.hist(df['Order Value'], bins=10, edgecolor='black')
plt.title('Distribution of Order Values')
plt.xlabel('Order Value')
plt.ylabel('Frequency')
plt.grid(True)
plt.savefig('Distribution of order values.jpeg')
plt.show()

# Plot bar chart of payment methods
plt.figure(figsize=(10, 6))
df['Payment Method'].value_counts().plot(kind='bar', color='skyblue', edgecolor='black')
plt.title('Frequency of Payment Methods')
plt.xlabel('Payment Method')
plt.ylabel('Number of Orders')
plt.xticks(rotation=45)
plt.grid(axis='y')
plt.savefig('frequency of payment method.jpeg')
plt.show()

discount_frequency=df['Discounts and Offers'].value_counts()
# Plot bar chart of discounts and offers
plt.figure(figsize=(10, 7))
plt.pie(discount_frequency, labels=discount_frequency.index, autopct='%1.1f%%', startangle=140, colors=sns.color_palette("Set3"))
plt.title('Frequency of Discounts and Offers')
plt.axis('equal')  # Equal aspect ratio ensures the pie is drawn as a circle.
plt.savefig('frequency of discounts and offers.jpeg')
plt.show()

df['Order Date and Time'] = pd.to_datetime(df['Order Date and Time'])
df['hour'] = df['Order Date and Time'].dt.hour
plt.figure(figsize=(12, 6))
sns.histplot(df['hour'], bins=24, kde=True)
plt.title('Order Timing Distribution')
plt.xlabel('Hour of the Day')
plt.ylabel('Number of Orders')
plt.savefig('order timing distribution.jpeg')
plt.show()

df['Delivery Date and Time'] = pd.to_datetime(df['Delivery Date and Time'])
df['delivery_time'] = (df['Delivery Date and Time'] - df['Order Date and Time']).dt.total_seconds() / 60
plt.figure(figsize=(12, 6))
sns.histplot(df['delivery_time'], bins=30, kde=True)
plt.title('Delivery Time Distribution')
plt.xlabel('Delivery Time (minutes)')
plt.ylabel('Number of Orders')
plt.savefig('Delivery Time Distribution')
plt.show()
````
#### Finding
1. The histogram shows the distribution of order values within the dataset,This analysis helps us understand the spread and frequency of different order values.
2. This analysis indicates that while all three payment methods are used, Cash on Delivery and Credit Cards are more prevalent compared to Digital Wallets.
3. This pie chart of  frequency of discounts and offers help the  business to gain insights into their promotional strategies and customer behavior, enabling them to make data-driven decisions to optimize marketing efforts and maximize revenue
4. This histogram chart helps us in Understanding peak order times in-order to the make  right resource allocation, such as staffing and inventory management, to meet high demand periods.
5. This chart helps in Identifying and addressing outliers can help improve overall delivery efficiency and customer satisfaction. Continuous monitoring ensures that delivery times remain within acceptable limits, enhancing the customer experience.


### Discussion

One of the key insight from these analysis is that cash on delivery is the most frequently used payment method. Also fewer order are place during the late-night or early morning hour
The insights derived from the data analysis have significant implications for culinary cost control and enhancing food delivery services. 

### Conclusion 

In conclusion, by leveraging these data-driven insights, businesses can make informed decisions to optimize menu pricing, improve promotional strategies, enhance operational efficiency, and ultimately provide a better customer experience. This approach ensures a balance between cost control and revenue enhancement, driving overall business success in the competitive food delivery market.

### References

Here are the reference for the data and tools used in the project. Python libraries such as pandas, matplotlib, and seaborn. The data was source from statso. These sources provided the foundation for our  analysis and visualization. 

### Q & A

Thanks you for your attention. I will be happy to answer any questions you may have about the analysis, findings, or any other aspect of the project.

















