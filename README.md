# Data Visualization

## Dataset Description
Kaggle Link:
https://www.kaggle.com/datasets/cameronseamons/electronic-sales-sep2023-sep2024

This dataset comprises one year of sales transaction records from an electronics company, covering the period from September 2023 to September 2024. It provides comprehensive details on customer demographics, product categories, and purchasing behaviors, offering valuable insights into the company's sales trends and customer preferences.

### Key Features

`Customer ID`: Unique identifier for each customer.
`Age`: Age of the customer (numeric).
`Gender`: Gender of the customer (Male or Female).
`Loyalty Member`: (Yes/No) (Values change by time, so pay attention to who cancelled and who signed up).
`Product Type`: Type of electronic product sold (e.g., Smartphone, Laptop, Tablet).
`SKU`: A unique code for each product.
`Rating`: Customer rating of the product (1–5 stars) (Should have no Null Ratings).
`Order Status`: Status of the order (Completed, Cancelled).
`Payment Method`: Method used for payment (e.g., Cash, Credit Card, Paypal).
`Total Price`: Total price of the transaction (numeric).
`Unit Price`: Price per unit of the product (numeric).
`Quantity`: Number of units purchased (numeric).
`Purchase Date`: Date of the purchase (format: YYYY-MM-DD).
`Shipping Type`: Type of shipping chosen (e.g., Standard, Overnight, Express).
`Add-ons Purchased`: List of any additional items purchased (e.g., Accessories, Extended Warranty).
`Add-on Total`: Total price of add-ons purchased (numeric).

## Data Understanding
### Data Cleaning for Each Column
This file is our initial data cleaning step.</br>
After load data, we have 1000 rows with 1000 student ids, we could conclude there will be no duplicate rows in our final dataset.</br>

> `Gender`
1. To handle the 0.1% of missing values in the "Gender" column, I used the column's mode (the most frequently occurring value) to fill these gaps. This approach ensures that the missing data is replaced with the most representative category, preserving the overall distribution of the data without introducing any significant bias. Given that the percentage of missing values is very small, using the mode is an efficient and simple way to maintain data consistency without significantly affecting the dataset's integrity. This method also allows us to avoid complications in analysis due to NaN values in the "Gender" column.</br>

> `Add-ons Purchased`
1. In this context, a missing value in "Add-ons Purchased" likely means that the customer didn’t purchase any additional items. By replacing NaN values with None, I make the data in the column consistent. Missing values can disrupt analyses and visualizations, especially in categorical fields where I expect each entry to represent a distinct category. Using None indicates that no add-ons were purchased, making the column more interpretable.</br>
2. Additionally, I created a "Cleaned Add-ons Purchased" column to further standardize and deduplicate the data. In this step, I split each entry by commas, removed extra spaces, and eliminated duplicate items. This ensured consistency across the dataset, making it easier to analyze the various add-ons customers chose.</br>
3. Based on the "Cleaned Add-ons Purchased" column, I then generated three binary columns: Add-ons Purchased Accessory, Add-ons Purchased Impulse Item, and Add-ons Purchased Extended Warranty. Each of these columns indicates whether a particular add-on was included in the purchase (1 for presence, 0 for absence). This transformation simplifies the analysis of customer purchasing patterns, as it allows quick filtering and aggregation based on specific add-ons.</br>
4. Finally, I removed the "Cleaned Add-ons Purchased" and "Add-ons Purchased" columns to keep the DataFrame focused on the new binary indicators, which are more straightforward for analysis and interpretation.</br>

> Outliers
1. `Age`: No outliers.</br>
2. `Total Price`: There are 200 outliers, with values clustered around the maximum observed price (11,396.8).</br>
3. `Add-on Total`: There are 147 outliers, with several values clustered near the upper range of add-on prices (around 246.7, 244.27, etc.).</br>
3. Given that the dataset consists of 20,000 rows, the presence of 200 outliers in "Total Price" and 147 outliers in "Add-on Total" represents a relatively small portion of the data (approximately 1% or less). In this context, removing or modifying such a small percentage of rows may not significantly impact the overall analysis and may even lead to loss of important information, especially if these outliers represent legitimate high-value purchases.</br>
4. Since these outliers are likely genuine data points that reflect high-end or bulk purchases, retaining them preserves the dataset's integrity and ensures that the analysis captures the full range of customer behaviors. Additionally, in a large dataset, the effect of outliers on central tendency measures (like the mean or median) is less pronounced, making it reasonable to keep these values for a comprehensive view of the dataset.</br>

