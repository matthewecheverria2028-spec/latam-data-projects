# Renewable Energy and Carbon Emissions in Latin America and the Caribbean: A Cautionary Finding

**A data-driven policy brief | Analysis of 26 LAC economies, 2000–2022**

---

## Executive Summary

Using World Bank panel data covering 26 Latin American and Caribbean (LAC) economies from 2000 to 2022, this analysis examines whether higher renewable energy adoption is associated with lower CO2 emissions per capita. A simple cross-country comparison suggests a strong negative relationship. However, once the analysis controls for each country's structural characteristics and shared regional trends over time, that relationship weakens substantially and is no longer statistically reliable. The headline finding is not "renewables don't matter" — it is that **cross-country comparisons of renewable energy and emissions can be misleading**, and policymakers should be cautious about assuming that expanding a given country's renewable share will, on its own and in the near term, produce a measurable drop in that country's per-capita emissions.

## Background

LAC has one of the cleanest electricity grids in the world on average, driven largely by hydropower. Emissions still vary enormously across the region, however — from fossil-fuel-exporting economies with very high per-capita emissions to smaller, hydro-rich economies with very low emissions. Understanding whether renewable energy expansion is actually associated with falling emissions, independent of a country's income level, is directly relevant to how development institutions like the IDB prioritize energy and infrastructure investment.

## Data and Method

The analysis draws on four World Bank World Development Indicators for 26 LAC countries, 2000–2022 (576 country-year observations after cleaning):

- **CO2 emissions per capita** (outcome variable)
- **Renewable energy as a share of final energy consumption** (variable of interest)
- **GDP per capita, log-transformed** (control for economic development)

Two models were estimated:

1. **Pooled OLS** — treats all country-years as independent observations, ignoring the panel structure.
2. **Two-way fixed-effects regression** (country and year fixed effects) — isolates the relationship *within* each country over time, after removing each country's fixed baseline level and any region-wide year-to-year shocks (e.g., a global recession).

## Results

| Model | Coefficient on renewable share | p-value | Interpretation |
|---|---|---|---|
| Pooled OLS | −0.078 | < 0.001 | Strong, significant negative relationship |
| Fixed Effects (country + year) | −0.019 | 0.093 | Weak, not significant at 5% level |

The coefficient shrank by roughly 75% and lost statistical significance once country and year fixed effects were introduced. GDP per capita, by contrast, remained strongly significant in both models.

## Interpretation

The pooled result is driven substantially by **which countries** have high renewable shares, not by emissions falling **as a given country's** renewable share rises over time. A handful of fossil-fuel-dependent economies with near-zero renewable shares and very high per-capita emissions (visible as clear outliers in the underlying data) are doing much of the work in the simple cross-country comparison. Once fixed effects strip out fixed, country-specific characteristics, the within-country relationship between renewable adoption and emissions is much weaker and cannot be distinguished from noise with confidence.

This is a common pattern in cross-country panel analysis: a compelling-looking scatter plot across countries often reflects structural differences between those countries rather than a policy-relevant effect that would materialize if any single country changed its own energy mix.

## Caveats

This analysis is observational, not causal. Countries that expand renewable energy may differ in unobserved ways — political stability, natural endowments (e.g., hydropower geography), or existing industrial structure — that also affect emissions independent of the energy transition itself. In addition, the low Durbin-Watson statistic in the pooled model indicates meaningful autocorrelation in the residuals, suggesting standard errors in a more rigorous version of this analysis should be clustered by country. A stronger causal design would require either an instrumental variable or a natural experiment — for instance, comparing emissions trends before and after a specific national renewable energy subsidy or mandate.

## Policy Implications

Policymakers and development institutions should be cautious about assuming that increasing a country's renewable energy share will mechanically and immediately reduce that country's emissions trajectory. This does not mean renewable energy investment lacks value — there are strong independent cases for it on energy security, cost, and long-run decarbonization grounds. But this analysis suggests that **cross-country benchmarking alone is insufficient evidence** for that specific causal claim, and that emissions outcomes are more strongly tied to a country's overall level of economic development than to its renewable energy share, at least within this sample and time period. Future evaluation of renewable energy policy should prioritize within-country, before/after designs over cross-country comparisons.

---

*Data source: World Bank World Development Indicators, accessed via the `wbgapi` Python package. Full analysis code and regression output available in the accompanying notebook.*
