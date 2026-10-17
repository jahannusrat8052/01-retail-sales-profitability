# Power BI build guide (not a completed .pbix)
1. Get Data → Text/CSV, load `orders_clean.csv`, `products.csv`, `targets.csv`.
2. In Power Query check OrderDate=Date, Qty=Whole Number, UnitPriceBDT/DiscountRate=Decimal; Trim text. Close & Apply.
3. Model: one-to-many `products[ProductID]` to `orders_clean[ProductID]`. Mark the cleaned order table as `Orders` if desired.
4. DAX calculated column in Orders: `RevenueBDT = IF(Orders[Status]="Completed",Orders[Qty]*Orders[UnitPriceBDT]*(1-Orders[DiscountRate]),0)`.
5. DAX calculated column: `COGSBDT = IF(Orders[Status]="Completed",Orders[Qty]*RELATED(products[UnitCostBDT]),0)`.
6. Measures: `Revenue = SUM(Orders[RevenueBDT])`, `COGS = SUM(Orders[COGSBDT])`, `Gross Profit = [Revenue]-[COGS]`, `Gross Margin = DIVIDE([Gross Profit],[Revenue],0)`.
7. Build cards for Revenue / Gross Profit / Completed Orders, line chart monthly Revenue, bar chart by Category, slicers City and Channel.
8. Add Month column `Month = FORMAT(Orders[OrderDate],"yyyy-MM")` to compare with monthly target table; use a properly unique Month dimension before connecting target values to avoid duplicate counting.
9. Validate totals against `outputs/summary.json` before publishing; if not validated, do not add a published Power BI report link to your CV.
