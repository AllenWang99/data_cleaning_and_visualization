# Data Visualization

## Dataset Description
Kaggle Link:
https://www.kaggle.com/datasets/cameronseamons/electronic-sales-sep2023-sep2024

This dataset comprises one year of sales transaction records from an electronics company, covering the period from September 2023 to September 2024. It provides comprehensive details on customer demographics, product categories, and purchasing behaviors, offering valuable insights into the company's sales trends and customer preferences.

### Key Features

`Customer ID`: Unique identifier for each customer.</br>
`Age`: Age of the customer (numeric).</br>
`Gender`: Gender of the customer (Male or Female).</br>
`Loyalty Member`: (Yes/No) (Values change by time, so pay attention to who cancelled and who signed up).</br>
`Product Type`: Type of electronic product sold (e.g., Smartphone, Laptop, Tablet).</br>
`SKU`: A unique code for each product.</br>
`Rating`: Customer rating of the product (1–5 stars) (Should have no Null Ratings).</br>
`Order Status`: Status of the order (Completed, Cancelled).</br>
`Payment Method`: Method used for payment (e.g., Cash, Credit Card, Paypal).</br>
`Total Price`: Total price of the transaction (numeric).</br>
`Unit Price`: Price per unit of the product (numeric).</br>
`Quantity`: Number of units purchased (numeric).</br>
`Purchase Date`: Date of the purchase (format: YYYY-MM-DD).</br>
`Shipping Type`: Type of shipping chosen (e.g., Standard, Overnight, Express).</br>
`Add-ons Purchased`: List of any additional items purchased (e.g., Accessories, Extended Warranty).</br>
`Add-on Total`: Total price of add-ons purchased (numeric).</br>

## Data Understanding
This analysis focuses on cleaning and preparing the dataset for meaningful insights into customer behavior. I addressed missing values, standardized categorical data, and created indicators for specific add-ons to simplify analysis. Additionally, I evaluated outliers to ensure high-value transactions are preserved, maintaining the integrity of customer spending patterns across the dataset.</br>

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

## Visualization
### Age
> `Age Distribution of Customers`
1. The chart shows a near uniform distribution, indicating that customers are relatively evenly distributed across all age groups. There is no significant skew toward any particular age group, meaning the company's target audience spans multiple age ranges.</br>
2. The age group around 50 years old shows slightly higher frequency, indicating this demographic might be more actively engaging with the company’s products or services. The lower frequency near the 18-year-old and 80-year-old edges suggests younger and older customers may have less interest or need for the company's offerings or the company’s products or marketing efforts are not effectively reaching these demographics.</br>
3. The average customer age appears to fall within the 30–60 age range, likely corresponding to middle-aged individuals with greater purchasing power. This could suggest that the company’s core products or services appeal primarily to this demographic.</br>
4. Since the 50-year-old age group represents a peak, marketing campaigns can be tailored to meet the needs of middle-aged individuals. Strategies such as loyalty programs or discounts on high-value items might appeal to this group.</br>

### Order Status
> `Order Status Distribution`
1. The number of completed orders is significantly higher than the number of canceled orders. This indicates that most transactions are successfully processed and fulfilled, which is a positive indicator for business operations.</br>
2. While cancellations are fewer than completed orders, the bar for "Cancelled" is still substantial. This suggests that cancellations are a notable factor worth investigating to minimize revenue loss.</br>
3. A high ratio of completed orders to canceled orders reflects operational efficiency and customer satisfaction. However, understanding the reasons behind cancellations could further improve the completion rate.</br>

### Payment Method
> `Payment Method Distribution`
1. Credit cards are the most frequently used payment method, with significantly higher usage compared to other methods. This indicates customer preference for credit cards, possibly due to convenience, rewards programs, or wide acceptance. Partnering with popular credit card providers could yield mutual benefits, such as promotional discounts, cashback offers, or exclusive deals to drive more sales.</br>
2. Bank transfers, PayPal, cash, and debit cards all have similar levels of usage, showing that customers also appreciate alternative payment methods. These methods cater to diverse customer preferences, likely influenced by factors such as ease of access or regional availability. While credit cards dominate, the relatively high usage of PayPal and bank transfers suggests a trend toward digital payment solutions. Improving support for these payment methods (e.g., faster checkout for PayPal or QR codes for bank transfers) can further enhance customer satisfaction. Evaluate whether specific customer demographics or regions prefer alternative payment methods. For instance, younger customers might favor digital wallets like PayPal, while older customers might still prefer bank transfers or cash.</br>
3. The lower usage of cash and debit cards could be attributed to a shift towards digital or contactless payments. The convenience of not carrying physical money or the limited use of debit cards for larger purchases.</br>

