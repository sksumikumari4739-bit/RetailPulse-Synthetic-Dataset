# RetailPulse-Synthetic-Dataset
RetailPulse – Synthetic Dataset
================================

Purpose:
Demo data for an AI-powered customer analytics and demand forecasting platform.

Files:
- customers.csv: 500 customer profiles.
- products.csv: 25 products with category, price, estimated cost and reorder level.
- sales_transactions.csv: 8,000 transaction records from 2025.
- daily_demand.csv: daily product demand records for 25 products across 365 days (one store assignment per product-date row).

Join keys:
- sales_transactions.customer_id -> customers.customer_id
- sales_transactions.product_id -> products.product_id
- daily_demand.product_id -> products.product_id

Suggested uses:
- Customer analytics: RFM (recency, frequency, monetary value), customer segmentation, channel/payment analysis.
- Demand forecasting: predict units_sold by date and product_id; use lag features, day-of-week, month, promotion_active and holiday_or_festival_period.
- Inventory: compare units_sold with products.reorder_level and identify low-stock risks.
- Sales dashboards: revenue by date, category, store, channel and payment method.

Important:
All records are synthetically generated for demonstration and learning. They do not represent real customers or actual retail sales.
Currency: INR.
