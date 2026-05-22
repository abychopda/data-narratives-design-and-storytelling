#  Data Narrative Studio Project  
## U.S. Housing Affordability Crisis Dashboard (2024–2026)

---

##  Overview

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

##  Project Objective

The goal of this project is to transform complex housing and economic datasets into a persuasive, human-centered data narrative that informs stakeholders about the growing affordability crisis in the United States.

The dashboard aims to:

- Identify states experiencing severe affordability stress
- Compare market health across regions
- Demonstrate the impact of mortgage rate changes
- Support data-driven housing policy discussions

---

##  Target Persona

### Primary Stakeholder
**US State Mayors & Urban Housing Policy Makers**

---

##  Narrative Structure — What → So What → What Next

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

##  Dashboard Features

### Key KPI Indicators

The dashboard includes:

- Market Health Score
- House Affordability Score
- Price Growth (YoY)
- Mortgage Rate
- Economic Stability

---

##  Advanced Interactive Features

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

##  Tools & Technologies

- Tableau
- Python
- Pandas
- GitHub
- SharePoint / Teams

---

##  Live Dashboard


**[Live Tableau Dashboard](https://public.tableau.com/app/profile/harshini.prasad/viz/USHOUSINGAFFORDABILITYCRISISGROUP27/Overview?publish=yes)**


---

##  Video Walkthrough


**[Dashboard Video Walkthrough](https://drive.google.com/drive/folders/1B02JfMsi4uJ-q_IQ8aSgSUA1lRLq3Boe)**


---

##  Project Structure

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

##  Data Sources

| Dataset | Purpose | Period |
|---|---|---|
| Zillow ZHVI Core Dataset | State median home values | Jan 2024 – Feb 2026 |
| FRED Mortgage30US | 30-year fixed mortgage rates | Jan 2024 – Apr 2026 |
| BLS LAUS | State unemployment data | Jan 2024 – Sep 2025 |
| US Census ACS | Median household income | 2023 & 2024 surveys |

---

##  Data Dictionary


###  Raw Fields

These are the raw columns ingested directly from the CSV data source. Data was cleaned and merged in Python (pandas) before loading into Tableau.

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `state` | String | — | Raw | U.S. state name (51 values including D.C.) used as the primary geographic dimension |
| `date` | Date | YYYY-MM-DD | Raw | First day of each month; spans Jan 2024 – Feb 2026 (26 months) |
| `year` | Integer | Year | Raw | Calendar year extracted from `date` at source |
| `month` | Integer | Month number (1–12) | Raw | Calendar month extracted from `date` at source |
| `year_month` | String | "YYYY-MM" | Raw | Combined year-month label (e.g. "2024-01") for display and filtering |
| `home_value` | Float | USD ($) | Zillow ZHVI — state median home value | State-level median home value; primary price signal. Source: Zillow Home Value Index |
| `civilian_population` | Float | Persons | BLS LAUS raw | Civilian non-institutional population by state, used as labour market denominator |
| `labor_force_total` | Float | Persons | BLS LAUS raw | Total persons in the labour force (employed + unemployed) |
| `labor_force_participation_rate` | Float | Proportion (0–1) | BLS LAUS raw | Share of civilian population in the labour force |
| `employment_total` | Float | Persons | BLS LAUS raw | Total persons employed in the state |
| `employment_population_ratio` | Float | Proportion (0–1) | BLS LAUS raw | Employed persons as a share of civilian population |
| `unemployment_total` | Float | Persons | BLS LAUS raw | Total unemployed persons; corrupted Oct 2025 rows were forward-filled from Sep 2025 |
| `unemployment_rate` | Float | % (e.g. 3.5 = 3.5%) | BLS LAUS raw | State unemployment rate. Missing Feb 2026 forward-filled from Jan 2026; encoding-corrupt Oct 2025 rows replaced with Sep 2025 values |
| `mortgage_rate` | Float | % (e.g. 6.72 = 6.72%) | FRED MORTGAGE30US — weekly rates averaged to monthly | National 30-year fixed mortgage rate, converted from weekly to monthly by simple average |
| `income_2023` | Integer | USD ($) | U.S. Census ACS 2023 survey | State median household income from the 2023 ACS survey (reports on earnings ~1 year prior) |
| `income_2024` | Integer | USD ($) | U.S. Census ACS 2024 survey | State median household income from the 2024 ACS survey |
| `median_household_income_lagged` | Integer | USD ($) | Vintage matching: `income_2023` for months in 2024; `income_2024` for months in 2025–2026 | Annual income proxy applied to each month via "vintage matching" — the standard HUD approach when ACS data is published with a ~1-year lag |


---

### Core Calculated Fields

Foundational calculations that feed into scoring, KPIs, and the simulator. Arranged in dependency order (each field is built on those above it).

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `Date Year` | Integer | Year | `YEAR([date])` | Tableau-level year extraction from the date field; used in LOD and filter logic |
| `Date Month` | Integer | Month number | `MONTH([date])` | Tableau-level month extraction; used in LOD and filter logic |
| `Home Value ($K)` | Float | $K (thousands) | `[home_value] / 1000` | Rescales raw home value to thousands for compact axis labelling in charts |
| `Monthly Income` | Float | USD/month ($) | `[median_household_income_lagged] / 12` | Converts annual lagged income to a monthly figure; denominator for all burden ratio calculations |
| `Loan Amount` | Float | USD ($) | `[home_value] * 0.8` | 80% of home value, assuming the standard 20% down payment; the principal on which mortgage payments are calculated |
| `Monthly Rate` | Float | Decimal/month | `([mortgage_rate] / 100) / 12` | Converts the annual percentage mortgage rate to a monthly decimal rate for use in the amortisation formula |
| `Monthly Mortgage Payment` | Float | USD/month ($) | `[Loan Amount] * ([Monthly Rate] * (1 + [Monthly Rate])^360) / ((1 + [Monthly Rate])^360 - 1)` | Standard 30-year amortisation formula. Assumes 20% down payment and 360 monthly payments. Represents the P&I payment only (no taxes, insurance, or PMI) |
| `Mortgage Burden Ratio` | Float | Proportion (0–1) | `[Monthly Mortgage Payment] / [Monthly Income]` | Core affordability metric. Share of monthly income consumed by the mortgage payment. HUD thresholds: ≥0.30 = cost-burdened; ≥0.40 = severely cost-burdened; 0.20–0.30 = "stretched" (dashboard-defined warning zone) |
| `Affordability Ratio` | Float | Ratio | `[median_household_income_lagged] / [home_value]` | Annual income divided by home value. Higher = more affordable. Does not account for interest rates. One of the three components of the Investment Score |
| `Economic Stability` | Float | Proportion (0–1) | `1 - ([unemployment_rate] / 100)` | Employment rate expressed as a 0–1 score (e.g., 5% unemployment → 0.95). Ranges from ~0.93 to 0.98 across states, so its variance is lower than the other Investment Score components |
| `Investment Score` | Float | Decimal (~0.015–0.060) | `[Affordability Ratio] * (1 / [mortgage_rate]) * [Economic Stability]` | Raw composite score combining income-to-price affordability, inverse mortgage rate (lower rates boost the score), and employment stability. The pre-rescaling basis for the Market Health Score |
| `YoY Home Value Change` | Float | Proportion (0–1) | `(ZN(SUM([home_value])) - LOOKUP(ZN(SUM([home_value])), -12)) / ABS(LOOKUP(ZN(SUM([home_value])), -12))` | Table calculation: percent change in home value versus the same month 12 rows prior. Used in trend charts to show which states are appreciating or declining |
| `Monthly Savings from Rate Cut` | Float | USD/month ($) | `[Monthly Mortgage Payment] - [What-If Monthly Payment]` | Difference between the actual current mortgage payment and the What-If payment at the user-selected rate. Positive = savings; negative = cost increase |
| `Bar - National Average` | Float | USD ($) | `AVG([home_value])` | Simple national average home value across all states for the current filter context; used as the benchmark bar in the state comparison chart |
| `Bar - Selected State` | Float | USD ($) | `AVG(IF [state] = [Selected State] THEN [home_value] ELSE NULL END)` | Home value for only the currently selected state; placed alongside the national average bar for direct comparison |

---


### Parameters

Interactive controls that allow users to change dashboard behaviour without altering the underlying data.

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `What-If Rate` *(Parameter 1)* | Float | % | Default: `4.5`; range 3.0–10.0 | User-controlled mortgage rate for the What-If Rate Simulator; drives all What-If payment and burden calculations |
| `Selected State` *(Parameter 2)* | String | — | Default: `"All States"` | State name selected by the user via dropdown or map click; filters State View and drives cross-filter actions across KPI tiles, trend chart, and simulator |
| `KPI Anchor Year` *(Parameter 3)* | Integer | Year | Default: `2026` | Reference year for all "current vs. prior year" KPI comparisons; changing this lets the dashboard compare any year to the one before it |
| `KPI Anchor Month` *(Parameter 4)* | Integer | Month number | Default: `2` (February) | Reference month paired with Anchor Year to pin the "current period" for KPI snapshot calculations |

---

### Scoring & Classification Fields

Fields that convert raw metrics into categorical labels, scores, and rankings used across charts and the map.

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `KPI Market Health Score 0-10` | Float | Score (0–10) | `MIN(10, MAX(0, (AVG([Investment Score]) - 0.015) / (0.06 - 0.015) * 10))` | Rescales the raw Investment Score from its observed range (0.015 worst → 0.060 best) onto a 0–10 scale. Boundaries are data-driven (actual state min/max). Used in KPI tiles and tooltips |
| `Affordability Category` | String | Category label | `IF [Mortgage Burden Ratio] >= 0.40 THEN "Crisis (>40%)"` `ELSEIF >= 0.30 THEN "Cost-Burdened (30-40%)"` `ELSEIF >= 0.20 THEN "Stretched (20-30%)"` `ELSE "Affordable (<20%)"` | Four-tier label applied to each state-month row based on the Mortgage Burden Ratio. Drives colour coding and policy recommendations |
| `Investment Category` | String | Category label | `IF [Investment Score] >= 0.045 THEN "High Opportunity"` `ELSEIF >= 0.030 THEN "Moderate"` `ELSE "Low Opportunity"` | Three-tier opportunity label based on the raw Investment Score; used to colour bubbles in the Unemployment vs Affordability scatter plot |
| `KPI Market Health Category` | String | Category label | `IF [KPI MHS 0-10] >= 6 THEN "High"` `ELSEIF >= 3.5 THEN "Moderate"` `ELSE "Low"` | Converts the 0–10 Market Health Score into a named band (High / Moderate / Low) for KPI tile labelling |
| `KPI Affordability Category` | String | Category label | `IF [KPI Housing Affordability Score 0-10] >= 6 THEN "Healthy"` `ELSEIF >= 3.5 THEN "Moderate"` `ELSE "Stressed"` | Named band for the Housing Affordability Score KPI tile |
| `KPI Mortgage Category` | String | Category label | `IF AVG([mortgage_rate]) <= 5.5 THEN "Low"` `ELSEIF <= 7.0 THEN "Moderate"` `ELSE "High"` | Labels the current mortgage rate environment for the mortgage KPI tile |
| `KPI Econ Category` | String | Category label | `IF AVG([Economic Stability]) >= 0.97 THEN "High"` `ELSEIF >= 0.95 THEN "Moderate"` `ELSE "Low"` | Labels economic stability level for the employment KPI tile |
| `KPI YoY Category` | String | Category label | `IF [KPI YoY Value] >= 0.03 THEN "High"` `ELSEIF >= 0 THEN "Moderate"` `ELSE "Declining"` | Classifies home value year-on-year growth into High / Moderate / Declining for the KPI tile |
| `YoY Category` | String | Category label | `IF [YoY Home Value Change] >= 0 THEN "Growing" ELSE "Falling"` | Row-level binary label for trend charts, flagging each state-month as appreciating or declining |
| `KPI Housing Affordability Score 0-10` | Float | Score (0–10) | `MIN(10, MAX(0, (0.40 - AVG([Mortgage Burden Ratio])) / (0.40 - 0.10) * 10))` | Rescales the Mortgage Burden Ratio onto a 0–10 affordability score where 10 = most affordable (burden ≤10%) and 0 = least affordable (burden ≥40%) |
| `KPI YoY Value` | Float | Proportion | `(AVG([LOD HV Current]) - AVG([LOD HV Prior])) / ABS(AVG([LOD HV Prior]))` | Year-on-year percent change in home value anchored to the KPI Anchor Year/Month parameters; immune to user date filters because it uses FIXED LOD values |
| `KPI YoY by State` | Float | Proportion | `(AVG(home_value at Feb 2026) - AVG(home_value at Feb 2025)) / ABS(AVG(home_value at Feb 2025))` | Hard-coded Feb 2025 → Feb 2026 YoY change per state; used in the state ranking table rather than the parameter-driven KPI tile |
| `State Rank Sort` | Integer | 0 or 1 | `IF [state] = [Selected State] THEN 0 ELSE 1 END` | Sorts the selected state to the top of the ranking table by assigning it sort order 0 |
| `Is Selected State` | Boolean | True / False | `[state] = [Selected State]` | Boolean flag; used to conditionally highlight, filter, or show/hide elements related to the selected state |

---


### KPI Dashboard Fields

Fields that produce the summary numbers and direction arrows displayed in the five KPI tiles at the top of the Overview.

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `KPI MHS vs Last Year` | Float | Score delta | `[MHS at anchor year/month] - [MHS at prior year/same month]` (both rescaled 0–10) | Change in Market Health Score compared to the same month last year; positive = improving |
| `KPI Market health score delta` | String | Arrow symbol | `IF [KPI MHS vs Last Year] > 0 THEN "▲" ELSEIF < 0 THEN "▼" ELSE "—"` | Direction arrow for the Market Health Score KPI tile |
| `KPI Affordability vs Last Year` | Float | Score delta | `[Affordability Score at anchor] - [Affordability Score at prior year]` (both on 0–10 scale) | Change in Housing Affordability Score year on year; positive = more affordable |
| `KPI Affordability delta` | String | Arrow symbol | `IF [KPI Affordability vs Last Year] > 0 THEN "▲" ELSEIF < 0 THEN "▼" ELSE "—"` | Direction arrow for the Affordability KPI tile |
| `KPI YoY vs Last Year` | Float | Percentage point delta | Change in the YoY growth rate versus the prior year's equivalent YoY growth | Shows whether home value appreciation is accelerating or slowing |
| `KPI YoY Arrow` | String | Arrow symbol | `IF [KPI YoY vs Last Year] > 0 THEN "▲" ELSEIF < 0 THEN "▼" ELSE "—"` | Direction arrow for the Home Value YoY KPI tile |
| `KPI Mortgage vs Last Year` | Float | Percentage points | `AVG([LOD Mortgage Current]) - AVG([LOD Mortgage Prior])` | Change in mortgage rate (pp) compared to the same month last year |
| `KPI Mortgage Arrow` | String | Arrow symbol | `IF [KPI Mortgage vs Last Year] > 0 THEN "▲" ELSEIF < 0 THEN "▼" ELSE "—"` | Direction arrow for the Mortgage Rate KPI tile |
| `KPI Econ vs Last Year` | Float | Percentage points | `(AVG([LOD Econ Current]) - AVG([LOD Econ Prior])) * 100` | Change in Economic Stability (employment rate) in percentage points versus the same month last year |
| `KPI Econ Arrow` | String | Arrow symbol | `IF [KPI Econ vs Last Year] > 0 THEN "▲" ELSEIF < 0 THEN "▼" ELSE "—"` | Direction arrow for the Economic Stability KPI tile |
| `LOD Max Year` | Integer | Year | `{ FIXED : YEAR(MAX([date])) }` | The maximum year in the dataset, computed before any filters; used to set smart defaults |


---
### What-If Simulator Fields

Fields powering the interactive mortgage rate simulator. All depend on `[What-If Rate]` (Parameter 1).

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `What-If Monthly Payment` | Float | USD/month ($) | `([home_value] * 0.8) * (([What-If Rate]/100/12) * (1 + [What-If Rate]/100/12)^360) / ((1 + [What-If Rate]/100/12)^360 - 1)` | Mortgage payment recalculated using the user-selected hypothetical rate; identical 30-year amortisation formula with 20% down payment assumption |
| `What-If Mortgage Burden` | Float | Proportion (0–1) | `[What-If Monthly Payment] / [Monthly Income]` | Mortgage burden under the hypothetical rate; compared against HUD thresholds to show whether the rate cut resolves affordability |
| `Monthly Savings from Rate Cut` | Float | USD/month ($) | `[Monthly Mortgage Payment] - [What-If Monthly Payment]` | Dollar savings (or added cost) per month from applying the What-If rate instead of the actual current rate |
| `What-If Savings Label` | String | Label | `IF AVG([Monthly Savings]) >= 0 THEN "Save $" + STR(INT(savings)) ELSE "Cost +" + STR(INT(ABS(savings))) + " extra"` | Human-readable annotation displayed on the simulator bar chart (e.g. "Save $638") |
| `What-If Bar Color` | String | Category | `IF AVG([Monthly Savings]) >= 0 THEN "Savings" ELSE "Cost Increase"` | Drives green/red bar colouring in the What-If chart |
| `What if Filter Combined` | Boolean | True / False | `[Top 15 Payment States] OR ([state] = [Selected State])` | Limits the What-If chart to the top 15 highest-burden states plus whichever state the user has selected |

---

### Rate Sensitivity Fields

Pre-computed snapshots of mortgage payments and burden ratios at six fixed interest rates (4.0% to 6.5%). Used in the Rate Sensitivity table in the State View.

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `Rate Sensitivity 4.0%` | Float | USD/month ($) | `AVG([home_value]) * 0.8 * (0.04/12 * (1 + 0.04/12)^360) / ((1 + 0.04/12)^360 - 1)` | Monthly mortgage payment if the rate were 4.0% |
| `Rate Sensitivity 4.5%` | Float | USD/month ($) | Same formula with `0.045` | Monthly mortgage payment if the rate were 4.5% |
| `Rate Sensitivity 5.0%` | Float | USD/month ($) | Same formula with `0.05` | Monthly mortgage payment if the rate were 5.0% |
| `Rate Sensitivity 5.5%` | Float | USD/month ($) | Same formula with `0.055` | Monthly mortgage payment if the rate were 5.5% |
| `Rate Sensitivity 6.0%` | Float | USD/month ($) | Same formula with `0.06` | Monthly mortgage payment if the rate were 6.0% |
| `Rate Sensitivity 6.5%` | Float | USD/month ($) | Same formula with `0.065` | Monthly mortgage payment if the rate were 6.5% |
| `Rate Sensitivity Burden 4.0%` | Float | Proportion (0–1) | `[Rate Sensitivity 4.0%] / AVG([Monthly Income])` | Mortgage burden ratio at 4.0%; compared to HUD thresholds to assign Crisis / Burdened / Affordable status |
| `Rate Sensitivity Burden 4.5%` | Float | Proportion (0–1) | `[Rate Sensitivity 4.5%] / AVG([Monthly Income])` | Mortgage burden ratio at 4.5% |
| `Rate Sensitivity Burden 5.0%` | Float | Proportion (0–1) | `[Rate Sensitivity 5.0%] / AVG([Monthly Income])` | Mortgage burden ratio at 5.0% |
| `Rate Sensitivity Burden 5.5%` | Float | Proportion (0–1) | `[Rate Sensitivity 5.5%] / AVG([Monthly Income])` | Mortgage burden ratio at 5.5% |
| `Rate Sensitivity Burden 6.0%` | Float | Proportion (0–1) | `[Rate Sensitivity 6.0%] / AVG([Monthly Income])` | Mortgage burden ratio at 6.0% |
| `Rate Sensitivity Burden 6.5%` | Float | Proportion (0–1) | `[Rate Sensitivity 6.5%] / AVG([Monthly Income])` | Mortgage burden ratio at 6.5% |
| `Rate Row 4.0%` | String | Formatted label | Composite text: `"4.0%:: (Crisis/Burdened/Affordable) $[payment] /mo [burden]% burden"` using amortisation constant `0.004774` | Full formatted row label for the State View Rate Sensitivity table at 4.0% |
| `Rate Row 4.5%` | String | Formatted label | Same structure with constant `0.005066` | Rate Sensitivity table row at 4.5% |
| `Rate Row 5.0%` | String | Formatted label | Same structure with constant `0.005368` | Rate Sensitivity table row at 5.0% |
| `Rate Row 5.5%` | String | Formatted label | Same structure with constant `0.005679` | Rate Sensitivity table row at 5.5% |
| `Rate Row 6.0%` | String | Formatted label | Same structure with constant `0.005996` | Rate Sensitivity table row at 6.0% |
| `Rate Row 6.5%` | String | Formatted label | Same structure with constant `0.006320` | Rate Sensitivity table row at 6.5% |

> **Note on amortisation constants:** Each constant (e.g. `0.004774` for 4.0%) is the pre-computed monthly payment factor `r(1+r)^n / ((1+r)^n − 1)` for a 30-year loan at that rate, applied to every $1 of loan principal. This avoids repeated `POWER()` calls inside string calculations.

---

### Display / UI / Label Fields

Presentation-layer fields that generate human-readable text, conditional formatting, and dashboard navigation logic.

| Field Name | Type | Unit | Formula / Logic | Purpose |
|---|---|---|---|---|
| `State Insight` | String | Narrative text | Conditional text based on `[Mortgage Burden Ratio]`: crisis (≥40%) / cost-burdened (30–40%) / stretched (20–30%) / healthy (<20%) | Plain-English summary sentence shown in the State View tooltip (e.g. "This state is in housing crisis. Over 40% of income goes to mortgage alone.") |
| `Key Insight` | String | Narrative text | Parameterised text combining selected state name, burden %, and HUD threshold comparison | Generates the prominent insight panel text in the State View (e.g. "California is COST-BURDENED. 44.9% of income consumed by mortgage — above HUD's 30% threshold.") |
| `Recommended Policy Actions` | String | Ordered list | IF-ELSEIF logic on `[Mortgage Burden Ratio]` → outputs 4 numbered policy actions appropriate to the state's affordability tier | Displays context-specific policy recommendations in the State View panel |
| `State Insight Filter` | Boolean | True / False | `[state] = [Selected State] OR [Selected State] = "All States"` | Controls visibility of the State Insight text block; shows for the selected state or all states when no state is selected |
| `State Rank Label` | String | Label text | `IF ATTR([state]) = [Selected State] THEN "#" + RANK + " of 51 states" ELSE ""` | Displays the selected state's affordability rank in the ranking table (e.g. "#3 of 51 states") |
| `State Rank Row Colour` | String | "Show" / "Hide" | `IF ATTR([state]) = [Selected State] THEN "Show" ELSE "Hide"` | Drives conditional row highlighting in the state ranking table |
| `State Rank Sort` | Integer | 0 or 1 | `IF [state] = [Selected State] THEN 0 ELSE 1` | Forces the selected state to sort to the top of the ranking table |
| `Is Selected State` | Boolean | True / False | `[state] = [Selected State]` | Master flag for cross-filter actions; triggers highlight and detail updates across all dashboard views when a state is clicked |
| `Burden Filter Combined` | Boolean | True / False | `[Top 20 Burden States] OR ([state] = [Selected State])` | Filters the mortgage burden bar chart to the 20 highest-burden states plus the selected state |
| `What-If Bar Color` | String | "Savings" / "Cost Increase" | `IF AVG([Monthly Savings]) >= 0 THEN "Savings" ELSE "Cost Increase"` | Maps to green or red colour encoding in the What-If simulator bar chart |
| `KPI MHS vs Last Year` arrows (`▲▼—`) | String | Symbol | Arrow direction fields for each KPI | Provides instant visual direction cues alongside all five KPI delta values |

---

### Appendix: Key Thresholds & Business Rules

| Threshold | Source | Applied In |
|---|---|---|
| Mortgage Burden ≥ 40% = Severely Cost-Burdened | HUD standard | `Affordability Category`, `State Insight`, `Key Insight`, `Rate Row` labels |
| Mortgage Burden ≥ 30% = Cost-Burdened | HUD standard | Same as above |
| Mortgage Burden 20–30% = "Stretched" | Dashboard-defined early warning | `Affordability Category` |
| Market Health Score 6–10 = Healthy | Data-driven rescaling (0.015–0.060) | `KPI Market Health Category` |
| Market Health Score 3.5–6 = Moderate | Same | Same |
| Market Health Score 0–3.5 = Low / Stressed | Same | Same |
| Investment Score ≥ 0.045 = High Opportunity | Observed data quartile | `Investment Category` (scatter plot) |
| Investment Score 0.030–0.045 = Moderate | Same | Same |
| Investment Score < 0.030 = Low Opportunity | Same | Same |
| 20% down payment assumed | Industry standard / HUD | `Loan Amount` and all mortgage calculations |
| Income vintage matching | HUD methodology | `median_household_income_lagged` |
| Forward-fill for missing unemployment | Conservative imputation | `unemployment_rate` (Oct 2025, Feb 2026) |

---

##  Team & Contributions

| Name | Roles | Contribution | Student ID |
|---|---|---|---|
| Ankita Adiveppagouda Patil | Data Vizualization and Lead | Project Appraoch, Vizualization | 26022830 |
| Abhishek Chopda | Project Co-Manager and Github Lead | Project Management and Design and Presentation  | 25611094 |
| Ferdinando Jr Enriquez  | Project Manager | Project Management and Design and Presentation | 25935343 |
| Gem He  | Data Engineer and Powerpoint Artist | Data Cleaning and Preparation, Presentation Approach | 25992948 |
| Harshini Prasad  | Data Vizualization | Vizualization and Documentation | 26025369 |
| Ka Yan Cheng   | Dashboard Developer & Lead | Built the entire Tableau dashboard from scratch, including data sourcing, enrichment datasets, calculated fields & logic, charts, KPI cards, What-If calculator, Story points and documentation. Provided multiple versions and ongoing technical support. | 25979218 |
| Ranjan Khanal   | Data Engineer and Documentation | Data Cleaning and Documentation | 25946613 |

---


## Credits

This project was developed as part of the **Data Narratives Design & Storytelling Studio** assessment.

Data sources and supporting organisations:

- Zillow Research
- Federal Reserve Economic Data (FRED)
- U.S. Census Bureau
- Bureau of Labor Statistics (BLS)

A special thanks to our professor **Jared Wong** for his guidance and his teachings.

---

##  License

This repository is intended for academic and educational purposes only.
