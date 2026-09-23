# PPDAC Analysis: Telecom Customer Churn Prevention
## Step 3: DATA - Exploration & Key Findings

**Analysis Date:** September 23, 2026  
**Dataset:** telecom_churn.csv (n=3,333 customers)

---

## Data Quality Summary ✅

| Metric | Value |
|--------|-------|
| **Total Records** | 3,333 customers |
| **Churn Rate** | 14.49% (483 churned, 2,850 retained) |
| **Missing Values** | 0 (100% complete) |
| **Data Completeness** | ✅ 100% - Ready for Analysis |

---

## CRITICAL FINDINGS: Top 5 Churn Drivers

### 🔴 **#1: NO CONTRACT RENEWAL (Strongest Driver)**
- **Churn Rate Without Renewal:** 42.0% (137 of 323 customers)
- **Churn Rate With Renewal:** 11.5% (346 of 3,010 customers)
- **Impact:** 3.7x higher churn when no active contract renewal
- **Statistical Significance:** p < 0.001 ***
- **Business Insight:** Contract renewal is the strongest protective factor against churn

### 🔴 **#2: HIGH CUSTOMER SERVICE CALLS (Problem Signal)**
- **0-3 Calls:** ~10-13% churn rate (normal)
- **4 Calls:** 45.8% churn rate
- **5 Calls:** 60.6% churn rate  
- **6+ Calls:** 55-100% churn rate
- **Statistical Significance:** p < 0.001 ***
- **Business Insight:** Multiple service calls indicate customer dissatisfaction; escalates churn risk dramatically

### 🔴 **#3: HIGH DAYTIME MINUTES USAGE (Usage Pattern)**
- **Churned Customers:** 206.91 min/day avg
- **Retained Customers:** 175.18 min/day avg
- **Difference:** 31.74 minutes more (+18% higher usage)
- **Correlation:** r = 0.205
- **Statistical Significance:** p < 0.001 ***
- **Business Insight:** Heavy users may be underserved by current plans/pricing

### 🟡 **#4: NO DATA PLAN (Service Gap)**
- **Churn Rate Without Data Plan:** 16.7% (403 of 2,411)
- **Churn Rate With Data Plan:** 8.7% (80 of 922)
- **Difference:** 2x higher churn without data plan
- **Statistical Significance:** p < 0.001 ***
- **Business Insight:** Data plan adoption is protective; missing service offering

### 🟡 **#5: HIGH OVERAGE FEES (Pricing Pain)**
- **Correlation with Churn:** r = 0.093
- **Churned Customers Overage Fee Avg:** $10.62
- **Retained Customers Overage Fee Avg:** $9.95
- **Difference:** $0.67 higher (6.7% more)
- **Statistical Significance:** p < 0.001 ***
- **Business Insight:** Unexpected charges drive dissatisfaction

---

## Lifetime Patterns (Account Tenure Analysis)

| Tenure Group | Customers | Churn Rate | Risk Level |
|--------------|-----------|-----------|------------|
| 0-30 weeks | 128 | 14.1% | 🟡 Moderate |
| 30-60 weeks | 383 | 12.8% | 🟢 Lower |
| 60-90 weeks | 821 | 13.4% | 🟢 Lower |
| 90-120 weeks | 963 | **16.0%** | 🟠 **Higher** |
| 120-150 weeks | 682 | 14.4% | 🟡 Moderate |
| 150-180 weeks | 268 | 15.3% | 🟡 Moderate |
| 180+ weeks | 88 | 14.8% | 🟡 Moderate |

**Key Finding:** Churn risk peaks at 90-120 weeks (~ 2 years). This may be a contract renewal decision point.

---

## Feature Correlation Rankings

| Rank | Feature | Correlation | Direction | Strength |
|------|---------|-------------|-----------|----------|
| 1 | **ContractRenewal** | -0.260 | Protective | Strong ⭐⭐⭐ |
| 2 | **CustServCalls** | +0.209 | Risk | Strong ⭐⭐⭐ |
| 3 | **DayMins** | +0.205 | Risk | Strong ⭐⭐⭐ |
| 4 | **DataPlan** | -0.102 | Protective | Moderate ⭐⭐ |
| 5 | **OverageFee** | +0.093 | Risk | Weak-Moderate ⭐ |
| 6 | **DataUsage** | -0.087 | Protective | Weak-Moderate ⭐ |
| 7 | **MonthlyCharge** | +0.072 | Risk | Weak ⭐ |
| 8 | **RoamMins** | +0.068 | Risk | Weak ⭐ |
| 9 | **DayCalls** | +0.018 | Risk | Negligible |
| 10 | **AccountWeeks** | +0.017 | Risk | Negligible |

---

## High-Risk Customer Segments

### 🔴 Segment A: "No Contract, High Service Calls"
- No contract renewal + 4+ service calls
- Estimated churn rate: **50-65%** (extreme risk)
- Action: URGENT intervention required

### 🔴 Segment B: "No Contract Renewal"  
- Contract renewal status = 0
- Base churn rate: **42%** (severe risk)
- Action: Contract retention priority

### 🟠 Segment C: "High Usage, No Data Plan"
- DayMins > 200 AND no data plan
- Estimated churn rate: **20-25%** (high risk)
- Action: Upgrade data plan offer

### 🟡 Segment D: "Overcharged Heavy Users"
- DayMins > 200 AND OverageFee > $10
- Estimated churn rate: **15-18%** (moderate risk)
- Action: Plan optimization offer

---

## Statistical Validation

**All Top 5 Drivers Confirmed Significant (p < 0.05):**
- ContractRenewal: p < 0.000001 ***
- CustServCalls: p < 0.000001 ***
- DayMins: p < 0.000001 ***
- DataPlan: p < 0.000001 ***
- OverageFee: p < 0.000001 ***

**Not Significant (control variables):**
- AccountWeeks: p = 0.340 (tenure alone not predictive)
- DayCalls: p = 0.287 (call frequency not predictive, only service calls matter)

---

## Next Steps

✅ Data exploration complete  
✅ Top churn drivers identified and validated  
✅ High-risk segments mapped  
⏭️ Move to ANALYSIS phase: Quantify impact and ROI of interventions

---

**Status**: ✅ Data Phase Complete  
**Confidence Level**: HIGH - All findings statistically significant (p < 0.05)  
**Next Step**: ANALYSIS - Segment deep-dive and ROI modeling
