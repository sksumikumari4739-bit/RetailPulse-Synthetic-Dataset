RetailPulse – AI-Powered Customer Analytics & Demand Forecasting Platform

A retail analytics project built for the Zidio Development – Data Science & Analytics programme (Team No 18, Batch Sept). It brings sales, customers, products, demand forecasts and inventory risk into one interactive Power BI dashboard.

The data is synthetic (created for learning), covers calendar year 2025, and amounts are in Indian rupees (INR).

Team
Member	Contribution
Vanshika Pal	Prophet demand forecast, accuracy tables, and the Power BI dashboard (data model, DAX measures, 12 report pages)
Gauri Wankhede	Data merging and cleaning
Shanmughapriya Vishwakarma	Lovable web page for EDA and data-quality checks
Sumitra Kumari	GitHub repository setup deployment and management

Mentor: Chandan Mishra

Links
Live page (EDA and data-quality): https://datauploadcheck.lovable.app/
Demo video: https://drive.google.com/file/d/1SyF4qjEFoTrrp-coZjCS_YJfMzrOeJJ6/view?usp=sharing
Feedback video: https://drive.google.com/file/d/1o8jRx8nTwvUgJyQxsi3H_H24KYmPyrLE/view?usp=sharing
Project report (PDF): https://drive.google.com/file/d/1KyTVsk1L4xb7hZ8bK1Eheaf7vamNBPgL/view?usp=sharing
What the project does
Sales and profit analytics: revenue, profit, margin, orders, average order value, trends by month, weekday and quarter.
Customer analytics: segments, age groups, loyalty points, payment methods and sales channels.
Demand forecasting: Prophet forecast of total daily demand, compared with a naive baseline.
At-risk customers: customers labelled "At Risk" in the dataset, with their revenue share.
Inventory risk: compares each product's reorder level with the reorder point needed for a 7-day lead time.
Key results
Metric	Value
Total revenue	₹11,123,342 (about ₹1.11 crore)
Total profit / margin	₹3,323,597 / 29.9 %
Orders / customers	8,000 / 500
Prophet MAPE (30-day test, 2–31 Dec 2025)	8.28 % (naive baseline 21.8 %)
At-risk customers	77 (15.3 % of revenue)
Products under-protected for a 7-day lead time	22 of 25
Dashboard pages (Power BI)
Executive Summary
Sales Trend Analysis
Product Performance
Customer Analytics
Region Sales
Monthly and Seasonal Sales
Customer Behavior
Profit and Revenue Analysis
Inventory Risk
Order and Transaction
Advanced Analytics (forecast and at-risk customers)
Interactive Filter
Tech stack

Python (Pandas, NumPy, Prophet) · Power BI Desktop (Power Query, DAX) · Lovable (EDA web page) · Git and GitHub

Repository structure

TODO: adjust this to the files that are really in the repository.

RetailPulse/
├── README.md
├── dashboard/        # Power BI file (.pbix) and PDF export of all pages
├── data/             # retailpulse_merged.csv, daily_demand_clean.csv, forecast outputs
├── notebooks/        # Prophet forecasting notebook
├── screenshots/      # Dashboard and EDA screenshots
└── report/           # Project report (PDF)
How to use
Dashboard: open the .pbix file in Power BI Desktop (free, Windows). A PDF export and screenshots are in the dashboard and screenshots folders for viewing without Power BI.
EDA page: open the live page, choose the "Retail sales" dataset, and upload data/retailpulse_merged.csv. The page shows the distribution of each column, missing values by column and a correlation matrix.
Forecast notebook: TODO add the steps and Python version, for example pip install pandas numpy prophet and then run the notebook in notebooks/.
Data
Dataset	Rows	Used for
Sales (merged file)	8,000	Revenue, profit, customers, payment, channel
Daily demand	9,125	Demand, promotions, holidays, forecast, inventory risk
Prophet forecast output	365	Actual, naive and Prophet daily demand

Note: the sales table records 14,012 units and the demand table records 93,551 units. They are separate sources and are not reconciled.

Model summary
Total daily demand forecast with Prophet; trained on 335 days and tested on the last 30 days of 2025.
Prophet MAPE 8.28 % and RMSE 21.9, against 21.8 % and 51.8 for a naive baseline.
TODO add the Prophet settings (seasonality, whether holiday and promotion flags were used).
Limitations and next steps
At-risk customers come from the At Risk label in the data. This version has no churn prediction model.
Experiment tracking (MLflow), drift detection (Evidently AI) and automatic retraining are not implemented yet.
The forecast is evaluated on a single 30-day window with one year of data.
Planned: churn model, RFM segmentation, drift monitoring, scheduled retraining, and a hosted dashboard with sample data.
Acknowledgements

Built as a team project for Zidio Development under the guidance of our mentor, Chandan Mishra.
