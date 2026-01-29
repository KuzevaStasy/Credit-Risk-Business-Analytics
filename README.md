# Credit Risk Management Framework

## 📌 Project Overview

This project demonstrates a business-oriented approach to credit risk analytics, portfolio monitoring, and management reporting.

The objective is to simulate how a Business Analytics & Credit Risk function can support management decisions in a non-banking financial institution through data-driven insights.

The project focuses on:
- Portfolio analytics
- Risk segmentation
- Early Warning Indicators (EWI)
- Management reporting logic
- Decision-support frameworks

This is **not a machine learning project**, but a business analytics and risk management exercise.

---

## 📊 Dataset

The analysis uses a feature-engineered version of the **Home Credit Default Risk dataset**.

Due to size and licensing considerations, the dataset is not included in this repository.

Dataset source:
Kaggle – Home Credit Default Risk

The available data represents a consolidated feature matrix where each row corresponds to a loan application enriched with customer and credit-related features.

---

## ⚠️ Important Analytical Note

The `TARGET` variable in the feature-engineered dataset acts as a **proxy risk indicator** rather than a raw binary default flag.

Therefore:
- Results reflect **relative risk differences across segments**
- Metrics are interpreted as **risk indicators**, not actual default probabilities

The goal is to demonstrate analytical thinking and portfolio risk logic.

---

## 🧠 Analytical Approach

The project is structured as a management-oriented analytical workflow:

### 1️⃣ Business Context & Data Understanding
- Portfolio view of the dataset
- Baseline KPIs
- Data quality considerations

### 2️⃣ Portfolio KPIs & Segmentation
- Exposure segmentation
- Income segmentation
- Demographic segmentation
- Risk distribution analysis

### 3️⃣ Early Warning Indicators (EWI)
- Exposure-based risk signals
- Affordability signals
- Demographic shifts
- External risk indicator drift

### 4️⃣ Management Insights & Reporting Framework
- Executive KPIs
- Portfolio steering logic
- Risk monitoring concepts
- Decision frameworks

---

## 🏦 Business Relevance

The analysis reflects real-world tasks of a Business Analytics / Credit Risk function:

- Translating data into management insights  
- Monitoring portfolio risk dynamics  
- Supporting risk-aware growth  
- Enabling proactive decision-making  

---

## 🛠️ Tools Used

- Python  
- Pandas  
- NumPy  
- Matplotlib  
- Seaborn  
- Jupyter Notebook  

---

## ▶️ How to Run

1. Download the dataset from Kaggle  
2. Place the feature matrix file in a `/data` or `/archive` folder  
3. Update file paths if needed  
4. Run notebooks sequentially  

---

## 👤 Author

Prepared as a demonstration project for a Business Analytics & Credit Risk leadership role.

---

## 📌 Disclaimer

This project is for demonstration purposes only and does not represent production risk models or real portfolio decisions.
