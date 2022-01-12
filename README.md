#### Author: Sasha Richardson

# Market Analysis Report

## Introduction 

#### Data Source
The dataset for this project is provided by Dr. Omar Romero-Hernandez. It is licensed as
CC0: Public Domain, which states, “You can copy, modify, distribute and perform the work,
even for commercial purposes, all without asking permission”. You can also see the license
status and download this dataset with the following link: https://www.kaggle.com/jackdaoud/marketing-data.

#### Data Features
This dataset has 28 columns, 2240 rows, and 0 duplicated rows. Feature information:

- Column 1: Customer’s unique identifier
- Column 2: Customer’s birth year
- Column 3: Customer’s education level
- Column 4: Customer’s marital status
- Column 5: Customer’s yearly household income
- Column 6: Number of children in customer’s household
- Column 7: Number of teenagers in customer’s household
- Column 8: Date of customer’s enrollment with the company
- Column 9: Number of days since customer’s last purchase
- Columns 10 - 15: Amount spent on different food items in the last 2 years
- Columns 16 - 19: Number of purchases made through different means.
- Column 20: Number of visits to company’s website in the last month
- Columns 21 - 26: Customer response to marketing campaigns.(1: accepted, 0: otherwi-se)
- Column 27:if a customer complained in the last 2 years. (1: yes, 0: no)
- Column 28: Customer’s country

## Exploratory and Statistical Data Analysis

### Are there any useful variables that can be engineered with the given data?

After assessing the dataset, new features were created that may be useful for further analysis.
- yr_join: The year that person became a customer, which can be engineered from “Dt_Customer”
- mth_join: The month that person became a customer, which can be engineered from “Dt_Customer”
- num_minors: The total number of minors in their family, which can be acquired by summing up by Kidhome and Teenhome.
- amnt_spent_total: Total amount spent in the last two years, which can be acquired by summing up all the “Mnt”-related columns
- total_num_purchases: Total number of purchases in the last two years, which can be acquired by summing up all the “Num”-related columns
- accept_campaign_total: Total amount a customer accepted the offer in all the marketing campaigns, which can be acquired by summing up all the “Accepted”-related columns and the “Response” column
- average_order_volume: engineered by dividing Total_Mnt by Total_num_purchase

### Are there any patterns or anomalies in the data which can be visualized?

A heat-map was used to see the correlations between each variable. When it gets bluer, they
are more positively correlated, and when it gets redder, they are more negatively correlated.

<img src=https://user-images.githubusercontent.com/65242969/149207780-440c197f-6c19-414a-9611-371a03ce8352.png width="500" height="500" />

The following trends are observed:
- Customers with higher incomes tend to spend more and purchase more (r = 0.665).
They also tend to make a high number of purchases using a catalog (r = 0.587). Lastly,
those with higher incomes tend to spend more on meat products (r = 0.578).
- Customers that have children and teenagers at home tend to make frequent visits to the
company’s website (r = 0.418). Also, these customers tend to have a higher number of
purchases made with a discount (r = 0.440).
- Customers with a high average order volume tend to buy more wines and meat products
(r = 0.607, r = 0.504). They also tend to make a high number of purchases using a
catalog (r = 0.398).

### What Factors are Significantly Related to the Number of Store Purchases?

Random forest was used to predict store purchases and then the model’s feature importance
score was utilized to rank the factors. The results are as follow:
Mean Absolute Error: 0.688, Mean Squared Error: 1.29, Root Mean Squared Error: 1.14.
The range of NumStorePurchases is 14, and the Root Mean Squared Error is only 1.14(less
than 10% of the range), which means it is a reliable model.

<img src=https://user-images.githubusercontent.com/65242969/149208689-7c32feb5-f0f6-4f75-86ea-32d41806ed7f.png width="500" height="350" />

It can be seen that the top 5 factors are:
1. Total number of purchases in the last two years
2. Total amount spent in the last two years
3. Total number of purchases through catalog in the last two years
4. Total number of purchases through website in the last two years
5. Amount spent on wine in the last 2 years

### Comparing the Outcome of the Marketing Campaigns and Investigating the

Difference in Performance of the Most Successful Campaign and the Rest with
Respect to Location.

<img src=https://user-images.githubusercontent.com/65242969/149209065-101fb2da-cf97-4914-a907-13d4f5052d0c.png width="500" height="350" />

In the above figure, Response (the last marketing campaign) is the most successful one. It
performed nearly twice as well as the previous campaigns, except campaign 2.

Consequently, let’s look at the proportion change of each country from the previous cam-
paigns to the most successful campaign.

<img src=https://user-images.githubusercontent.com/65242969/149209265-87ca2b7d-ba08-44a4-b493-130ae22c202d.png width="500" height="350" />

Spain has relatively more customers (+4%), and India has fewer customers (-3%) attracted
to the last campaign.


### The ’Age Effect’ : How Significantly Related is a Customers Year of Birth to the Amount of Money they Spend on Different Food Items?

To statistically verify this, the data is first divided into two groups. One is the ’born before
the year 1970’ group and the 'born after 1970' group. Then, box-plots are used to visualize
these two groups to see if they are different in terms of how much money they spend on
different items. Namely: wines, fish, meat, fruits, sweet products,and gold.

<img src=https://user-images.githubusercontent.com/65242969/149209457-acd41aec-4263-44aa-9317-6f3fa7b2f6ad.png width="575" height="500" />

The t-test was conducted to test whether their means are similar. Significance is determined
if the p-value is less than 0.05.
From the t-test, it is found that the following items exhibit an ’Age Effect’:
Wines (p = 1.70e-14), Meat (p = 0.04), Fish (p = 0.03), and Gold (p = 0.0002)

## Conclusion

### Insights
- People having kids at home are less valuable customers as they spend less seeing as
they tend to have a high number of purchases made with a discount.
- The purchasing of wine products brings more costumers into stores.
- Notably, the last marketing campaign performed nearly twice as well as the previous
campaigns. Customers were most responsive in Spain, while the opposite is seen in
India.
- Older customers (born before 1970) are valuable costumers as they tend to spend more
on most of the available products.

### Data-Driven Solutions
- Build a loyalty program to make high-income and older customers loyal as long as
possible.
- Keep using the same marketing techniques in the last campaign, spending more for
the marketing budget in Spain, and less in India

