# 📊 Data Narrative Studio Project  
## U.S. Housing Affordability Crisis Dashboard (2024–2026)

---

## 📖 Overview

The **U.S. Housing Affordability Crisis Dashboard** is an interactive Tableau dashboard developed to analyze housing affordability trends across all 51 U.S. states between 2024 and 2026.

The project combines housing prices, mortgage rates, unemployment data, and household income statistics to evaluate housing market conditions and affordability stress at the state level.

Rather than treating affordability as a simple home-price issue, the dashboard adopts a multidimensional approach incorporating:

- Household income
- Mortgage interest rates
- Employment conditions
- Housing costs
- Economic stability indicators

The dashboard was designed for:

- Urban planners
- Policymakers
- Housing analysts
- Government stakeholders

---

## 🎯 Project Objective

The goal of this project is to transform complex housing and economic datasets into a persuasive, human-centered data narrative that informs stakeholders about the growing affordability crisis in the United States.

The dashboard aims to:

- Identify states experiencing severe affordability stress
- Compare market health across regions
- Demonstrate the impact of mortgage rate changes
- Support data-driven housing policy discussions

---

## 👤 Target Persona

### Primary Stakeholder
**US State Mayors & Urban Housing Policy Makers**

---

## 📖 Narrative Structure — What → So What → What Next

### WHAT

16 out of 51 U.S. states require more than 30% of monthly income to cover mortgage payments alone, meeting the federal definition of **cost-burdened housing**.

- Hawaii reaches **47.9%**
- California reaches **44.9%**

This indicates that housing affordability has deteriorated significantly across major U.S. housing markets.

---

### SO WHAT

Mortgage rates peaked at **7.06% in May 2024**, yet home prices continued to rise.

This reveals a disconnect between:

- Housing prices
- Income affordability
- Economic conditions

The correlation between unemployment and home value is only **0.07**, suggesting that economic hardship alone does not explain rising housing costs.

The dashboard highlights how affordability stress is now driven more by structural market conditions than traditional economic indicators.

---

### WHAT NEXT

Lower mortgage rates can improve affordability conditions.

For example:

- California households could save approximately **$828 per month** if mortgage rates fell to **4.5%**

However, lower rates alone are insufficient in high-cost states such as Hawaii, where home prices remain the primary affordability barrier.

The analysis suggests that:

- Housing supply expansion
- Zoning reform
- Long-term housing policy intervention

are essential to improving affordability outcomes.

---

## 📊 Dashboard Features

### Key KPI Indicators

The dashboard includes:

- Market Health Score
- House Affordability Score
- Price Growth (YoY)
- Mortgage Rate
- Economic Stability

---

## 🚀 Advanced Interactive Features

### 1. Context-Aware Filtering

Selecting a state dynamically updates:

- KPI cards
- Scatter plots
- Trend charts
- Mortgage simulations
- State rankings

This enables interactive state-level exploration and narrative-driven analysis.

---

### 2. Viz-in-Tooltip (Embedded Trend Analysis)

Interactive hover tooltips reveal additional state-level insights and trend information without requiring users to navigate away from the dashboard.

---

### 3. What-If Mortgage Rate Simulator

The dashboard includes a parameter-driven mortgage simulator allowing users to test Federal Reserve rate-cut scenarios.

The simulator dynamically recalculates:

- Monthly mortgage payments
- Mortgage burden ratios
- Estimated monthly savings
- Affordability conditions

---

## 🛠️ Tools & Technologies

- Tableau
- Python
- Pandas
- GitHub
- SharePoint / Teams

---

## 🌐 Live Dashboard


