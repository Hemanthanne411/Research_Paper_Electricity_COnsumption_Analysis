# Analyzing Seasonal and Sectoral Electricity Consumption Trends in Sweden

## 📊 Project Overview

This project analyzes 34 years of electricity consumption data in Sweden (1990-2024) to understand consumption patterns across different sectors and seasonal variations. The analysis applies statistical techniques to identify trends, quantify seasonal effects, and explore the relationship between domestic consumption and electricity exports.

---

## 🎯 Research Question

How has electricity consumption evolved over time across different sectors in Sweden, and how do seasonal variations influence sectoral electricity usage?

---

## 📁 Dataset

**Source:** Statistics Sweden (SCB) Database  
**Period:** January 1990 - December 2024 (34 years, monthly data)  
**Coverage:** ~420 data points per sector

**Sectors Analyzed:**
- Mining and Manufacturing
- Electricity, Gas, Heat and Water Plants
- Railways, Trams and Bus Traffic
- Residential and Other Services
- Exports

---

## 🔄 Analysis Workflow Diagram
```
┌─────────────────────────────────────────────────────────────┐
│              RAW DATASET (SCB Sweden)                       │
│         Monthly Electricity Consumption 1990-2024           │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ↓
┌─────────────────────────────────────────────────────────────┐
│          PHASE 1: DATA PREPARATION                          │
├─────────────────────────────────────────────────────────────┤
│  Categorized months into seasons                            │
│  (Winter, Spring, Summer, Autumn)                           │
│                                                             │
│  Output: ✅ Structured dataset ready for analysis           │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ↓
┌─────────────────────────────────────────────────────────────┐
│          PHASE 2: OVERALL TREND ANALYSIS                    │
├─────────────────────────────────────────────────────────────┤
│  Technique: CUSUM                                           │
│  Purpose: Detect consumption trend direction                │
│                                                             │
│  Result: ✅ Overall consumption INCREASING                  │
│          Stable until 2000, then sharp increase             │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ↓
┌─────────────────────────────────────────────────────────────┐
│          PHASE 3: SECTORAL ANALYSIS                         │
├─────────────────────────────────────────────────────────────┤
│  Step 3A: Average Consumption                               │
│  → Result: Residential sector highest consumer              │
│                                                             │
│  Step 3B: Growth Rates (CAGR)                               │
│  → Result: Residential growing, Power plants declining      │
│                                                             │
│  Step 3C: Power Plants Contribution                         │
│  → Result: Decreased from ~8% to ~3% (efficiency gains)     │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ↓
┌─────────────────────────────────────────────────────────────┐
│          PHASE 4: SEASONAL ANALYSIS                         │
├─────────────────────────────────────────────────────────────┤
│  Step 4A: Consumption by Season                             │
│  → Result: Residential peaks in winter                      │
│            Industrial stable year-round                     │
│                                                             │
│  Step 4B: Seasonality Strength Index (SSI)                  │
│  → Result: Residential highly seasonal (SSI=0.83)           │
│            Industrial weakly seasonal (SSI=0.28)            │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ↓
┌─────────────────────────────────────────────────────────────┐
│   PHASE 5: CONSUMPTION vs EXPORTS RELATIONSHIP              │
├─────────────────────────────────────────────────────────────┤
│  Step 5A: Group Comparison                                  │
│  → Result: Exports higher during low consumption            │
│                                                             │
│  Step 5B: Hypothesis Testing                                │
│  → Result: Difference is statistically significant          │
│                                                             │
│  Step 5C: Correlation Analysis                              │
│  → Result: Weak negative correlation (-0.23)                │
│                                                             │
│  Conclusion: Relationship exists but is weak                │
└──────────────────────────┬──────────────────────────────────┘
                           │
                           ↓
┌─────────────────────────────────────────────────────────────┐
│                    KEY INSIGHTS                             │
├─────────────────────────────────────────────────────────────┤
│  ✅ Overall consumption increasing                          │
│  ✅ Residential: highest & growing                          │
│  ✅ Power plants: declining (efficiency & renewables)       │
│  ✅ Residential highly seasonal, industrial stable          │
│  ✅ Weak export-consumption relationship                    │
└─────────────────────────────────────────────────────────────┘
```

## 🔄 Analysis Workflow

### Phase 1: Data Preparation
**Process:**
- Categorized months into meteorological seasons:
  - Winter: December, January, February
  - Spring: March, April, May
  - Summer: June, July, August
  - Autumn: September, October, November

