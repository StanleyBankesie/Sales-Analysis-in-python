# Sales-Analysis-in-python

## By Stanley Bankesie

## Overview
This repository contained code and resources for conducting sales analysis. The analysis aimed to extract insights from sales data to aid decision-making processes within a business.

### Objectives of this Analysis
Objectives of this analysis wasto establish the following metrics.
* What is the the overall sales trend?
* What are the top 10 products by sales?
* What are the most selling products?
* Which is the most prefered shipping mode?
* Which are the most prefered category and sub-category?

## Data
The dataset used for this analysis was sourced from the sales department of superstore a fitictious shop. The dataset included information such as date, product information and customer informations and demographics.


### Importing Libraries
python libraries was ipmportedto aid in analysis. below is the libaries import into jupyter notebook
``` bash 
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
plt.style.use('ggplot')
import seaborn as sns
```
### Importing Dataset
dataset was imported into the notebook with the following command. output and details can be fount in the attached notebook
```bash
sales=pd.read_excel('superstore_sales.xlsx')
```
### Data Auditing
The dataset was reviewed and evaluated to check its accuracy and completeness and reliability to clear doubts about any descripancies, errors and inconsistencies. below are the checks made to append data quality of the dataset. details can be found in the notebook file. 

 Checking the first 10 rows
```bash
sales.head(10)
```

 Checking the the number of rows and columns in the Dataset
```bash

sales.shape
```
 Coinfirming the datatypes of each columns
```bash
sales.dtypes
```
 Checking the columns in the dataset
```bash
sales.columns
```

### Exploratory Data Analysis
- <H4> What is the the overall sales trend?

 The first date a product was ordered
```bash 
sales['order_date'].min()
```
 The last date a product was ordered
```bash
sales['order_date'].max()
```
 Extracting month and year from the dataset
```bash
sales['month_year']=sales['order_date'].apply(lambda x: x.strftime('%Y-%m'))
```
 Grouping by month_year and sales
```bash  
trend_sales=sales.groupby('month_year').sum()['sales'].reset_index()
```
* Details and output can be found the notebook attached

- <h4> What are the top 10 products by sales?
  


Retrieving the product name from the dataset
```bash
sales['product_name']
```
Grouping by product name and sales
```bash
product_sales=pd.DataFrame(sales.groupby('product_name').sum()['sales'])
```
Sorting products by sales in descending order
```bash
product_sales=product_sales.sort_values('sales',ascending=False)
```
Top 10 Products by Sales
```bash
product_sales[:10]
```

- <h4> What are the most selling products?

Grouping by product name to their quantity
```bash
most_sold_product=pd.DataFrame(sales.groupby('product_name').sum()['quantity'])
```
Sorting out most sold product 
```bash
most_sold_product=most_sold_product.sort_values('quantity',ascending=False)
```
Retrieving top 10 most sold product
```bash
most_sold_product[:10]
```
find details in the the notebook attached

- <h4> Which is the most prefered shipping mode?

Detailed graph can be found in the the notebook attached


- <h4> Which are the most prefered category and sub-category?

Grouping by catagory and sub category  by profit
```bash
profitable_category=pd.DataFrame(sales.groupby(['category','sub_category']).sum() ['profit'])
```
Sorting by category and profit in descending order
```bash
profitable_category.sort_values(['category','profit'],ascending=False)
```
find details in the the notebook attached

### Results
* Results provided the: 
* Top 10 products by sales
* Top 10 products by quantity
* Most preferred product category