**[Live Tableau Dashboard](https://public.tableau.com/app/profile/harshini.prasad/viz/USHOUSINGAFFORDABILITYCRISISGROUP27/Overview?publish=yes)**


---

## 🎥 Video Walkthrough


**[Dashboard Video Walkthrough](https://drive.google.com/drive/folders/1B02JfMsi4uJ-q_IQ8aSgSUA1lRLq3Boe)**


---

## 📂 Project Structure

```text
data-narratives-design-and-storytelling/
│
├── data/
│   ├── raw datasets/
│   └── final processed dataset/
│
├── data cleaning/
│   └── Dataset Cleaning.ipynb
│
├── docs/
│   └── DVN AT3 Group 27 Game Plan.xlsx
│
├── misc/
│   ├── correlation_matrix.png
│   └── Export Calculated FieldsV2.ipynb
│
├── pitch slides/
│   └── DVN AT3 Group 27 - Presentation Slides.pptx
│
├── reports/
│
├── tableau/
│   └── US HOUSING AFFORDABILITY CRISIS.twbx
│
└── README.md
```

---

## 📊 Data Sources

| Dataset | Purpose | Period |
|---|---|---|
| Zillow ZHVI Core Dataset | State median home values | Jan 2024 – Feb 2026 |
| FRED Mortgage30US | 30-year fixed mortgage rates | Jan 2024 – Apr 2026 |
| BLS LAUS | State unemployment data | Jan 2024 – Sep 2025 |
| US Census ACS | Median household income | 2023 & 2024 surveys |

---

## 📘 Data Dictionary

### Core Dataset Variables

| Variable | Type | Unit | Source | Provenance |
|---|---|---|---|---|
| state | String | / | Zillow / BLS / FRED | Full U.S. state name; 51 values including DC |
| date | Date | Monthly (end of month) | Zillow ZHVI | Range: 2024-01-31 to 2026-02-28 |
| home_value | Decimal | USD ($) | Zillow ZHVI | State-level median home value, seasonally adjusted |
| unemployment_rate | Decimal | % | BLS LAUS | Civilian unemployment rate by state |
| mortgage_rate | Decimal | % | FRED MORTGAGE30US | 30-year fixed mortgage rate averaged monthly |
| income_2023 | Integer | USD ($) | US Census ACS 2023 | State median household income |
| income_2024 | Integer | USD ($) | US Census ACS 2024 | State median household income |
| median_household_income_lagged | Integer | USD ($) | Derived | Vintage-matched ACS income estimates |
| labor_force_total | Decimal | Count | BLS LAUS | Civilian labour force total by state |
| civilian_population | Decimal | Count | BLS LAUS | Civilian non-institutional population |
| employment_total | Decimal | Count | BLS LAUS | Total employed persons by state |
| unemployment_total | Decimal | Count | BLS LAUS | Total unemployed persons by state |

---

### Calculated Fields

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| Monthly Income | Decimal | USD/month | median_household_income_lagged ÷ 12 | Converts annual income into monthly income |
| Loan Amount | Decimal | USD | home_value × 0.8 | Assumes 20% down payment |
| Monthly Rate | Decimal | Fraction | mortgage_rate ÷ 100 ÷ 12 | Converts annual mortgage rate into monthly decimal |
| Monthly Mortgage Payment | Decimal | USD/month | Standard 30-year amortisation formula | Monthly mortgage repayment estimate |
| Mortgage Burden Ratio | Decimal | Ratio (0–1) | Monthly Mortgage Payment ÷ Monthly Income | Housing affordability burden metric |
| Affordability Ratio | Decimal | Ratio | median_household_income_lagged ÷ home_value | Measures income coverage relative to home prices |
| Economic Stability | Decimal | Ratio (0–1) | 1 − unemployment_rate | Proxy for labour market strength |
| Investment Score | Decimal | Score | Affordability × Mortgage × Stability composite | Composite opportunity metric |
| Home Value ($K) | Decimal | $K | home_value ÷ 1000 | Simplified chart display |
| YoY Home Value Change | Decimal | % | 12-month lag calculation | Measures annual price growth |
| What-If Monthly Payment | Decimal | USD/month | Parameter-adjusted mortgage formula | Simulated repayment under different rates |
| What-If Mortgage Burden | Decimal | Ratio | What-If Payment ÷ Monthly Income | Simulated affordability burden |
| Monthly Savings | Decimal | USD/month | Current Payment − What-If Payment | Savings from lower rates |
| Affordability Category | String | Category | IF/ELSEIF categorisation | Groups affordability conditions |
| Investment Category | String | Category | IF/ELSEIF categorisation | Groups investment opportunity levels |

---

## 👥 Team & Contributions

| Name | Roles | Contribution | Student ID |
|---|---|---|---|
| Ankita Adiveppagouda Patil | Data Vizualization and Lead | Project Appraoch, Vizualization | 26022830 |
| Abhishek Chopda | Project Co-Manager and Github Lead | Project Management and Design and Presentation  | 25611094 |
| Ferdinando Jr Enriquez  | Project Manager | Project Management and Design and Presentation | 25935343 |
| Gem He  | Data Engineer and Powerpoint Artist | Data Cleaning and Preparation, Presentation Approach | 25992948 |
| Harshini Prasad  | Data Vizualization | Vizualization and Documentation | 26025369 |
| Ka Yan Cheng   | Data Vizualization and Powerpoint Artist | Project Approach and Vizualization | 25979218 |
| Ranjan Khanal   | Data Engineer and Documentation | Data Cleaning and Documentation | 25946613 |

---


## 🙌 Credits

This project was developed as part of the **Data Narratives Design & Storytelling Studio** assessment.

Data sources and supporting organisations:

- Zillow Research
- Federal Reserve Economic Data (FRED)
- U.S. Census Bureau
- Bureau of Labor Statistics (BLS)

A special thanks to our professor **Jared Wong** for his guidance and his teachings.

---

## 📜 License

This repository is intended for academic and educational purposes only.