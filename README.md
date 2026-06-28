# Part 4: Tableau Executive Dashboard & Data Storytelling

**Student Name:** Dhruv Malik  
**Student ID:** BITSoM_BA_2511947  
**Repository:** `dhruvmalik_bitsom_ba_2511947_part4_tableau_dashboard`

---

## Business Problem Summary

The retail leadership team requires an executive dashboard to monitor and act on sales performance, profitability, customer segment behavior, shipping effectiveness, discount impact, and return patterns across a two-year period (Jan 2024 – Dec 2025). The dashboard must support data-driven decisions on where to invest, where to cut, and where risks are growing.

---

## Dataset Description

**File:** `data/dashboard_sales_data.xlsx`  
**Records:** 4,200 orders  
**Fields:** 20 columns  
**Date Range:** January 2024 – December 2025

| Field | Type | Description |
|---|---|---|
| order_id | String | Unique order identifier |
| order_date / ship_date | Date | Order placed and shipped dates |
| customer_id | String | Customer identifier |
| customer_segment | String | Consumer / Corporate / Home Office |
| region / state / city | String | Geographic hierarchy |
| category / sub_category | String | Product hierarchy |
| ship_mode | String | Shipping tier used |
| sales | Decimal | Order revenue |
| quantity | Integer | Units ordered |
| discount | Decimal | Discount rate applied (0–1) |
| profit | Decimal | Gross profit |
| return_flag | Integer | 1 = returned, 0 = not returned |
| delivery_days | Integer | Days from order to delivery |
| customer_rating | Decimal | Customer satisfaction score |
| campaign_channel | String | Acquisition channel |

---

## Tableau Workbook Description

**File:** `tableau/executive_dashboard.twbx`

The workbook contains 7 worksheets and 1 executive dashboard:

| Sheet | Purpose |
|---|---|
| Sales Trend | Monthly sales line chart (2024 vs 2025 YoY) |
| Regional Performance | Grouped bar: Sales & Profit by Region |
| Category Profitability | Horizontal bar: Profit by Sub-Category, colored by Category |
| Customer Segment View | Grouped bar: Sales & Profit by Segment |
| Shipping Performance | Bar: Avg Delivery Days by Ship Mode with Delay Bucket |
| Discount vs Profit | Scatter plot: Discount rate vs Profit with zero-line |
| Return Analysis | Bar: Return Rate by Category |
| Executive Dashboard | Combined view with KPI cards, 7 charts, and 5 filters |

---

## Calculated Fields Created

| Field | Formula |
|---|---|
| Profit Margin | SUM([profit]) / SUM([sales]) |
| Cost | [sales] - [profit] |
| Average Order Value | SUM([sales]) / COUNTD([order_id]) |
| Return Rate | SUM([return_flag]) / COUNTD([order_id]) |
| Shipping Delay Bucket | IF delivery_days <= 1 → Fast; <= 3 → Standard; <= 5 → Slow; else Very Slow |
| Discount Tier | Grouped discount ranges (None / 0-10% / 10-20% / 20-30% / 30%+) |
| Is Returned | Human-readable version of return_flag |
| Profit Per Order | SUM([profit]) / COUNTD([order_id]) |

---

## Dashboard Components

- **5 KPI Cards:** Total Sales, Total Profit, Profit Margin, Return Rate, Avg Order Value
- **7 Chart Views:** Sales Trend, Regional Performance, Category Profitability, Customer Segment, Shipping Performance, Discount vs Profit, Return Analysis
- **5 Filters:** Region, Category, Customer Segment, Order Date, Ship Mode
- **1 Action Filter:** Clicking a Region bar filters all connected views

---

## Filters and Interactions

- Global filters applied to all sheets from the dashboard
- Region, Category, Segment: List filters (multi-select)
- Order Date: Range filter (slider)
- Ship Mode: Checkbox filter
- Action: Click on Regional bar → highlights matching data in trend and category views

---

## Key Business Insights

1. South region leads all geographies in sales ($64.7M) and profit ($9.99M)
2. Technology generates 84% of total company profit — Copiers, Phones, Accessories are top sub-categories
3. Year-over-year sales are growing ~12% (2025 vs 2024)
4. Standard Class shipping averages 4.7 days — the slowest tier, used by majority of customers
5. 30%+ discount orders frequently yield negative profit — discount policy reform needed
6. Home Office segment leads in sales ($74.5M); Corporate segment is underleveraged
7. Return rate is 4.5% overall; Furniture has the highest concentration of costly returns
8. Referral and Organic channels produce higher-quality customers than Paid channels

---

## Dashboard Story Summary

The business is growing with a clear profit engine in Technology. The South region and Home Office segment are bright spots. Key risks include margin erosion from excessive discounting, slow Standard Class shipping hurting satisfaction, and over-reliance on Technology for profit. Leadership should introduce a discount authorization policy, replicate South's execution model across other regions, and shift investment toward Corporate segment growth.

Full story in: `outputs/dashboard_story.md`

---

## Assumptions and Limitations

- return_flag = 1 is treated as a returned order; no partial return logic is modeled
- campaign_channel has ~3% null values; those orders are excluded from channel analysis
- Profit represents gross margin; no SG&A or operating expenses are included
- Geographic analysis is at Region level; state/city breakdown is available in the workbook
- Dataset limited to 2024–2025; no pre-campaign baseline data is available

---

## Screenshots Included

| File | Contents |
|---|---|
| screenshots/full_dashboard.png | Complete executive dashboard with KPIs and all charts |
| screenshots/sales_trend_view.png | Monthly sales trend 2024–2025 |
| screenshots/regional_performance_view.png | Sales and profit by region |
| screenshots/category_profitability_view.png | Sub-category profit ranked bar chart |
| screenshots/filter_interaction_view.png | Filter applied: Technology category, West region |
