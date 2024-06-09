# Sales_Dashboard_ABC-tech

## Problem Statement

This dashboard is a critical tool for ABC Technologies, providing comprehensive insights to enhance sales strategies by analyzing revenue trends and profit margins. It monitors revenue trends, identifies peak sales periods and potential downturns, and supports strategic planning for promotions and inventory management. The dashboard evaluates profit margins across products, aids in pricing adjustments, and cost management, and identifies top-performing products and key customers, highlighting areas needing more focus. By presenting geographical sales data and uncovering regional performance variations, it facilitates targeted marketing and distribution strategies. It also detects service and product improvement areas, offers actionable insights to enhance customer satisfaction, and illustrates revenue distribution across markets, helping to address market-specific challenges and boost market penetration and sales performance. Ultimately, by leveraging this dashboard, ABC Technologies can accurately identify issues, capitalize on strengths, and implement targeted improvements to drive increased sales and profitability.

Since, the decline in sales and profitability, the company must make informed decisions and devise strategies to boost sales. Targeting a wider range of customers and products can help close the gap between top performers and others. Additionally, since Delhi has the highest sales, the company should implement initiatives to increase sales in other markets as well.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file and xlsx file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : It was observed that in none of the columns errors & empty values were present.
- Step 5 : Make the first row as header where needed
- Step 6 : Change the data type of columns accordingly. For dates table, the date and cy_date column change shows error changing from text to date, so change typw with locale.
- Step 7 : Add conditional column in dates file for month_no to sort month name accordingly. 
- Step 8 : In the markets table, remove data for New York and Paris as it is unnecessary.
- Step 9 : In the transactions table, currency column has spacing issues so trim the data and remove USD currency as we are working only on INR data.
- Step 10 : In the Power Query Editor, save all these changes and then choose close and apply.
- Step 11 : In the Model view, build relationship between the tables using star schema.
- Step 12 : Mark dates table as "Date table" for better calculations.
- Step 13 : In the Data view, create a new table named as BaseMeasures(2).
- Step 13 : In the basemeasures(2) table, create following measures:
    
    a) Sales Qty = SUM('transactions'[sales_qty])
    
    b) Revenue = SUM('transactions'[sales_amount])

    c) Total Profit Margin = SUM('transactions'[profit_margin])

    d) Revenue Last Year = CALCULATE([Revenue],SAMEPERIODLASTYEAR('dates'[date]))

    e) Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('products'),ALL('customer'),ALL('markets')))

    f) Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)

    g) Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('products'),ALL('customer'),ALL('markets')))

    h) meas_market_name = SELECTEDVALUE(markets[markets_name]) & " " & SELECTEDVALUE(markets[zone]) & " " & SELECTEDVALUE(dates[year])

- Step 14 : In the Report view, 
  
  a) Create card visuals using BaseMeasures(2) table to show Revenue, Sales Qty, Total profit Margin and Profit Margin %.

  b) Create Line and column clustered chart to show Revenue, Revenue of last year and profit margin % on cy_date column axis. This chart shows the overall data of the sales trend and profit margins.

  c) Create Treemap using Revenue data based on the markets and apply filter on Top 5 markets.

  d) Create Line graph of Sales Qty over cy_date. This gives an idea of how the quantity of sale goods are going.

  e) Create stacked bar chart showing Revenue based on the customers. This chart shows top 5 customers and give insights to whom the company needs to focus on.

  f) Create another stacked bar chart showing Revenue based on the Products and filter the chart on the basis of top 5 products. This chart gives insights of most selling products.

  g) Create slicers for years, months and zone.

  h) Insert a text column on the top of the page using the meas_market_name that will dynamically show title based on the selected filter.


# Insights

A single page report was created on Power BI Desktop.

Following inferences can be drawn from the dashboard:
### Insights from Oct'21 to Jun'24

 * Total Revenue is ₹ 998M.

 * Total Sales Qauntity is 2M.

 * Total Profit Margin is of ₹ 24.6M.

 * Total Profit Margin % is 2.5%.

 * Maximum Revenue came from North zone with Delhi NCR of ₹ 526M.

 * Top Customer is Electricalsara Stores with ₹ 418M of revenue.

 * Maximum Revenue of ₹ 414M generated in the year 2022 with sales Qty of 997K having profit margin of ₹ 9.3M.

 * Most Proftable year was 2023 having total Profit Margin of ₹ 10.5M and Profit Marging of 3.1%.




