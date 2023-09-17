# SQL-DannyMa-Challenge05

## Introduction
Data Mart is Danny’s latest venture and after running international operations for his online supermarket that specializes in fresh produce. In June 2020 - large-scale supply changes were made at Data Mart. All Data Mart products now use sustainable packaging methods in every single step from the farm all the way to the customer. Danny needs help quantifying the impact of this change on the sales performance of Data Mart and its separate business areas.
The key business questions he wants answers for as follows:

- What was the quantifiable impact of the changes introduced in June 2020?
- Which platform, region, segment, and customer types were the most impacted by this change?
- What can we do about the future introduction of similar sustainability updates to the business to minimize the impact on sales?

## Data Overview

There is only a single table for this case study: data_mart.weekly_sales. The Entity Relationship Diagram is shown below with the data types.

![](DannyMa05.PNG)

- Data Mart has international operations using a multi-region strategy.
- Data Mart has both, a retail and online platform in the form of a Shopify storefront to serve their customers.
- Customer segment and customer_type data relate to personal age and demographics information shared with Data Mart.
- Transactions is the count of unique purchases made through Data Mart and sales is the actual dollar amount of purchases
- Each record in the dataset is related to a specific aggregated slice of the underlying sales data rolled up into a week_date value which represents the start of the sales week.

## Case Study Questions
The following case study questions require some data-cleaning steps before we start to unpack Danny’s key business questions in more depth.

### 1. Data Cleansing Steps
In a single query, perform the following operations and generate a new table in the data_mart schema named clean_weekly_sales:

- Convert the week_date to a DATE format
- Add a week_number as the second column for each week_date value, for example, any value from the 1st of January to the 7th of January will be 1, the 8th to 14th will be 2, etc
- Add a month_number with the calendar month for each week_date value as the 3rd column
- Add a calendar_year column as the 4th column containing either 2018, 2019 or 2020 values
- Add a new column called age_band after the original segment column using the following mapping on the number inside the segment value

![](DannyMa05b.PNG)

Add a new demographic column using the following mapping for the first letter in the segment values:

![](DannyMa05c.PNG)

- Ensure all null string values with an "unknown" string value in the original segment column as well as the new age_band and demographic columns
- Generate a new avg_transaction column as the sales value divided by transactions rounded to 2 decimal places for each record

### 2. Data Exploration
- What day of the week is used for each week_date value?
- What range of week numbers are missing from the dataset?
- How many total transactions were there for each year in the dataset?
- What is the total sales for each region for each month?
- What is the total count of transactions for each platform
- What is the percentage of sales for Retail vs Shopify for each month?
- What is the percentage of sales by demographic for each year in the dataset?
- Which age_band and demographic values contribute the most to Retail sales?
- Can we use the avg_transaction column to find the average transaction size for each year for Retail vs Shopify? If not - how would you calculate it instead?

### 3. Before & After Analysis
This technique is usually used when we inspect an important event and want to inspect the impact before and after a certain point in time.

Taking the week_date value of 2020-06-15 as the baseline week where the Data Mart sustainable packaging changes came into effect.
We would include all week_date values for 2020-06-15 as the start of the period after the change and the previous week_date values would be before
Using this analysis approach - answer the following questions:

- What are the total sales for the 4 weeks before and after 2020-06-15? What is the growth or reduction rate in actual values and percentage of sales?
- What about the entire 12 weeks before and after?
- How do the sales metrics for these 2 periods before and after compare with the previous years in 2018 and 2019?


