# albertus-ariel-securebank-credit-risk-segmentation
Credit card approval optimization at SecureBank through multi-variable risk segmentation — identifying high-risk applicant profiles across 438K+ records to reduce default approvals by 10%.

# 🏦 SecureBank Credit Risk Segmentation Analysis

**Program:** RevoU FSDA October '25 — Batch Amsterdam, Team 6  
**Author:** Albertus Ariel Renara Pranata  
**Tools:** Python (Google Colab) · Tableau · Statistical Testing

---

## 📌 Business Problem

SecureBank's current approval system relies heavily on income as the primary screening variable. Despite a low overall default rate **(0.83%)**, approximately **10.9% of approved applicants** fall into high-risk categories — meaning 1 in 9 approved customers disproportionately contributes to potential losses.

**Three core gaps identified:**
- 🔴 Income alone does not differentiate default risk (p = 0.658, not significant)
- 🟠 Unemployed applicants are **33% more likely to default** than employed ones
- 🟡 High-risk combinations (Low Income + Large Family) reach **3.48% default rate** — 4x the average

---

## 🎯 Objective

Shift from an income-only approval strategy to a **multi-variable risk segmentation model**, targeting a **≥10% reduction in high-risk approvals** within the next quarter.

---

## 🗂️ Dataset Overview

| Table | Records | Description |
|-------|---------|-------------|
| `application_record` | 438,557 | Applicant demographic & financial data |
| `credit_record` | 1,048,575 | Monthly credit status history per applicant |
| **Merged dataset** | 438,557 | Final analysis table with `DEFAULT_FLAG` |

**Key Variables Analyzed:**

| Variable Group | Columns |
|----------------|---------|
| Demographics | `AGE_YEARS`, `CODE_GENDER`, `NAME_FAMILY_STATUS` |
| Financial Stability | `AMT_INCOME_TOTAL`, `NAME_INCOME_TYPE`, `EMPLOYED_YEARS`, `IS_UNEMPLOYED` |
| Household Profile | `CNT_CHILDREN`, `CNT_FAM_MEMBERS` |
| Credit Behavior | `STATUS`, `DEFAULT_FLAG`, `MONTHS_BALANCE` |
| Assets | `FLAG_OWN_CAR`, `FLAG_OWN_REALTY` |

---

## 🔬 Methodology
| Phase | Key Actions |
|-------|-------------|
| Data Cleaning | Handle missing values, correct data types, merge tables |
| EDA | Descriptive stats, distribution analysis, boxplots |
| Hypothesis Testing | Mann-Whitney U, Chi-Square tests per variable |
| Risk Segmentation | Income × Employment × Family Size matrix analysis |

---

## 📊 Key Findings

### Hypothesis Testing Results

| Variable | Test | p-value | Result |
|----------|------|---------|--------|
| Income Level | Mann-Whitney U | 0.658 | ❌ Not Significant |
| Employment Status | Chi-Square | 0.05 | ✅ Significant |
| Real Estate Ownership | Chi-Square | 0.0056 | ✅ Significant |
| Household Size | Mann-Whitney U | 0.687 | ❌ Not Significant |

### Risk Concentration Matrix

| Segment | Income | Family | Status | Default Rate |
|---------|--------|--------|--------|-------------|
| 🔴 Highest Risk | Low | Large | Employed | **3.48%** |
| 🔴 High Risk | High | Small | Unemployed | **1.54%** |
| 🔴 High Risk | Low | Small | Unemployed | **1.57%** |
| 🟢 Lowest Risk | Very High | Small | Employed | **0.09%** |
| 🟢 Low Risk | Mid | Small | Employed | **0.69%** |

### Default Rate by Key Dimensions

| Dimension | Highest Risk | Rate | Lowest Risk | Rate |
|-----------|-------------|------|-------------|------|
| Occupation | IT Staff | 3.33% | Cooking Staff | 0.76% |
| Education | Lower Secondary | 1.87% | Academic Degree | 0.00% |
| Employment | Unemployed | 1.04% | Employed | 0.78% |
| Family Size | Large (5+) | >1.0% | Small | 0.70% |

---

## 💡 Recommendations

| Priority | Action | Expected Impact |
|----------|--------|-----------------|
| 🔴 Stop | Tightening income thresholds | Income is statistically flat across risk groups |
| 🔴 Implement | Stricter cut-offs for unemployed applicants | Eliminate 33% higher-risk approvals |
| 🟡 Penalize | "Toxic Trio": Unemployed + Low Income + Large Family | Target 3.48% default segment |
| 🟡 Add | Family size as weighted factor in scorecard | Capture affordability stress signal |
| 🟢 Use | Occupation as risk multiplier/screener | Differentiate 3.33% vs 0.76% default roles |
| 🟢 Build | Segment-based approval rules (Income × Employment × Family) | Cut defaults by ≥10% |

---

## 📁 Repository Structure
securebank-credit-risk-segmentation/
├── README.md
├── deck/
│   └── DEEPP Final Deck_SecureBank_Risk Segmentation Analysis _Albertus Ariel R P.pdf
├── notebook/
│   └── securebank_analysis.ipynb        ← Google Colab workbook
├── dashboard/
│   └── tableau_workbook_link.md         ← Tableau Public link

---

## 🔗 External Links

| Resource | Link |
|----------|------|
| 📊 Tableau Dashboard | [Credit Risk Segmentation Dashboard](https://public.tableau.com/views/TableauDEEPPRiskSegmentationWorkbook-AlbertusArielR/Dashboard1) |
| 💻 Google Colab Notebook | [Analysis Notebook](https://drive.google.com/file/d/1Zd_wZ4MwsK4ElQZgL96xLCY22z5sl42e/view) |

---

## 📬 Contact

**Albertus Ariel Renara Pranata**  
arielrenara@gmail.com  
[LinkedIn — Ariel Renara](https://www.linkedin.com/in/arielrenara)
