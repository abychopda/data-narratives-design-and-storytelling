# U.S. Housing Affordability Crisis Dashboard (2024–2026)

## Overview

The **U.S. Housing Affordability Crisis Dashboard** is an interactive Tableau dashboard developed to analyze housing affordability trends across all 51 U.S. states between 2024 and 2026.

The project combines housing prices, mortgage rates, unemployment data, and household income statistics to evaluate housing market conditions and affordability stress at the state level.

The dashboard was designed for:
- Urban planners
- Policymakers
- Housing analysts
- Government stakeholders

The project emphasizes that housing affordability cannot be measured through home prices alone and instead requires a multidimensional approach combining:
- Income
- Mortgage rates
- Employment conditions
- Housing costs

---

# Dashboard Features

## Key KPI Indicators

The dashboard includes five KPI summary tiles:

- Market Health Score
- Housing Affordability Score
- Home Price Growth
- Mortgage Rate Trends
- Economic Stability

---

# Interactive Dashboard Features

Users can interactively filter:
- Year (2024–2026)
- Month
- State

The dashboard supports:
- Hover tooltips
- Cross-dashboard filtering
- Parameter-driven simulations
- State-level drill-down analysis

---

# Advanced Tableau Features

## 1. Viz-in-Tooltip (Embedded Sparkline Charts)

Each state on the investment-opportunity map contains an embedded sparkline chart showing 26 months of home-value trends directly inside the tooltip.

### Purpose
Allows users to analyze state-level housing trends without leaving the main dashboard.

---

## 2. Cross-Sheet Filter & Parameter Actions

Selecting a state dynamically updates:
- KPI cards
- Scatter plot
- Trend charts
- Narrative insights
- Mortgage simulator

### Purpose
Provides real-time state-level drill-down analysis through a single interaction.

---

## 3. What-If Mortgage Rate Simulator

The dashboard includes a parameter-driven mortgage simulator allowing users to test Federal Reserve rate-cut scenarios.

The feature dynamically recalculates:
- Monthly mortgage payments
- Mortgage burden ratios
- Monthly savings
- Affordability conditions

### Example
At a 4.5% mortgage rate scenario, California homeowners save approximately \$800/month compared to current rates.

---

# Data Sources

The project integrates one core dataset and three enrichment datasets.

## Core Dataset

| Dataset | Purpose | Period |
|---|---|---|
| Zillow ZHVI Core Dataset | State median home values | Jan 2024 – Feb 2026 |

---

## Enrichment Datasets

| Dataset | Purpose | Period |
|---|---|---|
| FRED Mortgage30US | 30-year fixed mortgage rates | Jan 2024 – Apr 2026 |
| BLS LAUS | State unemployment data | Jan 2024 – Sep 2025 |
| US Census ACS | Median household income | 2023 & 2024 surveys |

---

# Data Preparation

Data cleaning and preparation were performed using Python and pandas.

## Cleaning Tasks

- Removed corrupted unemployment rows
- Forward-filled missing values
- Converted weekly mortgage data into monthly averages
- Standardized date formats
- Merged datasets using state-month keys
- Applied income vintage matching
- Created calculated affordability metrics

---

# Dataset Structure

| Metric | Value |
|---|---|
| Rows | 1,326 |
| States | 51 |
| Time Coverage | Jan 2024 – Feb 2026 |
| Granularity | State-Month |

Each row represents one state for one month.

---

# Data Dictionary

| Variable Name | Type | Description | Source |
|---|---|---|---|
| state | String | U.S. state name | Zillow |
| date | Date | Monthly observation date | Integrated Dataset |
| home_value | Float | Median state home value | Zillow |
| mortgage_rate | Float | 30-year mortgage rate | FRED |
| unemployment_rate | Float | State unemployment rate | BLS |
| median_household_income_lagged | Float | Median annual household income | ACS |
| Affordability Ratio | Calculated Float | Income ÷ Home Value | Calculated |
| Economic Stability | Calculated Float | 1 − unemployment rate | Calculated |
| Investment Score | Calculated Float | Composite affordability score | Calculated |
| Market Health Score | Calculated Float | Normalized market score | Calculated |
| Mortgage Burden Ratio | Calculated Float | Mortgage payment ÷ monthly income | Calculated |

---


## 👥 Team
| Name | Roles | Contribution | Student ID |
|---|---|---|---|
| Ankita Adiveppagouda Patil | Data Vizualization and Lead | Project Appraoch, Vizualization | 26022830 |
| Abhishek Chopda | Project Co-Manager and Github Lead | Project Management and Design and Presentation  | 25611094 |
| Ferdinando Jr Enriquez  | Project Manager | Project Management and Design and Presentation | 25935343 |
| Gem He  | Data Engineer and Powerpoint Artist | Data Cleaning and Preparation, Presentation Approach | 25992948 |
| Harshini Prasad  | Data Vizualization | Vizualization, Presentation and Documentation | 26025369 |
| Ka Yan Cheng   | Data Vizualization and Powerpoint Artist | Project Approach, Data Cleaning and Vizualization | 25979218 |
| Ranjan Khanal   | Data Engineer and Documentation | Data Cleaning, Vizualization and Documentation | 25946613 |

---