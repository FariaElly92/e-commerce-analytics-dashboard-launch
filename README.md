# 🛒 E-Commerce Customer Churn Analysis & Power BI Dashboard Launch

## Executive Summary
A cross-functional project integrating data analytics (SQL, Power BI) and agile product management to identify key drivers of customer churn in an e-commerce enterprise. The initiative identified €120k in at-risk revenue and delivered an interactive reporting tool for executive decision-makers.

---

## 📂 Data Source & Business Context
* **Data Origin:** E-commerce customer transaction history dataset queried via MySQL / PostgreSQL.
* **Tools Used:** SQL Workbench, Power BI, Jira, GitHub.

---

## 📊 SQL Data Extraction & Pipeline Script

-- Query: Extract Customer Order History & Segment Churn Risk Level
SELECT 
    c.customer_id,
    c.customer_segment,
    COUNT(o.order_id) AS total_orders,
    ROUND(SUM(o.total_amount), 2) AS lifetime_value_eur,
    DATEDIFF(CURRENT_DATE(), MAX(o.order_date)) AS days_since_last_order,
    CASE 
        WHEN DATEDIFF(CURRENT_DATE(), MAX(o.order_date)) > 90 THEN 'High Churn Risk'
        WHEN DATEDIFF(CURRENT_DATE(), MAX(o.order_date)) BETWEEN 30 AND 90 THEN 'Medium Churn Risk'
        ELSE 'Active'
    END AS churn_risk_status
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.customer_segment;

---

## 🗣 Stakeholder Communication Matrix

| Stakeholder Group | Core Focus / Interest | Frequency | Channel | Output Deliverable |
|---|---|---|---|---|
| Executive Board | Revenue Retention & Churn KPIs | Monthly | Steering Committee | Power BI Summary Deck |
| Marketing Department | Re-engagement Campaign Segments | Bi-Weekly | Asana Board | Exported High-Risk Customer Lists |
| Data Engineering | SQL Query Speed & Data Pipeline Health | Weekly | Agile Standup | Technical Pipeline Logs |

---

## 📝 Lessons Learned & Project Closeout Summary

* **Major Wins:** Delivered Power BI dashboard 3 days ahead of schedule; enabled automated weekly email summary reports to leadership.
* **Project Bottlenecks:** API schema changes from payment vendors required unexpected data cleaning steps during Sprint 2.
* **Future Recommendations:** Implement automated SQL unit tests in the ETL pipeline before ingestion into Power BI.

---

## 👤 Project Lead & Documentation
**Faria** — Technical Project Manager / Data Analyst  
* Certified Google Project Management Professional  
* M.Sc. Media Informatics
