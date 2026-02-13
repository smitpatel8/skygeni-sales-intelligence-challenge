# 🚀 SkyGeni Sales Intelligence Challenge

### 📄 [**View Final Solution PDF**](./SkyGeni_Sales_Intelligence_Challenge_Solution.pdf) 
*(Contains the comprehensive business report, answers to all case questions, and strategic recommendations)*

---

## 📌 Executive Summary
**The Problem:** SkyGeni’s CRO complains, "“Our win rate has dropped over the last two quarters, but pipeline volume looks healthy. I don’t know what exactly is going wrong or what my team should focus on.”


**The Solution:** I identified and framed the core business problem faced here. Carried out detailed Exploratory Data Analysis (EDA) to get a clear picture. And later, I developed a **Deal Risk Scoring Engine** (Random Forest Classifier) that predicts the probability of failure for every open deal. This shifts the sales strategy from reactive to proactive, allowing leadership to intervene on high-value, high-risk "Zombie Deals" before they are lost.

---

## 📂 Repository Contents

| File | Description |
| :--- | :--- |
| 📓 **[EDA_SkyGeni_Challenge.ipynb](./EDA_SkyGeni_Challenge.ipynb)** | **Part 2:** Exploratory Data Analysis. Visualizing the "Q1 Hangover" and Regional performance gaps. |
| 🤖 **[SkyGeni_Deal_Risk_Scoring_Model.ipynb](./SkyGeni_Deal_Risk_Scoring_Model.ipynb)** | **Part 3:** The Machine Learning pipeline. Pre-processing, Training (Random Forest), and Risk Scoring logic. |
| 📄 **[Solution PDF](./SkyGeni_Sales_Intelligence_Challenge_Solution.pdf)** | **Full Report:** The business narrative, system design, and final recommendations. |
| 📊 **[skygeni_sales_data.csv](./skygeni_sales_data.csv)** | **Dataset:** The raw anonymized CRM data used for this analysis. |

---

## 🔍 Project Walkthrough & Approach

### Part 1: Problem Framing (The Pivot)
Initially, I hypothesized the core issue was a "Quantity vs. Quality" disconnect (Marketing sending bad leads). However, initial data exploration revealed a **"Last Mile" problem**: deals were progressing deep into the funnel (Negotiation stage) before stalling. This pivoted the focus from Lead Gen to **Sales Execution & Closing**.

### Part 2: Key Insights (EDA)
Using Python (Pandas/Seaborn), I uncovered three critical patterns:
1.  **The "Q1 Hangover" (Seasonality):** The Q1 drop was not a systemic failure but a recurring seasonal pattern visible in historical data (Fiscal Year reset effects).
2.  **The "Western Collapse":** North America and Europe saw the sharpest declines, while APAC remained stable.
3.  **Velocity Trap:** "Zombie Deals" (stagnant >60 days) had a <10% win rate but cluttered 40% of the pipeline.

### Part 3: The Decision Engine (Machine Learning)
To address the "Zombie Deal" problem, I built a **Deal Risk Scoring Engine**.
* **Model Choice:** **Random Forest Classifier**. Selected for its ability to capture non-linear relationships (e.g., how "High Deal Value" is good, but "High Value + Stagnation" is fatal).
* **Strategy:** We implemented a **Time-Based Split** (Train on 2023, Test on Q1 2024) to simulate real-world conditions and prevent data leakage.
* **Output:** A probability score (0-100%) for every deal, flagging those with **>75% Risk** for immediate executive intervention.

### Part 4: Mini System Design ("The Deal Guardian")
If SkyGeni were to productize this, it would be a SaaS layer sitting on top of Salesforce.