**Output:** Structured dataset ready for temporal and seasonal analysis

---

### Phase 2: Overall Trend Analysis

**Objective:** Determine if Sweden's total electricity consumption is increasing, decreasing, or stable over 34 years

**Technique:** CUSUM (Cumulative Sum Control Chart)
- Detects structural breaks and trend shifts in time-series data
- Accumulates deviations from the mean to highlight overall direction

**Result:**  
✅ **Overall increasing trend** in electricity consumption from 1990-2024  
- Relatively stable consumption during 1990-2000  
- Sharp increase observed post-2000

**Visualization:** Time-series plot showing CUSUM values with zero reference line

---

### Phase 3: Sectoral Analysis

**Objective:** Identify which sectors consume the most electricity and analyze their growth trends

**Analysis Components:**

#### 3A. Average Consumption by Sector
**Method:** Calculated mean consumption across all years for each sector  

**Results:**
| Sector | Average Consumption (GWh) |
|--------|---------------------------|
| Residential and Other Services | 9,421 |
| Mining and Manufacturing | 4,339 |
| Electricity, Gas, Heat and Water Plants | 446 |
| Railways, Trams and Bus Traffic | 234 |

**Visualization:** Bar chart comparing average consumption

---

#### 3B. Growth Rate Analysis (CAGR)
**Method:** Compound Annual Growth Rate calculation  
**Formula:** `CAGR = [(End Value / Start Value)^(1/Years)] - 1`

**Results:**
| Sector | CAGR | Trend |
|--------|------|-------|
| Residential | +0.68% | Steady growth |
| Railways, Trams, Bus Traffic | +0.53% | Moderate growth |
| Mining and Manufacturing | -0.54% | Gradual decline |
| Electricity, Gas, Heat, Water Plants | -1.96% | Significant decline |

**Interpretation:**
- Residential sector shows consistent growth in consumption
- Power plants sector shows significant decline, likely reflecting improved efficiency and renewable energy adoption

---

#### 3C. Power Plants Contribution Over Time
**Method:** 12-month moving average of power plants' contribution to total consumption

**Finding:**  
✅ Power plants contribution decreased from ~7-8% (1990s) to ~3% (2024)  
- Indicates improved operational efficiency  
- Reflects Sweden's transition to renewable energy sources

**Visualization:** Line plot with moving average showing declining trend

---

### Phase 4: Seasonal Analysis

**Objective:** Quantify how seasonal variations affect electricity consumption across sectors

#### 4A. Consumption by Season
**Method:** Calculated average consumption for each sector across seasons

**Key Findings:**

**Residential Sector:**
- Winter: ~7,000 GWh (highest)
- Summer: ~3,000 GWh (lowest)
- Winter consumption ~2.3× higher than summer due to heating demand

**Mining and Manufacturing:**
- Relatively stable across all seasons (~4,200-4,400 GWh)
- Industrial operations maintain consistent year-round consumption

**Visualization:** Grouped bar chart showing sector-wise consumption across seasons

---

#### 4B. Seasonality Strength Index (SSI)
**Method:** Calculated SSI to quantify seasonal effect strength  
**Range:** 0 (no seasonality) to 1 (very strong seasonality)

**Results:**
| Sector | SSI | Seasonality Strength |
|--------|-----|---------------------|
| Residential | 0.83 | **Strong** - Highly seasonal |
| Electricity, Gas, Heat, Water Plants | 0.70 | Moderate |
| Railways, Trams, Bus Traffic | 0.56 | Moderate |
| Mining and Manufacturing | 0.28 | **Weak** - Stable year-round |

**Insight:** Residential sector exhibits strong sensitivity to seasonal changes; industrial sectors remain relatively stable

---

### Phase 5: Domestic Consumption vs Exports Relationship

**Objective:** Analyze whether electricity exports increase when domestic consumption decreases during summer

**Hypothesis:** When domestic consumption is low, Sweden exports more electricity (surplus energy utilization)

#### 5A. Comparative Analysis
**Method:** Split summer data into high vs low domestic consumption periods

**Results:**
- Mean exports during **low** domestic consumption: 2,098 GWh
- Mean exports during **high** domestic consumption: 1,731 GWh
- Difference: 367 GWh higher exports during low consumption periods

---

#### 5B. Statistical Validation
**Hypothesis Testing:**

**T-test:**
- Purpose: Compare means of two groups
- p-value: 0.039 (< 0.05)
- **Result:** ✅ Statistically significant difference

