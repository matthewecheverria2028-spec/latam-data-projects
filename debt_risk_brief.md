# Sovereign External Debt Risk in Latin America and the Caribbean

**A data-driven risk screening brief | 17 LAC economies, 2010–2022**

---

## Executive Summary

Using World Bank International Debt Statistics data for 17 Latin American and Caribbean (LAC) economies, this analysis builds a SQL-queryable panel database and an interactive dashboard to screen for external debt risk. Three risk dimensions are examined: overall debt burden, short-term refinancing exposure, and debt service strain relative to exports. The analysis finds that risk is not concentrated in a single country or driven by a single factor — Argentina shows the highest refinancing risk (short-term debt exposure), while Colombia and El Salvador show the highest ongoing debt service strain, and Suriname and Nicaragua carry the largest overall debt burdens relative to their economies. Critically, a simple region-wide relationship between debt burden and economic growth does not hold: several of the most interesting data points are explained by country-specific events (a commodity-driven growth boom in one case, a sovereign default in another) rather than a general regional pattern.

## Background

External debt sustainability is a central concern in development finance: a country with heavy short-term debt or a fast-rising debt service burden faces genuine risk if global financial conditions tighten or its own export revenues fall. Unlike a single-indicator "debt-to-GDP" headline, real risk screening requires looking at multiple indicators together, since a country can look fine on one measure and risky on another.

## Data and Method

Data was pulled from the World Bank's International Debt Statistics and World Development Indicators databases via the `wbgapi` Python package, covering 17 LAC economies from 2010–2022 (four high-income LAC economies — Chile, Costa Rica, Panama, and Uruguay — are not covered by this dataset, as the World Bank does not track detailed external debt statistics for economies it classifies as having full market access).

The panel was loaded into a SQL database, and four analytical queries were run:
1. **Current debt burden ranking** — which countries carry the highest external debt relative to Gross National Income (GNI) in the most recent year.
2. **Fastest-rising debt service burden** — using a SQL window function to compute year-over-year change in debt service as a share of exports.
3. **Refinancing risk classification** — flagging countries by their short-term debt share of total external debt (a standard early-warning indicator: high short-term debt means more of a country's debt must be refinanced imminently, which is dangerous if credit markets tighten).
4. **Debt vs. growth relationship** — a country-level comparison of average debt burden against average GDP growth over the full period.

Results were exported to a clean dataset and visualized in an interactive Power BI dashboard.

## Findings

**Debt burden is highest in Suriname and Nicaragua.** As of 2022, Suriname's external debt stood at roughly 120% of GNI and Nicaragua's at roughly 105% — both far above the regional norm of 30–60%. Suriname's position reflects its 2020–2021 sovereign debt default and subsequent restructuring, a real and well-documented crisis rather than a data anomaly.

**Argentina stands alone on refinancing risk.** Argentina's short-term debt share (~20% of total external debt) is roughly 40% higher than the next-highest country (Jamaica, ~14%), and it is the only country in the sample flagged as "Elevated risk" on this measure. This is a distinct risk dimension from overall debt burden — Argentina's total debt-to-GNI ratio (40%) is actually mid-range for the region, but the *composition* of that debt (heavily short-term) is what creates acute rollover risk.

**Debt service strain is concentrated in Colombia, El Salvador, Brazil, and Argentina.** These four countries devote the largest share of their export earnings to servicing external debt (30–34%), a meaningfully different risk signal than either of the above two measures.

**No simple region-wide relationship between debt and growth.** A scatter of average debt burden against average GDP growth shows no clear regional trend. The most striking data point — Guyana, with average annual growth near 13%, an outlier by a wide margin — is explained entirely by Guyana's 2020-onward offshore oil production boom, not by any general debt-related mechanism. This is a useful reminder that cross-country macro correlations are often driven by a small number of idiosyncratic national stories rather than a generalizable pattern.

## Caveats

This is a public-data risk *screen*, not a full sovereign credit analysis. A complete debt sustainability assessment would additionally weigh currency composition of debt (foreign- vs. local-currency denominated), maturity profiles beyond the short-term/long-term split used here, market access and borrowing costs, and political/institutional factors. The World Bank's IDS data also excludes several LAC economies classified as high-income, so this screen is not comprehensive of the full region. Finally, debt service and short-term debt figures can be volatile year to year for smaller economies with thin external financing markets, so single-year snapshots should be read alongside the multi-year trend, not in isolation.

## Conclusion

Risk in LAC's external debt landscape is multidimensional: the country with the highest total debt burden (Suriname) is not the same country with the highest refinancing risk (Argentina) or the highest debt service strain (Colombia). A one-number debt ranking would miss all of this nuance. This kind of multi-indicator screening — built on a real SQL pipeline and delivered as an interactive dashboard — is the type of first-pass risk triage that supports more detailed country-level analysis in a development finance or capital markets context.

---

*Data source: World Bank International Debt Statistics and World Development Indicators, accessed via the `wbgapi` Python package. Full SQL queries and dashboard available in the accompanying notebook and Power BI report.*
