# 🏦 Banking Risk Analytics Dashboard

A Power BI dashboard solution designed to minimize lending risk in banking and financial services by enabling data-driven loan approval decisions based on client profiles.

---

## 📌 Problem Statement

Financial institutions face significant risk when lending to customers without a reliable mechanism to assess repayment likelihood. This project addresses the need for a centralized, interactive analytics solution that:

- Consolidates client banking data across multiple sources
- Evaluates individual risk profiles
- Empowers decision-makers to approve or decline loans based on objective, data-backed insights

---

## 💡 Solution

Power BI dashboards that help banks make decisions based on applicant profiles — if an applicant is likely to repay the loan, the loan is approved; otherwise, it is declined.

---

## 📂 Dataset Overview

The dataset contains information about bank and client details across **5 interlinked tables**:

| Table | Description |
|-------|-------------|
| `Banking Relationship` | Bank-level relationship data |
| `Client-Banking` | Core client financial data |
| `Gender` | Gender classification |
| `Investment Advisor` | Advisor assignment details |
| `Period` | Time period references |

Tables are connected via **primary keys** and **foreign keys**.

---

## 🔧 Data Cleaning & Feature Engineering

The following transformations were applied to the `Client-Banking` table:

- **Engagement Timeframe** — Timeline of how long clients have been with the bank
- **Engagement Days** — Number of days since the client joined (`DATEDIFF` from join date to today)
- **Income Band** — Binned income categories: `Low` (< 100K), `Mid` (< 300K)
- **Processing Fees** — Fee rate derived from fee structure (e.g., `High` → 0.05)

---

## 📐 DAX Measures & Functions

| Function | Purpose | Example |
|----------|---------|---------|
| `SUM` | Aggregates numeric columns | `Bank Deposit = SUM('Clients - Banking'[Bank Deposits])` |
| `DISTINCTCOUNT` | Counts unique values | `Total Clients = DISTINCTCOUNT('Clients - Banking'[Client ID])` |
| `SUMX` | Row-by-row expression sum | `Total Fees = SUMX('Clients - Banking', [Total Loan] * [Processing Fees])` |
| `SWITCH` | Conditional value mapping | Fee structure categorization |
| `DATEDIFF` | Date interval calculation | `Engagement Days = DATEDIFF([Joined Bank], TODAY(), DAY)` |

---

## 📊 KPIs

| KPI | Description |
|-----|-------------|
| **Total Clients** | Distinct count of all bank clients |
| **Total Loan** | Bank Loan + Business Lending + Credit Card Balance |
| **Bank Loan** | Total loan amount to be repaid by clients |
| **Business Lending** | Loans issued to small businesses |
| **Total Deposit** | Bank Deposit + Savings + Foreign Currency + Checking Accounts |
| **Total Fees** | Processing fees charged based on loan amount |
| **Bank Deposit** | Money deposited into the bank |
| **Checking Accounts** | Transactional account balances |
| **Savings Account** | Interest-bearing deposit balances |
| **Foreign Currency Account** | Balances held in non-domestic currencies |
| **Credit Cards Balance** | Total outstanding credit card debt |
| **Engagement Length** | Sum of engagement days across all clients |

---

## 📈 Dashboard Pages

1. **Home** — Overview of key banking metrics
2. **Loan Analysis** — Breakdown of loan types, amounts, and risk
3. **Deposit Analysis** — Insights into deposits across account types
4. **Summary Dashboard** — Consolidated view for executive reporting

---

## 🔍 Key Insights

- **Private banks** have a higher number of clients compared to public banks
- Nationality-wise loan exposure is tracked to identify high-risk segments
- Account-level investment patterns inform growth and retention strategies

---

## 🚀 Future Work

- Identify which bank types attract more clients to help others build competitive strategies
- Surface nationality-level insights on loan defaults and repayment patterns
- Provide granular breakdowns of deposit amounts by account type and investor segment
- Expand dashboard to include predictive loan default scoring

---

## 🛠️ Tools & Technologies

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Excel](https://img.shields.io/badge/Excel-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)

---

## 📁 Project Structure

```
banking-dashboard/
├── data/
│   ├── Banking_Relationship.csv
│   ├── Client_Banking.csv
│   ├── Gender.csv
│   ├── Investment_Advisor.csv
│   └── Period.csv
├── dashboard/
│   └── Banking_Dashboard.pbix
├── docs/
│   └── Banking_Report.docx
└── README.md
```

---
