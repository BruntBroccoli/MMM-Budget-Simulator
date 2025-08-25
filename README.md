# MMM Budget Simulator

## ❔Business Problem

Marketers often struggle to allocate budgets effectively across digital channels. This project creates a tool that empowers marketers to simulate real-world scenarios for a small-to-medium e-commerce brand and understand how shifting spend across channels impacts sales.

---

## 📨Executive Summary

- Built a **Media Mix Model (MMM)** using weekly digital marketing spend and sales.
- Applied **adstock** to capture the carry-over effects of advertising.
- Fitted an **Ordinary Least Squares (OLS) regression** to estimate each channel’s contribution to sales.
- Produced **coefficients** that quantify sales lift per channel.
- Developed a **Power BI budget simulator** to test “what-if” scenarios and compare baseline vs adjusted sales predictions.

---

## 🧑🏻‍🍳Project Summary

This project delivers a budget simulator that helps marketers understand the potential lift in sales when reallocating spend across digital channels: **Display, Email, Influencer, Search, and Social**.

---

## 🗂️Repository Contents

### 1. Python Scripts

- `MMM_Simulated_Data` → generates simulated weekly spend + sales data.
- `MMM_Budget_Simulator_V4` → applies adstock, fits the OLS regression, and outputs results for Power BI.

### 2. Excel Files

- `MMM_Simulated_Data.xlsx` → simulated dataset.
- `MMM_Data_Dictionary_V2.xlsx` → data dictionary for all fields.
- `mmm_budget_sim_results.xlsx` → baseline vs scenario predicted sales.
- `mmm_sales_coefficients.xlsx` → regression coefficients.
- `mmm_sales_features_baseline.xlsx` → baseline features for Power BI.

### 3. Power BI Tool

- `MMM_Simulator_V3.pbix` → interactive dashboard for exploring budget scenarios.

---

## 🧬Replication Instructions

1. **Generate simulated data**
    - Run `MMM_Simulated_Data.py` (or use the provided file `MMM_Simulated_Data.xlsx`).
2. **Run the budget simulator script**
    - Run `MMM_Budget_Simulator_V4.py` (or use the provided outputs).
    - This generates:
        - `mmm_budget_sim_results.xlsx`
        - `mmm_sales_coefficients.xlsx`
        - `mmm_sales_features_baseline.xlsx`
3. **Open the Power BI workbook** (`MMM_Simulator_V3.pbix`)
    - Requires Power BI Desktop.
    - Inputs:
        - **Top-left slicer** → set your budget (up to $10,000 in this version).
        - **Left-side sliders** → allocate percentages of the budget to each channel.
            - Percentages will normalize to 100% automatically.
    - Outputs:
        - A summary statement of the scenario’s predicted impact.
        - A channel-level breakdown table.
        - A waterfall chart showing sales lift or decline.
        - A cluster chart comparing actual vs scenario spend per channel.

---

## 📊Using Your Own Data

1. Match your dataset to the same structure as `MMM_Simulated_Data.xlsx`.
2. Run `MMM_Budget_Simulator_V4` on your data — this will generate the same three output files (`mmm_budget_sim_results`, `mmm_sales_coefficients`, `mmm_sales_features_baseline`).
3. Plug these outputs into the Power BI simulator (`MMM_Simulator_V3.pbix`).
    - Adjust the **budget slicer max** to reflect your business’s maximum budget.

---

## 🖋️Methodology

This project builds a **Media Mix Model (MMM)** to estimate the impact of different marketing channels on weekly sales and to simulate “what-if” budget reallocations.

### 1. Data Preparation

- Weekly spend data aggregated by channel.
- Each channel’s spend was **adstocked** to capture carry-over effects.
- Non-marketing controls (e.g., price index, inventory, promotions, holidays) were included to isolate true marketing effects.

### 2. OLS Regression

We assume weekly sales can be explained as:

$$
y=β0+β1x1+β2x2+⋯+ϵ
$$

- y = actual sales
- β0 = intercept (baseline sales if spend = 0)
- βi = coefficient for channel or control variable
- xi = adstocked spend or control variable
- ϵ = residual (unexplained variation)

OLS estimates the coefficients by minimizing the squared difference between actual and predicted sales.

### 3. Predictive Equation

Once fitted, the model produces estimated coefficients:

$$
\hat{y}=β^0+β^1x1+β^2x2+…
$$

- $\hat{y}$​ = predicted sales (no residual term — purely systematic, explainable part).

### 4. Budget Simulator

- Apply multipliers to channel spends.
- Recalculate predicted sales under new scenarios.
- Compare **baseline vs scenario predictions** to measure sales lift/decline.

---

## 💡Results / Insights

This project uses simulated data. In one scenario with a **$5,000 budget**:

- **+15% Social** and **+10% Search**
- **–10% Email** and **–15% Display**

Produced an estimated **+75.2% lift in predicted sales**.

---

## 👷🏻Future Improvements

- Incorporate long-term brand-building metrics (e.g., organic social, YouTube).
- Experiment with alternative models (Ridge/Lasso regression, Bayesian MMM).
- Add confidence intervals to quantify uncertainty in predictions.

---

## 🔑 Why This Project Matters

- Demonstrates the **end-to-end workflow**: simulation → adstock → OLS regression → coefficients → Power BI dashboard.
- Bridges **data science and business decision-making**: marketers can experiment with real trade-offs in channel allocation.
- Recruiters/hiring managers can quickly see both the **technical rigor** and the **practical business application** of the project.

---

## 🤖 Use of AI in This Project

This project was **conceived, scoped, and designed entirely by me**:

- Defined the business problem.
- Designed the methodology and simulation approach.
- Built the Power BI simulator for budget allocation testing.

I also used AI as a **coding assistant and learning partner**:

- Helped accelerate Python scripting for data simulation, adstock transformations, and OLS modeling.
- Provided explanations of statistical concepts (e.g., adstock, intercepts, coefficients) to speed up my learning.
- Assisted with debugging and documentation formatting.

All **product thinking, methodology choices, and dashboard design** were my own. I designed the dish — what to bake and how to serve it — but AI was like a recipe book: offering techniques and instructions I could adapt to my own kitchen.
