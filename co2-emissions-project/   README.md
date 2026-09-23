# Renewable Energy & CO2 Emissions in Latin America

**Does renewable energy adoption predict lower CO2 emissions across Latin American and Caribbean countries — once you control for economic development and country-specific differences?**

## Key Finding

A simple cross-country comparison shows a strong negative relationship between renewable energy share and CO2 emissions per capita. But once the analysis controls for each country's fixed characteristics and shared regional trends over time (a two-way fixed-effects model), that relationship weakens by roughly **75%** and loses statistical significance. The takeaway: the naive result was driven mostly by *which* countries have high renewable shares (e.g., fossil-fuel exporters vs. hydro-rich economies), not by emissions falling *as* a given country's renewable share rises over time.

## Data & Method

- **Source:** World Bank World Development Indicators, pulled via the `wbgapi` Python package
- **Sample:** 26 Latin American & Caribbean countries, 2000–2022 (~576 country-year observations)
- **Variables:** CO2 emissions per capita, renewable energy share (% of final energy consumption), GDP per capita
- **Method:** Pooled OLS regression, then a two-way fixed-effects panel regression (country + year effects), using `statsmodels` and `linearmodels`

| Model | Coefficient on renewable share | p-value |
|---|---|---|
| Pooled OLS | −0.078 | < 0.001 |
| Fixed Effects (country + year) | −0.019 | 0.093 (not significant at 5%) |

## Files

- [`latam_energy_co2_analysis.ipynb`](./latam_energy_co2_analysis.ipynb) — full analysis notebook: data pull, cleaning, exploratory plots, both regression models
- [`policy_brief.md`](./policy_brief.md) — full written brief with findings, caveats, and policy implications

## Caveats

This is an observational analysis, not a causal one. Countries that expand renewables may differ in unobserved ways (political stability, hydropower geography, industrial structure) that also affect emissions. See the full brief for a more complete discussion.
