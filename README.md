# ShopSphere Customer Churn Analytics & Predictive Modeling

An end-to-end data pipeline designed to analyze customer churn characteristics and deploy a predictive machine learning model. This project integrates relational database engineering (SQL Server) with statistical data science and machine learning (Python) to bridge the gap between technical metrics and actionable corporate strategy.

## 📌 Project Architecture
1. **Database Tier (SSMS):** Designed relational table schemas tracking 240+ customers, 2,000+ usage logs, and 180+ support interactions. Created a master view (`vw_ChurnModelPreparation`) using window functions, complex aggregations, and CTEs.
2. **Data Pipeline:** Handled cross-platform export parsing (UTF-16 encoding alignments) to ingest raw database layers directly into a Pandas DataFrame.
3. **Exploratory Data Analysis (EDA):** Rendered behavioral scatter plots and categorical distribution models using Seaborn and Matplotlib to isolate churn triggers.
4. **Machine Learning Tier:** Engineered categorical features via One-Hot Encoding and deployed a **Random Forest Classifier** to map predictive decision boundaries.

---

## 📊 Key Analytical Insights

### 1. App Engagement vs. Support Friction
* **The Onboarding Gap:** A distinct cluster of customers registered but recorded **zero minutes of usage** and zero support tickets before churning, highlighting a breakdown in initial product adoption.
* **The Friction Boundary:** Customers who opened support interactions early on and had their issues left **unresolved** stopped using the platform (`Minutes < 500`) and universally churned.
* **Retained Baseline:** Highly engaged users (`Minutes > 500`) tolerate occasional friction; even with multiple support tickets, they remain active as long as their issues are resolved.

### 2. Subscription Tier Vulnerability
* The **Basic** tier contains the highest volume of absolute churn. However, the churn-to-active ratio remains a uniform **~35% across all tiers** (Basic, Premium, Enterprise), proving that churn is driven by platform experience rather than pricing constraints.

---

## 🌲 Machine Learning Performance & Feature Weights

The **Random Forest Classifier** achieved an overall evaluation score of **100% accuracy, precision, and recall** on the test split. 

> 🔍 **Data Science Note:** Because the target variable (`Churned`) was derived programmatically based on explicit operational thresholds in the data simulation phase, the algorithm uncovered the deterministic rules perfectly, acting as an exceptional proof-of-concept pipeline.

### 🎯 Feature Importance Hierarchy
* **Primary Drivers (65%+ Weight):** `TotalRevenue` and `TotalMinutesUsed`. Financial investment and session time are the definitive signs of customer health.
* **Secondary Signals:** `UsageFrequency` and `HasUnresolvedTicket`.
* **Zero Impact:** Demographic profiles (`Country`, `TrafficSource`, `AccountTier`) have near-zero impact, confirming that user behavior and support bottlenecks dictate customer lifespan.

---

## 🚀 Actionable Corporate Strategy

1. **Automated SLA Alerts:** Set up automated triggers to route high-revenue accounts to Customer Success teams immediately if an active support ticket stays open for over 48 hours while usage minutes decline.
2. **Interactive Onboarding:** Deploy targeted walkthroughs within 48 hours of user creation to capture the zero-minute dropout segment.
3. **Usage Frequency Nudges:** Build behavioral re-engagement email loops for users whose weekly login frequencies drop below a critical baseline.

---

## 🛠️ Tech Stack & Libraries Used
* **Database Management:** SQL Server Management Studio (SSMS)
* **Environment:** VS Code, Jupyter Notebooks
* **Language:** Python 3
* **Core Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `joblib`.
