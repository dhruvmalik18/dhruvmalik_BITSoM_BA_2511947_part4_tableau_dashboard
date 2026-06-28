# Business Insights
**Analyst:** Dhruv Malik | **Student ID:** BITSoM_BA_2511947

---

## Calculated Fields Created

| Field | Formula | Purpose |
|---|---|---|
| Profit Margin | SUM([profit]) / SUM([sales]) | Overall profitability rate |
| Cost | [sales] - [profit] | Derived cost of goods |
| Average Order Value | SUM([sales]) / COUNTD([order_id]) | Revenue per unique order |
| Return Rate | SUM([return_flag]) / COUNTD([order_id]) | % of orders returned |
| Shipping Delay Bucket | IF delivery_days <= 1 → Fast; <= 3 → Standard; <= 5 → Slow; else Very Slow | Delivery speed categorization |
| Discount Tier | IF discount = 0 → None; <= 10% → Low; <= 20% → Medium; <= 30% → High; else Very High | Discount impact grouping |
| Is Returned | IF return_flag = 1 → "Returned" ELSE "Not Returned" | Human-readable return label |
| Profit Per Order | SUM([profit]) / COUNTD([order_id]) | Profit efficiency per order |

---

## Insight 1 — Sales Trend: Revenue Grew 12% in 2025 vs 2024

**Observation:** Monthly sales in 2025 consistently outperform the same months in 2024 across nearly all months.

**Data Evidence:** 2024 total sales ≈ $104M; 2025 total ≈ $113M. Several months in 2025 exceeded $11M, while 2024 peaks were near $10.5M.

**Interpretation:** The business is growing year-over-year. The new campaign and product investments are likely driving incremental revenue.

**Recommended Action:** Identify which months underperformed (e.g., mid-year dips) and investigate whether they correlate with campaign pauses or inventory issues.

---

## Insight 2 — Regional Performance: South Region Leads in Sales

**Observation:** The South region generated the highest total sales ($64.7M) and profit ($9.99M) among all four regions.

**Data Evidence:** North = $54.6M sales, East = $48.9M, West = $48.9M. South leads by ~$10M over its nearest competitor.

**Interpretation:** South is the strongest revenue driver. It may also have favorable customer demographics or stronger distribution.

**Recommended Action:** Investigate what makes South outperform — is it product mix, channel, or team execution? Replicate those factors in the East and West regions.

---

## Insight 3 — Category Profitability: Technology Dominates Profit

**Observation:** Technology category generates $28M of the company's $33.3M total profit — a staggering 84% share.

**Data Evidence:** Furniture contributed $3.6M profit; Office Supplies contributed $1.7M.

**Interpretation:** Technology is the engine of profitability. Furniture and Office Supplies have relatively thin margins.

**Recommended Action:** Consider increasing Technology inventory and marketing spend. Evaluate whether Furniture margins can be improved via pricing or supplier renegotiation.

---

## Insight 4 — Sub-Category: Copiers, Phones, Accessories Drive Most Value

**Observation:** Among sub-categories, Copiers ($7.3M), Phones ($7.1M), and Accessories ($7.2M) lead profit generation. Office supply sub-categories (Paper, Binders, Art) each contribute less than $400K.

**Data Evidence:** Bottom 5 sub-categories each produce under $370K in profit; top 3 produce over $7M each.

**Interpretation:** A small number of high-value SKUs are carrying the business. The tail of low-profit sub-categories may not justify shelf/catalog space.

**Recommended Action:** Conduct a portfolio rationalization exercise for sub-categories below $500K profit. Double down on Copiers and Phones with targeted promotions.

---

## Insight 5 — Discount Impact: Higher Discounts Correlate With Lower Profit

**Observation:** Orders with 30%+ discounts frequently result in negative or near-zero profit.

**Data Evidence:** Pearson correlation between discount and profit = -0.27. Orders in the "30%+" discount tier show average negative profit contribution per order.

**Interpretation:** Heavy discounting is eroding margin without proportionally increasing volume or customer value.

**Recommended Action:** Set a discount approval threshold at 20%. Any discount beyond that should require manager authorization and a minimum order value to justify margin dilution.

---

## Insight 6 — Shipping Performance: Standard Class Causes Significant Delays

**Observation:** Standard Class shipping averages 4.7 delivery days, versus Same Day at 0.4 days and First Class at 1.8 days.

**Data Evidence:** ~60%+ of orders use Standard Class. Avg delivery days: Same Day=0.4, First Class=1.8, Second Class=2.7, Standard Class=4.7.

**Interpretation:** Most customers are experiencing the slowest shipping tier. This likely impacts customer satisfaction and repeat purchase rates.

**Recommended Action:** Consider incentivizing upgrades to First Class for orders above a certain value threshold, or offering Standard Class customers proactive shipping updates to reduce dissatisfaction.

---

## Insight 7 — Return Patterns: Return Rate Is Low but Concentrated

**Observation:** Overall return rate is 4.5% (191 of 4,200 orders). Furniture shows the highest concentration of returns among categories.

**Data Evidence:** 191 total returns; Furniture's higher-value items (Tables, Bookcases) dominate return SKUs.

**Interpretation:** While the absolute return rate is manageable, Furniture returns are likely more costly due to higher unit values and shipping costs.

**Recommended Action:** Improve product descriptions and customer expectations for Furniture (dimensions, materials). Consider a "no free return" policy for Furniture above a size threshold to reduce abuse.

---

## Insight 8 — Business Risk: Home Office Segment Has Highest Sales But Needs Retention Focus

**Observation:** Home Office generates the highest segment sales ($74.5M) and profit ($11.6M), but this segment is the most sensitive to economic disruptions (remote work trends).

**Data Evidence:** Home Office leads Consumer ($71.9M) and Corporate ($70.6M) by a meaningful margin.

**Interpretation:** Over-concentration in the Home Office segment creates risk if remote work adoption declines or competition increases in that segment.

**Recommended Action:** Build a segment-specific loyalty program for Home Office customers. Simultaneously grow Corporate segment through B2B outreach, which tends to have higher CLV and lower churn risk.
