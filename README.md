🛒 Ecommerce Orders Project with Visualization
📊 Overview

This project analyzes Brazilian e-commerce order data to explore customer behavior, order timelines, and payment trends. 
Using Python, pandas, and visualization libraries (Matplotlib, Seaborn), the notebook processes raw Excel data into clear visual insights that reveal purchasing patterns and delivery performance.

🎯 Project Objectives

Load and merge multiple order-related datasets.

Perform exploratory data analysis (EDA) to understand customer and payment patterns.

Visualize payment types, values, and installment usage.

Build aggregated datasets for customer-level insights and scatter plots.

🧩 Dataset Description

The project uses three main datasets:

File	Description	Key Columns
orders.xlsx	Customer order information including timestamps and delivery status	order_id, customer_id, order_status, order_purchase_timestamp, order_delivered_customer_date, order_estimated_delivery_date
order_payment.xlsx	Payment details for each order	order_id, payment_type, payment_installments, payment_value
customers.xlsx (optional)	Customer demographic or ID reference	customer_id, customer_unique_id
🧠 Code Breakdown
1️⃣ Importing Required Libraries
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns


These libraries handle data manipulation and visualizations.

2️⃣ Loading Datasets
orders_data = pd.read_excel('Ecommerce Orders Project/orders.xlsx')
payments_data = pd.read_excel('Ecommerce Orders Project/order_payment.xlsx')


Each dataset is loaded into a pandas DataFrame for analysis.

3️⃣ Exploratory Data Analysis (EDA)

The notebook explores order statuses, delivery times, and payment patterns.
For example, the box plot below shows the range of payment values by payment type:

plt.boxplot([
    payment_values[payment_types == 'credit_card'],
    payment_values[payment_types == 'boleto'],
    payment_values[payment_types == 'voucher'],
    payment_values[payment_types == 'debit_card']
],
labels = ['Credit Card', 'Boleto', 'Voucher', 'Debit Card'])

plt.xlabel('Payment Type')
plt.ylabel('Payment Value')
plt.title('Box Plot showing Payment Value ranges by Payment Type')
plt.tight_layout()
plt.show()


📈 Insight: Credit card payments show the widest range of values, suggesting higher transaction flexibility compared to other methods.

4️⃣ Aggregating Customer-Level Payments

To summarize total payment and installment information per customer:

scatter_df = master_data.groupby('customer_unique_id').agg({
    'payment_value': 'sum',
    'payment_installments': 'sum'
})


This creates a customer-level summary dataset (scatter_df) — ideal for scatter plots showing spending vs. installment patterns.

📉 Visualization Highlights

Box Plot — Payment values by payment type

Scatter Plot — Customer total spend vs. number of installments

Histogram / KDE Plot — Distribution of payment values

Delivery Timelines — Purchase to delivery duration (optional)


📈 Example Insights

Credit cards dominate the payment method landscape.

Some customers make very high-value purchases with large installment counts.

Delivery completion is consistent with estimated timelines for most orders.

🧑‍💻 Author

Defeng Cao
Data Analyst | SQL | Python | Tableau | Power BI
