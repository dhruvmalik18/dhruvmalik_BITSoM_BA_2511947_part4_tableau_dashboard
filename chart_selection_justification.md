# Chart Selection Justification
**Analyst:** Dhruv Malik | BITSoM_BA_2511947

---

## Chart 1 — Sales Trend: Line Chart

**Question answered:** How is sales revenue changing over time month by month?

**Why this chart type:** A line chart is the gold standard for continuous time-series data. It shows the direction of change, rate of change, and seasonality patterns simultaneously. The human eye naturally reads slope as trend.

**Fields used:**
- X-axis: MONTH(Order Date)
- Y-axis: SUM(Sales)
- Color: Year (to enable YoY comparison)

**Design principle applied:** Use lines for time-based continuity; avoid bar charts for dense time series as they become visually cluttered.

**Mistake avoided:** Did not use a bar chart, which would obscure the trend signal with visual noise when there are 24 monthly data points.

---

## Chart 2 — Regional Performance: Grouped Bar Chart

**Question answered:** Which region generates the most sales and profit, and how do these two measures compare within each region?

**Why this chart type:** A grouped bar chart allows side-by-side comparison of two measures (Sales and Profit) across four categorical groups (Regions). It makes both within-group and across-group comparisons easy.

**Fields used:**
- X-axis: Region
- Y-axis: SUM(Sales), SUM(Profit)
- Color: Measure Name (Sales = blue, Profit = teal)

**Design principle applied:** Consistent color assignment for each measure across all charts to build visual vocabulary for the viewer.

**Mistake avoided:** Did not use a pie chart, which would be unable to show both Sales and Profit simultaneously and would distort perception of small differences.

---

## Chart 3 — Category Profitability: Horizontal Bar Chart

**Question answered:** Which sub-categories generate the most and least profit?

**Why this chart type:** A horizontal bar chart is ideal when category labels are long (sub-category names). Sorting by profit value makes ranking immediately visible. The horizontal layout prevents label truncation.

**Fields used:**
- Y-axis: Sub-Category (sorted by profit ascending)
- X-axis: SUM(Profit)
- Color: Category (to group sub-categories visually by parent)

**Design principle applied:** Sort bars by value to enable rank comparison. Use color only to encode a meaningful dimension (Category), not for decoration.

**Mistake avoided:** Did not use a treemap alone, which would be harder to rank precisely. Did not use a vertical bar chart, which would truncate long sub-category names.

---

## Chart 4 — Customer Segment View: Grouped Bar Chart

**Question answered:** How do the three customer segments compare in terms of sales and profit contribution?

**Why this chart type:** A grouped bar chart cleanly compares two measures across three segments. The small number of categories (3) and measures (2) makes grouped bars highly readable.

**Fields used:**
- X-axis: Customer Segment
- Y-axis: SUM(Sales), SUM(Profit)
- Color: Measure Name

**Design principle applied:** Same color palette as Regional chart to maintain consistency — viewers learn the color code once and apply it everywhere.

**Mistake avoided:** Did not use a stacked bar, which would make it impossible to compare individual values precisely (stacking hides the baseline for all but the first segment).

---

## Chart 5 — Shipping Performance: Horizontal Bar Chart (Avg Delivery Days)

**Question answered:** Which shipping mode is fastest and slowest on average?

**Why this chart type:** A simple horizontal bar chart sorted by delivery time makes the ranking immediately actionable. Viewers can instantly see that Standard Class is 3x slower than First Class.

**Fields used:**
- Y-axis: Ship Mode
- X-axis: AVG(Delivery Days)
- Color: Shipping Delay Bucket (calculated field — green for fast, red for slow)

**Design principle applied:** Use color to encode urgency — red for slow shipping signals risk to the viewer without requiring them to read the numbers first.

**Mistake avoided:** Did not use a line chart (shipping mode is not a continuous variable). Did not use a pie chart (delivery days are not parts of a whole).

---

## Chart 6 — Discount vs Profit: Scatter Plot

**Question answered:** Is there a relationship between discount level and profit? Do higher discounts lead to lower profit?

**Why this chart type:** A scatter plot is the correct choice for showing the relationship between two continuous numerical variables. It reveals correlation, clustering, and outliers that no other chart type can show simultaneously.

**Fields used:**
- X-axis: Discount (continuous)
- Y-axis: Profit (continuous)
- Color: Category (to see if discount-profit dynamics differ by category)
- Reference line at Y=0 (profit breakeven)

**Design principle applied:** Added a zero-profit reference line to make negative profit orders immediately visible. This turns a descriptive chart into a decision-support tool.

**Mistake avoided:** Did not aggregate by discount tier and show a bar chart, which would have hidden the distribution and variance. The scatter plot reveals that some 0% discount orders also have negative profit (likely cost issues), which aggregation would mask.

---

## Chart 7 — Return Analysis: Bar Chart by Category

**Question answered:** Which categories have the highest return rates?

**Why this chart type:** A bar chart comparing return rate across three categories (Furniture, Office Supplies, Technology) is clean and direct. Return rate is a proportion, making bar height easy to interpret.

**Fields used:**
- X-axis: Category
- Y-axis: Return Rate (calculated field)
- Color: Category (consistent with category color palette used throughout)

**Design principle applied:** Consistent category color coding — Furniture = amber, Office Supplies = teal, Technology = navy — is applied across all charts. Viewers do not need to re-read legends on every chart.

**Mistake avoided:** Did not use a pie chart (return rate is not a part-of-whole measure). Did not use a line chart (Category is not a time dimension).

---

## Dashboard-Level Design Principles Applied

| Principle | How Applied |
|---|---|
| Consistent color vocabulary | Same colors for Category and Measure type across all sheets |
| KPI cards at the top | 5 headline numbers immediately visible without scrolling |
| Filters applied globally | Region, Category, Segment, Date, Ship Mode filters affect all sheets |
| Action filters | Clicking a region bar highlights related data across connected sheets |
| Minimal clutter | Gridlines are light dashed, axis lines removed, no decorative elements |
| Business-friendly titles | Every chart title is a plain-English question, not a technical description |
| Sorted bars | All bar charts sorted by value to enable immediate rank comparison |
