Exploratory Data Analysis(EDA) on Retail Sales Data

Tools used:

Google Colab
Excel
Power BI
GitHub

PHASE 1: Understanding the Dataset:
There are 1000 rows and 9 columns
Columns names include: 

Numerical columns:
1. Transactional ID
2. Date
3. Age
4. Quantity
5. Price per unit
6. Total amount
   
Categorical columns:
8. Customer ID
9. Gender
10. Product Category

PHASE 2: Data Loading and Cleaning
Iʼve initially loaded it into Google Colab and have done the cleaning by 
removing duplicates
handling missing values
formatting the data types.

PHASE 3: Descriptive Statistics
Identified numerical columns 

Transactional ID
Date
Age
Quantity
Price per unit
Total amount

Generated summary statistics like

Mean(average sales)
Median(middle value)
Mode(most frequent value)
456.0
135
50
Standard deviation(data spread)
559.997631555123

PHASE 4: TIME SERIES ANALYSIS
Ensured date column is in proper format which is mandatory.
Extracted time features
decomposed into year, month, and day components for time-based analysis.

Monthly Sales Analysis: 
1. May month had the highest sales
2. September had the lowest
3. Thereʼs no repeating pattern.

Yearly Sales Analysis:
1. gave a conclusion that the sales were in the dropping pattern with a steep
line.

Daily Sales Analysis:
1. Saturday had the highest sales
2. Thursday had the lowest

Weekly Sales Analysis:
1. Weekends had more sales compared to the week days.

PHASE 5: 

CUSTOMER & PRODUCT ANALYSIS
Electronics generated highest revenue with dominant sales, compared to the
other two.  
Females were the top contributors on the revenue than males.
Identified high-value customers on basis of their average amount spent.
Customers were segmented based on spending behavior into high-value and
low-value groups.

PHASE 6: DATA VISUALIZATION
In colab
Imported Visualization Libraries: Matplotlib and Seaborn

CATEGORYWISE SALES 
The bar chart shows that Electronics contributed the highest sales, while 
Beauty has the lowest performance.

MONTHLY SALES TREND
The line graph highlights trends and seasonal patterns in sales over time and
concluded that May was the highest sales month.

SALES DISTRIBUTION
The histogram shows the distribution of sales values, indicating skewness and
variability. It shows the max value at the range of 0250.

CATEGORY SHARE

The pie chart shows percentage contribution of each category. 
Electronics- 34.4%
Clothing-34.1%
Beauty-31.5%

BOXPLOT
The boxplot looks for outliers and spread of sales data and concluded that
there were no outliers.

In Power BI created graphs on
Year by Total Amount
Month by Total Amount
Day by Total Amount
Product Category by Total Amount
Age by Total Amount

PHASE 7: Recommendations(Insights):
The business relies heavily on a few high-value transactions, indicating
potential dependence on premium customers.
Business performance is influenced by time-based demand pattern.
Strong relationship between sales and profit. A positive correlation
between sales and profit indicates that increasing sales generally leads to
increased profitability.
Category analysis indicates that not all product categories contribute
equally to total sales. Electronics were the highest sellers.
Revenue is concentrated among a few customers, Additionally, many
customers make fewer or smaller purchases
Analysis of purchase frequency shows that some customers make
repeated purchases, while others are one-time buyers.
