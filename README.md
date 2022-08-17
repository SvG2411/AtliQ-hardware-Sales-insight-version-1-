# AtliQ-hardware-Sales-insight-version-1-
Config files for my GitHub profile.
Data Analysis Using SQL
Show all customer records

SELECT * FROM customers;

Show total number of customers

SELECT count(*) FROM customers;

Show transactions for Chennai market (market code for chennai is Mark001

SELECT * FROM transactions where market_code='Mark001';

Show distrinct product codes that were sold in chennai

SELECT distinct product_code FROM transactions where market_code='Mark001';

Show transactions where currency is US dollars

SELECT * from transactions where currency="USD"

Show transactions in 2020 join by date table

SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

Show total revenue in year 2020,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

Show total revenue in year 2020, January Month,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

Show total revenue in year 2020 in Chennai

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

Data Analysis Using Power BI
Formula to create norm_amount column
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)

Revenue = SUM('sales transactions'[norm_sales_amount])
Profit = BaseMeasures[Revenue]-[Total cost]
Sales Qty = SUM('sales transactions'[sales_qty]) 
Profit LY = CALCULATE([Profit],SAMEPERIODLASTYEAR('sales date'[date].[Date]))
Total profit margin = SUM('sales transactions'[profit_margin])
profit Margin % = DIVIDE([Total profit margin],[Revenue])
Revenue contribution = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))
Profit Margin Contribution % = DIVIDE([Total profit margin], CALCULATE([Total profit margin],ALL('sales products'),ALL('sales customers'), ALL('sales markets')))

Insights:-
1 Revenue trend is declining since last 4 years.
2 More than 50% revenue is coming from Delhi market.
3 Highest profit margin given '7.54%' given for customer 'Leader' and profit margin contribution of customer 'Leader' is 5.06%.
4 For Electricalslance Stores our profit margin is negative (lowest) i.e. -2.09% and profit contributed by this customer also is in negative.
5 Electricalsara Stores has profit contribution of almost 37% in total profit and profit margin for same customer is 2.25%.
6 About 76% of the profit is generated from north region.



