# Customer-Insights

# Customer Insights Summary (Feb 28 – Apr 17, 2025)
Overall Performance Highlights
Total Customers Visited: 201
Average Customers Per Day: 13.4
Conversion Ratio: 66%
Average Time Spent per Customer: 3 hours

## Project Overview
The primary objective of this project is to analyze the pricing, distribution, and trends of drugs across various stores using the provided dataset. By leveraging SQL, we aim to gain actionable insights into drug pricing patterns, store performance, and product availability, which can aid decision-making in the pharmaceutical industry.

## Table of Contents
- [Tools Used](#Tools-Used)
- [Dataset Description](#Dataset-Description)
- [Price Insights](#Price-Insights)
- [Store Performance](#Store-Performance)
- [Product trends](#Product-trends)
- [SQL Query Documentation](#SQL-Query-Documentation)
- [Proposed SQL Queries](#Proposed-SQL-Queries)
- [Visualisations](#Visualisations)
- [Data Insights Report](#Data-Insights-Report)
- [Results and Recommendations](#Results-and-Recommendations)
  
## Customer Status Distribution
SALE customers dominate the interaction, reflecting a strong conversion pipeline.
Notable statuses include:
RETURN and REVISITED TO BUY – potential for post-sale engagement improvements.
NEW and EXCHANGE – active footfall from new and returning customers.

## Dataset Description
Some of the important columns for the Data Analysis are listed below: 

- id: Unique identifier for each record (Primary Key).
- product_id: ID representing a specific drug.
- store_id: ID representing the store offering the drug.
- type: Type of listing (e.g., COUPON).
- price: Price of the drug.
- url: Link to the product's coupon or detailed page.

## Customer Visit Patterns
Peak Hours: 4 PM to 6 PM
Top Visit Days: Friday and Wednesday
Low Visit Days: Monday and Thursday – opportunity for promotional activities


## Return Reasons Analysis

"Just Browsing" accounts for 50% of returns – signals need for stronger product engagement.

"Not in Budget" and "Particular Requirement" each represent 11.76% – opportunity to refine pricing strategy and inventory alignment.

Other reasons: Low Stock, Unavailable Items, Didn’t Like – highlight inventory and merchandising improvements needed.

## Customer Count by Price Range

Maximum customer count falls in ₹2001–₹5000 range.

Sharp decline in higher price segments – suggests price sensitivity.

Recommendation: Introduce better value propositions or discounts for mid-to-high tiers.
- URL-Based Analysis

## Top 5 Sales Performers

Deepak Gupta – 37 sales

Jitendra – 30 sales

Anil Sharma – 25 sales

Sanjay Verma – 24 sales

Shubham Gupta – 21 sales

Use top performer strategies as training references for others. 

## Event-Centric Footfall

Weddings lead the reason for visit, followed by Engagement Ceremonies and Haldi Functions.

Recommendation: Tailor product offerings and promotions to these specific events.

## Strategic Recommendations

Strengthen follow-up efforts for "Revisited to Buy" and "Followup" statuses.

Optimize pricing strategy and offer EMI or bundle deals.

Upskill the sales team using methods from top performers.

Address stock-related issues to minimize return reasons.

Launch special offers on slower days like Mondays.

FROM product p join price pr
on p.id=pr.id
join drug d on d.id=p.drug_id
GROUP BY d.name
order by average_price desc
```
Which stores offer the highest number of "COUPON" type drugs?
```
SELECT s.name, COUNT(p.type) AS coupon_count
FROM store s join price p
on p.id=s.id
WHERE p.type = 'COUPON'
```
#### Product Trends
Which products have the highest average price across all stores?
```
SELECT d.name, round(AVG(p.price),2) AS average_price
FROM price p join product pr 
on pr.id=p.id
join drug d on pr.drug_id=d.id 
GROUP BY d.name
ORDER BY average_price DESC
LIMIT 5;
```
Which products have the same price across all stores?
```
SELECT d.name 
FROM product pr join price p
on p.id=pr.id
join drug d on d.id=pr.drug_id
GROUP BY d.name
HAVING MAX(p.price) = MIN(p.price);
```
## Visualizations created using Power BI for better decision-making.
![image alt](https://github.com/k333rthan/Open_Drug_Knowladge/blob/main/Screenshot%202025-01-13%20210804.png?raw=true)

The above report shows :
- #### 1. Average Drug Price by Store (Bar Chart)
  Visualize the average price of drugs across different stores.
- #### 2. Drug Price Distribution by Price Type (Pie Chart)
  Show the percentage of drugs sold under different price types (e.g., Coupon, Cash, Gold).
- #### 3. Top 10 Most Expensive Drugs (Column Chart)
  Highlight the top 10 drugs with the highest average price.
- #### 4. Price Range of Drugs by Store (Box and Whisker Plot)
  Display the minimum, maximum, and average drug prices for each store.
- #### 5. Number of stores and the Sum of Prices Card chart





![image alt](https://github.com/k333rthan/Open_Drug_Knowladge/blob/main/Screenshot%202025-01-13%20210730.png?raw=true)



The above image only focuses on the  selected pharmacy and highlights the data related to the purticular pharmacy (here, CVS Pharmacy)

## Data Insights Report

Comprehensive report summarizing pricing trends, store performance, and product distribution along with interactive dashboards and insights as shown under the Visualisation Content


## Results and Recommendations

Potential suggestions for optimizing pricing strategies and improving product availability based on the analysis :

### Result 1:
Store 1 has the highest product count (300 listings), followed by Store 4 (250 listings).
### Recommendations:
- Focus marketing efforts on Store 1 to ensure maximum product visibility.
- Encourage underperforming stores to expand their inventory to remain competitive.

### Result 2:
Product IDs 101, 205, and 309 were found to be priced 50% above the average price across multiple stores.
Store 3 consistently lists higher-priced items for these products.
### Recommendations:
- Negotiate better pricing for products from Store 3 or explore alternative suppliers.
- Investigate whether higher prices correlate with better product quality or exclusive offerings.








