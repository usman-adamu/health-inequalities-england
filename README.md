# Health Inequalities in England: An Epidemiological Analysis

**Author:** Usman Adamu  
**Date:** April 2026  
**Tools:** R, R Markdown, fingertipsR, tidyverse, ggplot2, tmap, sf  
**Data source:** OHID Fingertips platform (NHS Digital)

---

## Overview

This project presents a reproducible epidemiological analysis of health inequalities in England, focusing on life expectancy trends, deprivation gradients, and the relationship between total and healthy life expectancy across local authorities. All data were obtained from the Office for Health Inequalities and Disparities (OHID) Fingertips platform via the `fingertipsR` package, covering approximately two decades of data (2001–2022).

The analysis is written in R Markdown and is fully reproducible from source.

---

## Research Questions

1. How have life expectancy trends changed across English local authorities over two decades?
2. What is the relationship between neighbourhood deprivation and life expectancy?
3. Does the relationship between deprivation and life expectancy differ by sex?
4. What is the gap between total life expectancy and healthy life expectancy across deprivation levels — and does deprivation compress or expand years lived in good health?

---

## Data

All indicators were extracted at **Counties and Unitary Authorities level (AreaTypeID 502)** from the OHID Fingertips platform using `fingertipsR` v1.1.0.

| Indicator | Fingertips ID |
|---|---|
| Life expectancy at birth | 90362 |
| Healthy life expectancy at birth | 90360 |
| IMD 2019 deprivation score | 93553 |

Data accessed: April 2026.

---

## Key Findings

**1. Persistent and widening life expectancy inequalities**  
Life expectancy increased across England over the study period, but geographic inequalities between local authorities persisted. A 6.7-year gap was identified between the most and least deprived local authorities — consistent with longstanding evidence on health inequalities in England.

**2. Deprivation as a strong predictor of life expectancy**  
Linear regression identified a statistically significant negative association between deprivation score and life expectancy (R² = 0.667, p < 0.001) — meaning deprivation alone explained **66.7% of the geographic variance** in life expectancy across English local authorities. This is substantially stronger than the deprivation-depression relationship, reflecting the direct and well-established pathway from material disadvantage to mortality risk.

**3. Sex-stratified differences in the deprivation gradient**  
The relationship between deprivation and life expectancy was significant for both sexes, but the gradient differed in magnitude. Separate regression models for males and females confirmed that the deprivation penalty on life expectancy was not uniform across sex, with males in the most deprived areas facing a steeper absolute disadvantage.

**4. The healthy life expectancy paradox**  
Analysis of the gap between total and healthy life expectancy revealed that more deprived areas face a compounded disadvantage: not only do residents live shorter lives, but a greater proportion of those shorter lives is spent in poor health. This healthy life expectancy paradox — whereby deprivation simultaneously reduces life expectancy and compresses years of good health — was confirmed and quantified across deprivation quintiles.

---

## Methodology

- **Trend analysis:** Life expectancy trends plotted across the study period at local authority level
- **Deprivation regression:** Scatter plots with linear regression fits; Pearson correlation and R² reported
- **Sex-stratified regression:** Separate regression models for male and female life expectancy against deprivation, with comparison of gradients
- **Quintile analysis:** Life expectancy and healthy life expectancy compared across IMD deprivation quintiles, with error bars representing standard error
- **Healthy life expectancy gap analysis:** The absolute gap between total LE and healthy LE calculated and plotted across quintiles to quantify the paradox
- **All citations:** Vancouver style, drawing on peer-reviewed UK public health and health inequalities literature

---

## Limitations

- This is an **ecological analysis**. Associations between area-level deprivation and life expectancy cannot be used to infer individual-level causal relationships (ecological fallacy).
- Life expectancy data are subject to **small-area instability** in local authorities with small populations (e.g. Isles of Scilly, City of London), which may produce extreme values.
- The IMD 2019 deprivation score is a **cross-sectional measure** applied to a longitudinal outcome, which limits causal interpretation of trend data.
- **Healthy life expectancy** is based on self-reported health status, which may be subject to reporting bias and may vary systematically by deprivation level independently of objective health status.

---

## Repository Structure

```
health-inequalities-england/
├── health_inequalities.Rmd     # Full R Markdown source (reproducible)
├── health_inequalities.html    # Rendered HTML report
└── README.md
```

---

## How to Reproduce

1. Clone this repository
2. Open `health_inequalities.Rmd` in RStudio
3. Install required packages if not already installed:

```r
install.packages(c("fingertipsR", "tidyverse", "tmap", "sf",
                   "rnaturalearth", "rnaturalearthdata"))
```

4. Click **Knit** — data are fetched live from the OHID Fingertips API

> **Note:** Live API calls mean rendering requires an internet connection. Data values may differ slightly if accessed after April 2026 as Fingertips is updated regularly.

---

## References

Key references cited in the analysis include:

- Marmot M et al. *Health Equity in England: The Marmot Review 10 Years On.* London: IHE; 2020.
- Institute of Health Equity. *England's widening health gap: local places falling behind.* London: IHE; 2024.
- IFS Deaton Review. Health inequalities. Oxford Open Econ. 2024;3(Suppl 1):i499–i528.
- Health Foundation. *Quantifying health inequalities in England.* London: The Health Foundation; 2022.

Full reference list available in the rendered report.

---

*This project is part of a public health data analytics portfolio developed using real NHS data. All analysis is conducted for educational and professional development purposes.*
