# Retail Sales & Profitability Analytics (Bangladesh)
**Portfolio demo | Synthetic retail orders | July–September 2026**

## Business question
Which months and product categories generated revenue and **gross profit**, and where did revenue miss targets?

## Stack
Python 3 (CSV, `decimal`, Matplotlib), Excel/Google Sheets-compatible CSV, SQL (SQLite). Power BI build guide included; **no pre-built `.pbix` is claimed**.

## Run
```bash
python -m pip install -r requirements.txt
python src/analyze.py
```
Open `outputs/revenue_vs_target.png` and the generated CSVs. `sql/analysis.sql` provides equivalent SQL; use the original workbook/lab SQLite file if available.

## Verified findings (practice data)
- 120 order records; **107 completed**.
- Completed-order **revenue: BDT 816,587.50**.
- COGS: BDT 544,500.00; **gross profit: BDT 272,087.50** (NOT net profit).
- July: BDT 218,365; August: BDT 342,887.50; September: BDT 255,335.
- August exceeded its BDT 330,000 revenue target; July and September missed theirs.

## Suggested decision
Inspect September's drop by category and channel before changing budget. Prioritize margin (not just volume); validate discounts, cancellations and attribution with real data.

## Files
- `data/`: synthetic raw/clean orders and lookup tables
- `src/analyze.py`: reproducible KPI logic and chart
- `outputs/`: verified charts and result tables
- `sql/analysis.sql`: SQLite aggregation
- `POWER_BI_BUILD_GUIDE.md`: steps to reproduce KPI report in Power BI

## Disclosure
Synthetic **training** dataset. This repository was initially generated as a reproducible portfolio demonstration; review, run and explain the analysis yourself before describing it as personal hands-on experience. No real business outcome is implied.
