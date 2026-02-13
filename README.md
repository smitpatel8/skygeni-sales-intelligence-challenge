# 🚀 SkyGeni Sales Intelligence Challenge

### 📄 [**View Final Solution PDF**](./SkyGeni_Sales_Intelligence_Challenge_Solution.pdf) 
*(Contains the comprehensive business report, answers to all case questions, and strategic recommendations)*

---

## 📌 Executive Summary
**The Problem:** SkyGeni’s CRO complains, “Our win rate has dropped over the last two quarters, but pipeline volume looks healthy. I don’t know what exactly is going wrong or what my team should focus on.”


**The Solution:** I identified and framed the core business problem faced here. Carried out detailed Exploratory Data Analysis (EDA) to get a clear picture. And later, I developed a **Deal Risk Scoring Engine** (Random Forest Classifier) that predicts the probability of failure for every open deal. This shifts the sales strategy from reactive to proactive, allowing leadership to intervene on high-value, high-risk "Zombie Deals" before they are lost.

---

## 📂 Repository Contents

| File | Description |
| :--- | :--- |
| 📓 **[EDA_SkyGeni_Challenge.ipynb](./EDA_SkyGeni_Challenge.ipynb)** | **Part 2:** Exploratory Data Analysis. Visualizing the win rate trends and regional performance gaps. |
| 🤖 **[SkyGeni_Deal_Risk_Scoring_Model.ipynb](./SkyGeni_Deal_Risk_Scoring_Model.ipynb)** | **Part 3:** The Machine Learning model. Pre-processing, Training (Random Forest), and Risk Scoring logic. |
| 📄 **[Final Solution PDF](./SkyGeni_Sales_Intelligence_Challenge_Solution.pdf)** | **Full Report:** The business problem, narrative, model, system design, and final recommendations. |
| 📊 **[skygeni_sales_data.csv](./skygeni_sales_data.csv)** | **Dataset:** The data used for this analysis. |

---

## 🔍 Project Walkthrough & Approach

### Part 1: Problem Framing (The Pivot)
Initially, I hypothesized the core issue was a "Quantity vs. Quality" disconnect (Marketing sending bad leads). However, initial data exploration revealed a **"Deal Closing" problem**: deals were progressing deep into the funnel before stalling. This pivoted the focus from Lead Generation to **Sales Execution & Closing**.

### Part 2: Key Insights (EDA)
Using Python (Pandas/Seaborn/Matplotlib), I uncovered three critical patterns:
1.  **The "Seasonality" Factor:** The Q1 drop in the year 2024 was not a systemic failure but a recurring seasonal pattern visible in historical data (Fiscal Year reset effects).
2.  **The "Western Collapse":** North America and Europe saw the sharpest declines, while APAC and India remained stable.
3.  **Velocity Trap:** "Zombie Deals" (stagnant >60 days) had a <10% win rate but cluttered 40% of the pipeline.

### Part 3: The Decision Engine (ML model)
To address the "Zombie Deal" problem, I built a **Deal Risk Scoring Engine**.
* **Model Choice:** **Random Forest Classifier**. Selected for its ability to capture non-linear relationships (e.g., how "High Deal Value" is good, but "High Value + Stagnation" is fatal).
* **Strategy:** Implemented a **Time-Based Split** (Train on 2023, Test on Q1 2024) to simulate real-world conditions and prevent data leakage.
* **Output:** A probability score (0-100%) for every deal, flagging those with **>75% Risk** for immediate executive intervention.

### Part 4: Mini System Design
If SkyGeni were to productize this, it would be a SaaS layer sitting on top of CRM.

### 🧠 Part 5: Critical Reflection

No model is perfect. Here are the honest limitations and future improvements for this solution:

* **Weakest Assumption:** In Part 1, I initially assumed Marketing was at fault. The data proved me wrong, it was a **Closing problem**.
* **Production Risk:** Real-world CRMs are messy, the current One-Hot Encoding approach could fail. A robust production version would need a **Schema Mapping Layer**.
* **Future Improvement:** I would build a feedback button in the alert to collect outcome data.
* **Area of Least Confidence:** I selected a **75% risk score** as the cutoff for alerts. Whether this is mathematically optimal point is debatable. In a real deployment, I would first run an **A/B Test** to find the optimal cutoff.

---

## 💻 How to Run This Project

### 1. Prerequisites
Ensure you have **Python 3.8+** installed.

### 2. Installation
Clone the repository and install the required dependencies:

git clone [https://github.com/smitpatel8/skygeni-sales-intelligence-challenge.git](https://github.com/smitpatel8/skygeni-sales-intelligence-challenge.git)

### 3. Execution Order
To reproduce the results, run the Jupyter Notebooks in Google Colab or any other IDE in the following order:

1.  **`EDA_SkyGeni_Challenge.ipynb`**
    * *Action:* Generates the visualizations for Win Rates, Seasonality, and Velocity.
    * *Output:* Provides custom metrics and business insights.

2.  **`SkyGeni_Deal_Risk_Scoring_Model.ipynb`**
    * *Action:* Runs the Data Preprocessing, Feature Engineering, and trains the Random Forest Classifier.
    * *Output:* Generates the "Deal Risk Score" for all open deals.

---