### Customer Ratings
> `Distribution of Customer Ratings`
1. The highest number of ratings is centered around 3. This indicates that many customers consider their experience as average or neutral. The dominance of average ratings (3) indicates a need to enhance the overall customer experience. Customers who rate their experience as 3 could be incentivized to engage further through loyalty programs, discounts, or personalized follow-ups to move them into higher satisfaction levels.</br>
2. Positive ratings (4 and 5) combined appear to slightly exceed the lower ratings (1 and 2). This suggests a relatively balanced customer sentiment but indicates room for improvement to increase higher ratings.</br>
3. Ratings of 1 are the least common, which is a good sign as very negative feedback is limited. However, a considerable proportion of customers rated their experience as 2, which might indicate dissatisfaction but not extreme discontent.</br>

### Total Price
> `Distribution of Total Price`
1. The distribution of Total Price is right-skewed, with the majority of transactions concentrated at lower total price ranges (closer to 0).As the total price increases, the frequency of transactions decreases significantly. Since most transactions occur at lower total prices, the company's revenue likely depends on high sales volume rather than large-ticket purchases. Strategies to increase the frequency of low-price purchases (e.g., discounts or add-on bundles) could boost revenue.</br>
2. Most transactions fall in the 0–2000 range, indicating that the majority of purchases are for lower-priced products or small quantities.</br>
3. Transactions with a high Total Price (above 8000) are rare but still present. These might represent bulk purchases or high-value items (e.g., premium smartphones or laptops). Customers making higher-value purchases may represent a smaller but more profitable segment. Focus marketing efforts on retaining these customers through loyalty programs, personalized offers, or after-sales services.</br>

> `Unit Price vs Total Price`
1. The data forms clear clusters based on Product Type, indicating distinct price ranges and purchasing behaviors for each product:</br>
    - **Smartphones** (blue): Higher unit prices (closer to 1000) and a wide range of total prices.
    - **Tablets** (orange): Moderate unit prices (~200–800) and lower total prices.
    - **Laptops** (green): Higher unit prices (~500–800) and medium total prices.
    - **Smartwatches** (green): Moderate unit prices (~400–800) and relatively low total prices.
    - **Headphones** (purple): Lower unit prices (~200–400) and lower total prices.

2. Smartphones Dominate High Prices. Smartphones exhibit the highest unit prices and total prices, suggesting they are premium products that may involve higher quantities purchased or higher per-unit costs.</br>
3. Smartphones are high-ticket items, both in unit price and total price, making them the likely key revenue drivers. Strategies to promote smartphones (e.g., trade-in offers, installment plans) could further boost sales in this category.</br>
4. Lower-cost products like headphones and tablets cater to price-sensitive customers. Bundling these products with higher-priced items (e.g., headphones with smartphones) could drive additional revenue.</br>
5. Laptops show a narrower range of total prices compared to smartphones, despite having a similar unit price range. Offering configurations (e.g., more options for RAM/storage) or discounts could increase their appeal.</br>
6. The linear relationship in many clusters suggests customers are purchasing multiple quantities. Implementing upselling strategies (e.g., discounts for bulk purchases) could capitalize on this behavior.</br>

> `Total Price by Gender`
1. The total sales for Male and Female customers are nearly identical. This indicates that the company’s products or services appeal equally to both genders, reflecting balanced targeting. Male customers have a marginally higher total sales figure. However, the difference is negligible, suggesting no significant gender-based disparity in purchasing behavior.</br>
2. The similarity in total sales suggests that the company has successfully targeted and appealed to both male and female customers equally. Continue leveraging gender-neutral marketing strategies to maintain this balance.</br>

> `Total Price by Product Type`
1. Smartphones show the widest range of total prices, with both high median values and outliers. This suggests that smartphones are a high-value product with varying purchase quantities or configurations (e.g., different models, accessories bundled together). Smartphones' high variability and median price suggest they are a significant contributor to revenue. The company can focus on promoting premium smartphone models or bundles to capitalize on their high-value potential.</br>
2. Tablets, laptops, and smartwatches have similar median total prices, but the variability (interquartile range, IQR) for laptops and smartwatches is slightly larger than that for tablets. These products fall into a mid-price range with less extreme purchases compared to smartphones. The mid-range consistency for tablets, laptops, and smartwatches suggests that these products appeal to a broad audience. Offering bundled discounts (e.g., laptop + smartwatch) could encourage higher total prices for these products.</br>
3. Headphones show the lowest total price and the smallest variability. This indicates that headphones are likely sold as standalone items, with little variation in pricing or purchase quantity. While headphones are the most affordable, their small variability indicates limited customization or bundling. The company could explore packaging headphones with smartphones or offering premium models to increase total price variability.</br>
4. The presence of outliers in smartphones and smartwatches indicates occasional high-value transactions, which may represent bulk purchases or premium models.</br>

