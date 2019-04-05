# Travel Rewards Mastercard® Predictive Marketing - Machine Learning In Customer Analytics

## Background
The project was a case competition solution presented by the Team 3, for ATB Datathon, which aimed to bring together Canada’s leading minds in the fields of data science, artificial intelligence, machine learning, and other disciplines, to foster diverse discussions and problem solving, during March 30-31, 2019. The assigned theme was Customer Analytics with an anonymized credit-card-transaction dataset provided. 
<img src="Images/overall_framework.png" width="1000" />

## Problem Statement
The dual mandate of improving customer experience and banking revenue require tailor marketing of right product, to right customer and in right time. The "Travel Rewards Mastercard Predictive Marketing" model aims to predict travelling customer in the next month, and the ariline to use, based on previous credit card transaction behaviors. The bank can therefore make each Travel Rewards Mastercard offer tailored to the customer, airline transaction and timeframe. 
<img src="Images/travel_reward.png" width="500" />

## Data
The Transaction table include 137,794 records with date, time, account ID, amount and Merchant Category Code, from Jan 01 to Mar 31 in 2018. Other data include the mapping between account. The Account table include the Many-to-Many mapping beween customers and accounts. The Customer table include customers' demographic infomation.
### The keywords of 360+ transaction categories
<img src="Images/wordcloud.png" width="1000" />

## Pre-processing
To impute missing values, normalize and merge datasets as needed.
<img src="Images/relations.png" width="1000" />

## Feature Engineering
The idea is to  group transctions by customer, and find possible combinations of "Recency, Frequncy, Monetary", time cycles (Day of Week, Weekend or Weekdays, etc), and category groups. This is achieved by 3 levels of extraction stages. First level is to simply calculate the spending sum, mean, std, etc over Jan and Feb, plus the most recent amount and the days past. Second level is to repeat the first level once sub-grouped by categories, and once sub-grouped by time cycles. The third level is to repeat the first level, sub-grouped by time cycle AND categories. Before feature engineering, each transaction has only 6 feature, while after merging all levels together, we have 7754 features (sparse) for each customer. 
Noted that we originally have 365 merchant categories, with top 20% categories represent 90% transactions. So, we keep the categories with high occurances, while furthur group the cateogories with less than 0.2% occurence with CitiGroup's standard MCC Grouping. By doing so, we reduce the categories from 365 to 120. 
### Citigroup's MCC Grouping
<img src="Images/mcg_shot.png" width="1000" />
