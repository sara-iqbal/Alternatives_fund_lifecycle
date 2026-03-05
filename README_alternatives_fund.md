# Alternatives Fund Investor Lifecycle Tracker

**Sara Iqbal** | MSc Data Science | Portfolio Project

[Live Dashboard](https://sara-iqbal.github.io/alternatives-fund-investor-lifecycle) | [Google Colab Notebook](https://colab.research.google.com/drive/YOUR_COLAB_LINK) | [LinkedIn](https://www.linkedin.com/in/saraiqbaldata0602/)

---

## What This Project Is

This project simulates the complete operational lifecycle of a $500M alternatives fund from initial investor onboarding through to fund liquidation. It covers investor registration, AML/KYC status tracking, subscription document management, capital call and distribution scheduling, reporting obligations, side letter compliance, and the full pre-liquidation checklist.

The fund covers four alternative strategies: Private Equity, Private Credit, Real Assets, and Hedge Funds.

---

## What the Project Does

The pipeline runs in ten steps:

1. Defines the fund universe — a $500M alternatives fund with 50 investors across 8 jurisdictions and four fund strategies
2. Generates an investor register with AML/KYC status, risk ratings, FATCA/CRS classifications, subscription document status, side letter flags, and MLRO sign-off status per investor
3. Applies jurisdiction-specific risk profiles and AML/KYC review logic — UAE investors flagged High risk, escalated investors automatically assigned MLRO review
4. Simulates 12 months of capital calls and distributions using pro-rata allocation based on each investor's commitment size — producing investor-level call notices and distribution notices per month
5. Builds a reporting schedule across all approved investors — monthly NAV statements for Hedge Fund investors, quarterly capital account statements and reports for PE/PC/RA investors, and annual reports for all
6. Tracks side letter obligations per investor — bespoke reporting requirements, fee caps, co-investment rights, and ILPA reporting commitments
7. Generates capital account statements at year-end showing called capital, NAV, realised and unrealised value, management fees, carried interest, and estimated MOIC and IRR per investor
8. Produces a 24-item fund liquidation checklist covering all actions required before distributing liquidation payments — from final audit sign-off to regulatory deregistration
9. Exports an 8-sheet Excel file covering all of the above
10. Produces a summary of all key metrics across the full simulation

---

## Tools Used

Python, Pandas, NumPy, openpyxl, Chart.js

---

## Fund Universe

| Parameter | Detail |
|---|---|
| Fund size | $500M total commitments |
| Number of investors | 50 |
| Jurisdictions | US, UK, EU, Switzerland, Singapore, Japan, UAE, Canada |
| Fund strategies | Private Equity, Private Credit, Real Assets, Hedge Fund |
| Share classes | Single class — LP interests |
| Simulation period | 12 months (2024) |

---

## Investor Onboarding — AML/KYC Logic

| Status | Count | Description |
|---|---|---|
| Approved | 38 (76%) | MLRO signed off, subscription docs complete |
| Pending | 8 (16%) | Under review — docs incomplete or queried |
| Escalated | 4 (8%) | Referred to MLRO for enhanced due diligence |

Risk ratings are assigned by jurisdiction baseline and adjusted upward for escalated investors. FATCA/CRS classification is applied per jurisdiction — US investors receive W-9, non-US receive W-8BEN or CRS as applicable.

---

## Capital Call & Distribution Engine

Capital calls and distributions are allocated pro-rata to all approved investors based on their commitment as a percentage of the total approved commitment pool. Only investors with KYC Approved status receive call notices.

Each monthly record includes the fund-level amount, the investor's percentage, their individual allocation in dollars, the due date, and settlement status.

---

## Reporting Schedule

| Fund Type | Frequency | Report Types |
|---|---|---|
| Hedge Fund | Monthly | NAV Statement |
| Private Equity | Quarterly + Annual | Capital Account Statement, Quarterly Report, Annual Report, ILPA Report |
| Private Credit | Quarterly + Annual | Capital Account Statement, Quarterly Report, Annual Report |
| Real Assets | Quarterly + Annual | Capital Account Statement, Quarterly Report, Annual Report |

Side letter investors may have additional bespoke obligations — monthly NAV where not standard, ESG reports, ILPA template reporting, or audit inspection rights. These are tracked separately per investor.

---

## Results

| Metric | Value |
|---|---|
| Total investors | 50 across 8 jurisdictions |
| Total commitments | $500M |
| KYC approval rate | 76% (38 investors) |
| Side letter investors | 23 |
| Capital calls (12 months) | ~$312M called (62.4% of commitments) |
| Distributions (12 months) | ~$188M distributed |
| Total report obligations | 600+ across all investors and periods |
| On-time reporting rate | 100% (no missed deadlines in simulation) |
| Liquidation checklist | 18 of 24 items complete |
| Blocking items pre-distribution | 6 |
| Excel sheets exported | 8 |

---

## Excel Export — 8 Sheets

| Sheet | Contents |
|---|---|
| Investor Register | Full register of all 50 investors with onboarding details |
| AML/KYC Status | KYC status, risk rating, FATCA/CRS, MLRO sign-off per investor |
| Capital Calls | Monthly call notices with investor-level pro-rata allocations |
| Distribution Notices | Monthly distribution records with payment dates and status |
| Capital Accounts | Year-end capital account statements with NAV, MOIC, IRR |
| Reporting Schedule | Full report obligation list per investor per period |
| Side Letter Register | All 23 side letter investors with bespoke obligations |
| Liquidation Checklist | 24 pre-liquidation actions with owner and status |

---

## Dashboard

The GitHub Pages dashboard has five tabs:

- **Overview** — pipeline diagram, key metrics, fund snapshot charts
- **Investor Onboarding** — live filter by jurisdiction, AML/KYC status, risk rating, and fund type
- **Capital Calls** — enter a call amount and run it live to see pro-rata investor allocations update
- **Reporting Schedule** — select any month to see that period's full report obligation list
- **Fund Liquidation** — interactive checklist with clickable items and investor distribution register

---

## How to Run

Open the notebook in Google Colab and run all cells from top to bottom. No external data or API keys required — all data is generated within the notebook. The Excel file exports automatically at Step 9.

---

## Repository Structure

```
alternatives-fund-investor-lifecycle/
    index.html                              — GitHub Pages dashboard
    alternatives_fund_lifecycle.ipynb       — Google Colab notebook
    README.md                               — this file
```

---

## Other Projects

| Project | Tools | Description |
|---|---|---|
| Revenue Accrual & Fee Reconciliation Engine | Python, Pandas, openpyxl | 1,080 monthly fee calculations, 99.7% pre-investigation reconciliation accuracy |
| Bond Index Replication & Rebalancing Engine | Python, SciPy, NumPy | 150-bond replication of iShares LQD, tracking error 8.4 bps, IR 0.87 |
| Nexus Wealth Capital & Balance Sheet Optimizer | Python, Pandas, Streamlit | Basel III RWA engine, LCR monitoring, P&L waterfall |
| Real-Time Credit Card Fraud Detection | Python, XGBoost, SHAP | ROC-AUC 97.4%, F1 82.1% on 284,807 transactions |
| Algorithmic Trading Signal Engine | Python, PyTorch, LSTM | Directional accuracy 67.3%, Sharpe 1.42 |