> `Add-on Total vs. Total Price`
1. Add-on totals range from 0 to around 300, indicating customers purchase a diverse range of add-ons, both in quantity and value.</br>
2. There’s no strong correlation between the Add-on Total and the Total Price. This suggests that add-on purchases are not directly tied to the total purchase price of the main product.</br>

> `Total Price by Shipping Type`
1. The median Total Price is relatively consistent across all shipping types, suggesting that customers opt for various shipping options regardless of the value of their transactions. All shipping types exhibit a wide range of total prices, from very low-value transactions to high-value ones. The interquartile range (IQR) is similar for all shipping types, indicating comparable distribution of transaction sizes. The similar median and range across all shipping types indicate that shipping preference is not strongly correlated with Total Price. This implies that customers might prioritize convenience (e.g., faster delivery) over price when choosing shipping options.</br>
2. There are a few outliers with high Total Price for Standard, Same Day, and Expedited shipping. These might represent bulk purchases or premium products. Next coould analyze whether these transactions are tied to specific products or customer segments to replicate similar behavior.</br>
3. Premium shipping methods have slightly higher medians compared to Standard, Overnight, and Express options. This could indicate that customers opting for faster shipping tend to spend more, possibly for higher-priority or higher-value items. The slightly higher median for Same Day and Expedited shipping suggests customers using these options are willing to spend more. Consider promoting premium shipping options for high-value products or during sales events.</br>

> `Monthly Sales Trend`
1. A significant sales spike is observed in December 2023, indicating a strong seasonal effect, likely due to holiday shopping or year-end promotions. This suggests that December is a critical month for revenue generation. The December sales spike highlights the importance of holiday-focused marketing campaigns and promotions. Plan early for holiday sales by offering discounts, bundles, or limited-time offers to maximize revenue during this period.</br>
2. Following the holiday spike, sales remain consistently high between January and August 2024, showing sustained customer engagement and stable revenue. The steady sales after December suggest strong customer retention or consistent demand. Consider strategies to maintain this trend, such as loyalty programs, targeted marketing, or post-holiday promotions.</br>
3. A notable decline occurs in September 2024, potentially indicating a seasonal slowdown after the summer months. This may reflect typical post-summer or back-to-school trends, where spending decreases. Introduce back-to-school or early holiday promotions to counteract the decline and drive engagement during slower months.</br>
4. Sales in earlier months (September to November 2023) are relatively low but show a slight upward trend before the December spike. This indicates that sales momentum builds toward the end of the year. The December sales surge implies a need for inventory management and logistics optimization to meet heightened demand without stockouts.</br>

### Add-ons
> `Add-ons Total vs. Unit Price`
1. The data points form horizontal clusters, indicating that the Unit Price tends to fall into specific discrete values (e.g., 200, 400, 600, 800, 1000). This suggests that the products sold have standardized price points, possibly corresponding to specific product categories or configurations.</br>
2. There doesn’t appear to be a strong linear relationship between Add-on Total and Unit Price. Customers purchasing higher-value add-ons are not necessarily tied to higher Unit Price products.</br>
3. Add-on totals are distributed across a broad range (from 0 to ~300), suggesting that customers purchase add-ons regardless of the unit price of their main product.</br>
4. Even for lower-priced items (e.g., ~200 or 400), some customers purchase significant add-on totals, which indicates opportunities for bundling or upselling.</br>
5. For higher unit prices (~800–1000), the spread of Add-on Total is more consistent, indicating that premium products may drive higher add-on sales but not exclusively. Focus on targeted recommendations during the checkout process for these products to increase Add-on Total.</br>

> `Add-ons Purchased Proportion`
1. The proportions of the three add-on categories are relatively balanced. Add-ons Purchased Impulse Item leads slightly at 33.7%. Add-ons Purchased Accessory and Add-ons Purchased Extended Warranty each account for 33.1%. This indicates that customers are almost equally likely to purchase any of the three add-on types. Since all add-ons are evenly distributed, the company appears to have a well-balanced strategy for promoting accessories, impulse items, and extended warranties. This balance likely reflects the versatility of the product catalog and effective cross-selling strategies.</br>
2. While the difference is minor, Impulse Items have a slightly higher proportion, suggesting they may appeal more broadly or are promoted more effectively during transactions.</br>

