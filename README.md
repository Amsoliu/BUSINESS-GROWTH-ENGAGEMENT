# BUSINESS-GROWTH-ENGAGEMENT

##Table of Contents

- [Overview](#overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Data Cleaning/Preparation](#data-cleaningpreparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Data Analysis](#data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations](#recommendations)

###Overview

This project delivers a Business Growth & Engagement Dashboard that tracks orders, revenue, subscriptions, users, and product performance. It helps stakeholders monitor month-over-month growth, understand paid vs. free subscription mix, spot high-value customers, and act on low-engagement segments. The dashboard includes slicers (City, Order Status, Product Category) and visuals for revenue by month, overall user activity, invoice status, and a detailed customer orders table.

!

Key headline cards showcased:

Total Orders: 50

Total Quantity: 153

Total Users: 25

Subscriptions: 50 (Paid & Free split)

Paid Invoices: $17,050

Total Revenue: $37,300

Paid Sub Revenue: $19,150 (≈51%)

Free Sub Value/Attribution: $18,150 (≈49%)

Add your exported dashboard image to images/business-growth-dashboard.png in your repo (or update the path).

Data Source

Primary datasets (star schema recommended):

FactOrders: order_id, order_date, customer_id, product_id, city, order_status, quantity, unit_price, revenue.

FactSubscriptions: subscription_id, customer_id, start_date, plan_type (Paid/Free), status, monthly_value.

FactInvoices: invoice_id, order_id/subscription_id, invoice_date, amount, paid_flag.

DimCustomers: customer_id, name, city, segment.

DimProducts: product_id, category (Accessories, Headphones, Keyboard, Laptop, Monitor, Phone, Tablet), product_name.

Data can originate from CSV/Excel exports from CRM, billing, and ecommerce platforms.

Tools

Excel – Initial profiling, quick checks, and ad-hoc cleaning.

Power BI (Power Query + DAX) – Data modeling, measures, visuals, and publishing.

(Optional) GitHub – Version control and portfolio documentation.

Data Cleaning/Preparation

In preparing the dataset, the following steps were performed:

Remove Duplicates: based on natural keys (e.g., order_id, invoice_id, subscription_id).

Data Types: cast dates to Date, amounts to Decimal, flags to Boolean, IDs to Text.

Standardize Categories: normalize order_status (Delivered, Processed, Cancelled) and product categories.

Handle Nulls: impute/flag missing city, status, and unit_price; drop rows with non-recoverable critical fields.

Create Calendar Table: DimDate with Year, Month, Month Name (for correct chronological sorting).

Derived Columns: Revenue = quantity * unit_price; map Paid/Free subscription classification.

Modeling: star schema with relationships: FactOrders ↔ DimCustomers/DimProducts/DimDate; FactSubscriptions and FactInvoices linked via keys and dates.

Exploratory Data Analysis

EDA focused on answering:

Revenue Trend: How does revenue move month-to-month? Which months peak?

Subscription Mix: What’s the ratio of Paid vs. Free subscriptions and revenue contribution?

Order Health: What share of orders are Delivered vs. Processed vs. Cancelled?

Customer & City Insights: Which cities and customers generate the most revenue/orders?

Product Performance: Which categories (e.g., Laptop, Phone) drive sales and margin?

Engagement: How does Overall User Activity evolve across months? Any seasonality?

Data Analysis

Core measures (DAX examples you can include in your .pbix):

Total Orders = DISTINCTCOUNT(FactOrders[order_id])

Total Quantity = SUM(FactOrders[quantity])

Total Revenue = SUMX(FactOrders, FactOrders[quantity] * FactOrders[unit_price])

Paid Invoices = CALCULATE(SUM(FactInvoices[amount]), FactInvoices[paid_flag] = TRUE())

Paid Subs Revenue = CALCULATE(SUM(FactSubscriptions[monthly_value]), DimPlans[PlanType] = "Paid")

Free Subs Value = CALCULATE(SUM(FactSubscriptions[monthly_value]), DimPlans[PlanType] = "Free")

MoM Revenue % =
VAR PrevRev = CALCULATE([Total Revenue], DATEADD(DimDate[Date], -1, MONTH))
RETURN DIVIDE([Total Revenue] - PrevRev, PrevRev)

Cancelled Orders % =
DIVIDE(
    CALCULATE([Total Orders], FactOrders[order_status] = "Cancelled"),
    [Total Orders]
)

Revenue by Month = [Total Revenue]  -- visualized with DimDate[Month Sort]


Visuals used:

Cards/KPIs: Total Orders, Total Quantity, Total Users, Subscriptions, Total Revenue, Paid Invoice.

Donut/Pie: Order Status distribution; Paid vs. Free Subscriptions.

Column Chart: Revenue by Month.

Line Chart: Overall User Activity (sessions/engagement events).

Table: Customer Orders (Customer, City, Month, Day, Status, Revenue).

Slicers: City, Order Status, Product Category.

Results and Findings

Revenue: $37,300 total in the period displayed, with clear month-to-month variation and a visible mid-year peak.

Subscriptions: 50 total, with ~51% Paid contributing $19,150 and ~49% Free contributing $18,150 (conversion opportunity).

Orders & Fulfillment: 50 orders with a mix of Delivered/Processed/Cancelled; cancellations present measurable leakage.

Engagement: User activity line indicates spikes around specific months—likely linked to campaigns or product launches.

City & Customer Concentration: A few cities/customers (e.g., Rome, Madrid, London, Toronto, New York) dominate order rows—targetable for upsell/retention.

Product Mix: Multiple categories (Accessories → Tablet) surfaced; prioritize top performers while addressing laggards.

Recommendations

Accelerate Paid Conversion:

Target Free subscribers with nudges, trials, and limited-time discounts to lift the paid share above 60%.

Build usage → paywall triggers (e.g., unlock premium features after X activities).

Reduce Cancellations:

Add pre-cancel surveys and offer save-offers; monitor Cancelled Orders % weekly.

Improve post-purchase communications and delivery SLAs in high-cancel cities.

Campaign Cadence Around Peaks:

Replicate tactics from peak months; schedule engagement campaigns 2–3 weeks beforehand.

City-Level Playbooks:

For top cities, run VIP programs and referral incentives; for underperforming cities, localized promos.

Product Strategy:

Double down on categories with high margin & velocity (e.g., Laptops/Phones); bundle slower movers (Accessories) with best-sellers.

Instrumentation & Reporting:

Keep MoM Revenue %, Paid vs. Free, and Cancelled % as headline KPIs.

Add Customer Cohorts (first order month) and Retention views to track lifetime value.

How to Use This Repo

Export your Power BI dashboard image(s) and place in /images/.

Commit the .pbix (without credentials) and this README.md.

Update any measure names/paths if they differ in your model.

🔝
