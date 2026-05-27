# bmaruana01-FUTURE_DS_Task1
Future interns tasks

 Online Retail Analytics

A full end-to-end data analytics project covering data cleaning, exploratory analysis, and dashboard reporting on a real-world e-commerce transactional dataset.

** What this project does**
- Cleans raw retail data (handles cancellations, nulls, outliers, non-product entries, and type mismatches)
- Analyses revenue trends over time, top-selling products, and high-value customer regions
- Produces a multi-panel visual dashboard (matplotlib)
- Exports analysis-ready summary sheets to Excel
- Includes step-by-step Excel instructions for a client-ready
  interactive dashboard with PivotTables and slicers

**Key findings**
- Strong Q4 seasonality with November peak revenue
- United Kingdom accounts for ~82% of total revenue
- Netherlands, Ireland, and Germany lead international markets
- Top 10 SKUs contribute disproportionately to total revenue

  ** Tools & libraries**

| Layer | Tool | Purpose |
|---|---|---|
| Language | Python 3.x | Core scripting |
| Data wrangling | pandas | Cleaning, grouping, aggregation |
| Numerics | NumPy | Vectorised calculations |
| Visualisation | Matplotlib | Dashboard charts |
| Export | openpyxl | Writing Excel output files |
| Reporting | Excel (PivotTables) | Client-ready interactive dashboard |

**Python dependencies**
```bash
pip install pandas numpy matplotlib openpyxl
```

** File outputs**
| File | Description |
|---|---|
| `online_retail_cleaned.xlsx` | Cleaned dataset (main output of cleaning script) |
| `online_retail_returns.xlsx` | Separated cancellation / returns rows |
| `retail_analysis_output.xlsx` | Summary sheets: KPIs, monthly revenue, top products, countries |
| `retail_dashboard.png` | 6-panel visual dashboard (150 dpi) |


** Dataset**



| Property | Detail |
|---|---|
| Records | ~541,000 transactions (raw) |
| Period | December 2010 – December 2011 |
| Geography | 38 countries |
| Format | `.xlsx` |
| License | Public / open access |

### Columns

| Column | Type | Description |
|---|---|---|
| `InvoiceNo` | string | Unique invoice ID; prefix `C` = cancellation |
| `StockCode` | string | Product code |
| `Description` | string | Product name |
| `Quantity` | integer | Units per transaction |
| `InvoiceDate` | datetime | Date and time of transaction |
| `UnitPrice` | float | Price per unit (GBP) |
| `CustomerID` | string | Unique customer identifier (nullable) |
| `Country` | string | Customer country |

### Cleaning steps applied
- Removed fully duplicate rows
- Separated cancellations (InvoiceNo prefix `C`) and negative quantities
- Dropped administrative StockCodes (POST, DOT, AMAZONFEE, etc.)
- Filled missing descriptions via StockCode lookup
- Dropped zero / negative UnitPrice rows
- Tagged missing CustomerID rows as guest transactions (`IsGuest`)
- Standardised country names (EIRE → Ireland, etc.)
- Added derived column: `TotalPrice = Quantity × UnitPrice`