> `Add-ons Purchased Proportion` and `and Add-ons Purchased by Product Type (Line Chart)`
1. Both the stacked bar chart and line chart show that smartphones lead in the count of add-ons purchased across all categories. The peak in the line chart reflects the same, with all three add-on types showing the highest counts for smartphones.</br>
2. The line chart highlights a parallel trend for Accessories, Impulse Items, and Extended Warranties across all product types. This consistency indicates that customer preferences for add-ons do not drastically vary by product type, with smartphones consistently outperforming.</br>
3. Both charts show that headphones have the lowest count of add-ons purchased. This suggests that headphones are likely standalone purchases, with fewer opportunities for cross-selling or bundling add-ons. Bundling headphones with other products, like smartphones or tablets, could increase add-on sales.</br>
4. Tablets and Smartwatches have similar counts of add-ons purchased, with slight differences in distribution among the three add-on types. Impulse Items slightly lead for these product types, as shown in the line chart.</br>
5. In the line chart, Impulse Items (orange line) consistently lead for most product types, followed closely by Accessories (blue line) and Extended Warranties (green line). This highlights the strong appeal of Impulse Items, likely due to their low cost and ease of adding to a purchase.</br>
6. Extended Warranties consistently trail behind Accessories and Impulse Items across all product types, as seen in both charts. This indicates lower interest in or awareness of the value of warranties among customers.</br>

> `Add-ons Purchased Trend Over Time`
1. The add-ons purchased count increases over time, particularly after the start of 2024, suggesting an upward trend in customer engagement with add-ons.</br>
2. There is noticeable fluctuation in the add-on purchase counts, which may correspond to seasonal trends or promotional events. A sharp increase in purchases occurs near the start of 2024, possibly driven by holiday promotions or New Year sales.</br>
3. The three add-on types (Accessories, Impulse Items, and Extended Warranties) show similar trends over time, with no significant divergence. Impulse Items (orange) and Accessories (blue) seem to dominate the add-on count, while Extended Warranties (green) show slightly lower but steady counts.</br>
4. After a rapid rise, the add-on purchases plateau during the mid-2024 period, suggesting a stabilization in purchasing behavior.</br>

> `Heatmap of Add-ons Purchased by Product Type`
1. Smartphones show the highest counts of add-ons purchased across all three categories: Accessories (2410), Impulse Items (2362), and Extended Warranties (2387).This highlights smartphones as the primary driver of add-on sales. Since smartphones lead in add-on sales, focus marketing efforts on bundling popular Accessories (e.g., cases, chargers) and Impulse Items with smartphone purchases.</br>
2. Tablets and Smartwatches show comparable counts across add-on types, indicating balanced customer interest in Accessories, Impulse Items, and Extended Warranties for these products.</br>
3. Headphones consistently have the lowest add-on counts across all categories (803 for Accessories, 843 for Impulse Items, and 803 for Extended Warranties). This suggests that headphones are often standalone purchases with fewer complementary add-ons.</br>
4. Impulse Items slightly edge out Accessories and Extended Warranties for most product types, particularly for Tablets and Smartwatches.</br>
5. Extended Warranties have steady counts across all product types, though they remain slightly less popular than Accessories and Impulse Items. Highlighting the long-term cost savings of warranties in marketing campaigns.</br>

### Loyalty
> `Proportion of Loyalty Members`
1. A significant portion of the customers (78.3%) are not loyalty members, while only 21.7% are part of the loyalty program. This indicates that the majority of the customer base is not engaged in the company’s loyalty program. The relatively small percentage of loyalty members suggests there is a large untapped potential to increase engagement through targeted strategies to attract more customers to the program.</br>
2. Since non-loyalty members form the majority, efforts to convert them into loyalty members could lead to increased customer retention and higher average spending. Highlight the benefits of joining the loyalty program (e.g., discounts, exclusive offers, or reward points) in marketing campaigns.</br>
3. Use personalized email campaigns or in-store promotions to encourage non-members to join the loyalty program. Focus on high-spending non-members, as they are likely to benefit most from the program and could drive more value.</br>
4. For the 21.7% who are loyalty members, ensure retention by offering tailored benefits, exclusive promotions, or early access to new products. Monitor their engagement levels and provide incentives to keep them active in the program.</br>

