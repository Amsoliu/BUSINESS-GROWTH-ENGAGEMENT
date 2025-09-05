# BUSINESS-GROWTH-ENGAGEMENT

## Table of Contents

- [Overview](#overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)

### Overview

This project delivers a Business Growth & Engagement Dashboard that tracks orders, revenue, subscriptions, users, and product performance. It helps stakeholders monitor month-over-month growth, understand paid vs. free subscription mix, spot high-value customers, and act on low-engagement segments. The dashboard includes slicers (City, Order Status, Product Category) and visuals for revenue by month, overall user activity, invoice status, and a detailed customer orders table.

### Key headline cards showcased:

- Total Orders: 50
- Total Quantity: 153
- Total Users: 25
- Subscriptions: 50 (Paid & Free split)
- Paid Invoices: $17,050
- Total Revenue: $37,300
- Paid Sub Revenue: $19,150 (≈51%)
- Free Sub Value/Attribution: $18,150 (≈49%)

![Image](https://github.com/user-attachments/assets/e70ca4dc-a5b7-43ee-9ef6-9b7295928add)

![Image](https://github.com/user-attachments/assets/5523e10b-cce4-4f5b-858e-f640dc033be0)

### Data Source

Primary datasets (Kaggle):

### Tools

- Excel – Initial profiling, quick checks, and ad-hoc cleaning.
- Power BI (Power Query + DAX) – Data modeling, measures, visuals, and publishing.

### Data Cleaning/Preparation

In preparing the dataset, the following steps were performed:
1. Remove Duplicates: based on natural keys
2. Data Types: cast dates to Date, amounts to Decimal, flags to Boolean, IDs to Text.
3. Standardize Categories: normalize order_status (Delivered, Processed, Cancelled) and product categories.
4. Handle Nulls: impute/flag missing city, status, and unit_price; drop rows with non-recoverable critical fields.
5. Derived Columns: Revenue = quantity * unit_price; map Paid/Free subscription classification.

### Exploratory Data Analysis

EDA focused on answering:
- Revenue Trend: How does revenue move month-to-month? Which months peak?
- Subscription Mix: What’s the ratio of Paid vs. Free subscriptions and revenue contribution?
- Order Health: What share of orders are Delivered vs. Processed vs. Cancelled?
- Customer & City Insights: Which cities and customers generate the most revenue/orders?
- Product Performance: Which categories (e.g., Laptop, Phone) drive sales and margin?
- Engagement: How does Overall User Activity evolve across months? Any seasonality?

### Data Analysis

- The analysis centered on tracking business growth and engagement metrics through key measures and visuals. Core KPIs included total orders, quantity, revenue, paid invoices, subscription revenue (paid vs. free), and month-over-month revenue growth. It also measured order cancellations and revenue trends across months.
- To visualize insights, the dashboard used cards for headline KPIs, donut/pie charts for order status and subscription mix, column and line charts for monthly revenue and user activity, and a detailed customer orders table. Interactive slicers (city, order status, product category) allowed deeper filtering and segmentation.

### Results and Findings

- Revenue: $37,300 total in the period displayed, with clear month-to-month variation and a visible mid-year peak.
- Subscriptions: 50 total, with ~51% Paid contributing $19,150 and ~49% Free contributing $18,150 (conversion opportunity).
- Orders & Fulfillment: 50 orders with a mix of Delivered/Processed/Cancelled; cancellations present measurable leakage.
- Engagement: User activity line indicates spikes around specific months—likely linked to campaigns or product launches.
- City & Customer Concentration: A few cities/customers (e.g., Rome, Madrid, London, Toronto, New York) dominate order rows—targetable for upsell/retention.
- Product Mix: Multiple categories (Accessories → Tablet) surfaced; prioritize top performers while addressing laggards.

### Recommendations

- Accelerate Paid Conversion:
  Target Free subscribers with nudges, trials, and limited-time discounts to lift the paid share above 60%.
- Reduce Cancellations:
  Add pre-cancel surveys and offer save-offers; monitor Cancelled Orders % weekly.
- Improve post-purchase communications and delivery SLAs in high-cancel cities.
- Campaign Cadence Around Peaks:
  Replicate tactics from peak months; schedule engagement campaigns 2–3 weeks beforehand.
- City-Level Playbooks:
  For top cities, run VIP programs and referral incentives; for underperforming cities, localized promos.

[🔝](#BUSINESS-GROWTH-ENGAGEMENT)