**Mann-Whitney U-test:**
- Purpose: Non-parametric alternative (no distribution assumptions)
- p-value: 0.044 (< 0.05)
- **Result:** ✅ Statistically significant difference

**Interpretation:** The difference in exports between high and low domestic consumption periods is real and not due to random chance

---

#### 5C. Correlation Analysis
**Method:** Measured relationship strength between domestic consumption and exports

**Results:**
- **Pearson Correlation:** -0.23 (weak negative linear relationship)
- **Spearman Correlation:** -0.24 (weak negative monotonic relationship)

**Interpretation:**  
- Negative correlation confirms inverse relationship: as domestic consumption decreases, exports tend to increase
- Weak strength (-0.23) indicates this is not a strong relationship
- Other factors also influence export levels beyond domestic demand

**Conclusion:** While statistically significant, the relationship between domestic consumption and exports is weak. Sweden can leverage surplus energy for export during low-demand periods, but the effect is modest.

---

## 🔑 Key Findings Summary

### 1. Overall Trend
- Sweden's total electricity consumption has increased from 1990-2024
- Acceleration in growth observed post-2000

### 2. Sectoral Insights
- **Residential sector:** Largest consumer with steady growth (+0.68% annually)
- **Power plants:** Significant decline (-1.96% annually)
  - Contribution dropped from ~7-8% to ~3%
  - Reflects efficiency improvements and renewable energy adoption
- **Industrial sectors:** Slight decline in consumption

### 3. Seasonal Patterns
- **Residential:** Highly seasonal (SSI = 0.83) with winter peaks for heating
- **Industrial:** Minimal seasonal variation (SSI = 0.28) - stable year-round operations

### 4. Consumption-Export Dynamics
- Weak but statistically significant negative correlation (-0.23)
- Exports increase when domestic demand is low
- Opportunity for surplus energy export, though relationship is not strong

---

## 🛠️ Methodology & Techniques

### Statistical Methods

**1. CUSUM (Cumulative Sum Control Chart)**
- Detects structural breaks in time-series trends
- Accumulates deviations from mean to identify overall direction
- Used for: Overall consumption trend analysis

**2. CAGR (Compound Annual Growth Rate)**
- Measures average annual growth rate
- Formula: `[(End/Start)^(1/Years)] - 1`
- Used for: Sectoral growth comparison

**3. Seasonality Strength Index (SSI)**
- Quantifies seasonal effect strength (0 to 1 scale)
- Higher values indicate stronger seasonal variations
- Used for: Identifying seasonal sensitivity by sector

**4. Moving Average (12-month)**
- Smooths short-term fluctuations to reveal trends
- Used for: Power plants contribution trend

**5. Hypothesis Testing**
- T-test: Parametric test comparing group means
- Mann-Whitney U-test: Non-parametric alternative
- Threshold: p-value < 0.05 for statistical significance
- Used for: Validating export differences

**6. Correlation Analysis**
- Pearson: Linear relationship strength
- Spearman: Monotonic relationship (rank-based)
- Range: -1 to +1
- Used for: Measuring consumption-export relationship

---

## 🧰 Tech Stack

**Language:** Python

**Libraries:**
- `pandas` - Data manipulation and preprocessing
- `numpy` - Numerical computations
- `matplotlib` - Data visualization
- `scipy.stats` - Statistical tests (T-test, Mann-Whitney, correlation)
- `statsmodels` - Time-series analysis

---

## 💡 Implications

**For Energy Planning:**
- Residential demand management needed for winter peaks
- Industrial sector provides stable, predictable base load
- Power sector efficiency gains support sustainability goals

**For Policy:**
- Seasonal patterns inform infrastructure planning
- Export opportunities during low-demand periods
- Continued support for renewable energy transition

---

## 🔮 Limitations & Future Work

**Limitations:**
- Analysis based on historical data only
- External factors (economic conditions, policy changes, energy prices) not included
- Extreme weather events not separately analyzed

**Future Directions:**
- Incorporate external economic and policy variables
- Develop predictive models for consumption forecasting
- Analyze extreme weather event impacts
- Investigate renewable energy adoption effects in detail

---

## 📚 Data Source

Statistics Sweden (SCB) - Electricity consumption by usage area. Monthly 1990M01 - 2024M12  
https://www.statistikdatabasen.scb.se/

---

## 👤 Author

Hemanth Kumar Anne  
Blekinge Institute of Technology  
hemanth.anne101@gmail.com
