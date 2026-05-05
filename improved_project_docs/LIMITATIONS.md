# Limitations of This Analysis

This document provides an honest assessment of the limitations of this exploratory study. Understanding these limitations is essential for interpreting the results correctly and for identifying research directions that a PhD could address.

---

## 1. Data Limitations

### No Ground-Truth Validation
The entire analysis relies on reanalysis (NASA POWER/MERRA-2) and satellite-derived (PVGIS-SARAH2) datasets. **No ground-truth measurements from Sierra Leone weather stations were used.** This means:
- The absolute accuracy of GHI and wind speed values cannot be verified
- Systematic biases in reanalysis products may not be captured by the uncertainty budget
- The "reanalysis model bias" uncertainty component (8%) is based on literature values from other tropical regions, not Sierra Leone-specific validation

**What a PhD would do differently:** Deploy temporary measurement campaigns or partner with Sierra Leone's meteorological department to obtain at least 1–2 years of ground-truth data for cross-validation.

### Synthetic Load Profiles
The community electricity demand profile is entirely synthetic, based on published surveys and literature values for rural West Africa. **No measured load data from Sierra Leone communities was used.** The bimodal daily pattern and seasonal modulation are assumptions, not observations.

**What a PhD would do differently:** Conduct field surveys or use smart meter data from existing Sierra Leone mini-grids to calibrate demand models.

### Temporal Resolution
Most of the analysis uses daily-average data. Sub-daily variability (hourly cloud transients, wind gusts) is not captured, which underestimates short-term supply-demand mismatch and battery cycling requirements.

**What a PhD would do differently:** Use hourly or sub-hourly reanalysis data and simulate battery dispatch at matching resolution.

---

## 2. Methodological Limitations

### Simplified Energy Yield Model
The PV and wind yield calculations use simplified capacity factor models, not full physical simulation chains. Specifically:
- PV yield uses a linear GHI-to-power conversion with a fixed performance ratio, ignoring temperature derating, inverter efficiency curves, soiling, and shading
- Wind yield uses a generic IEC Class III normalised power curve, not a manufacturer-specific turbine model
- No wake losses, transformer losses, or transmission losses are modelled

**What a PhD would do differently:** Use pvlib's full transposition/temperature/inverter model chain for PV, and a specific turbine power curve with wake loss modelling for wind.

### Two-Parameter Weibull Assumption
The wind speed distribution is modelled as a standard two-parameter Weibull. While Q-Q diagnostics support this choice for Freetown, some West African sites exhibit bimodal wind speed distributions (monsoon/trade wind regimes) that require mixture Weibull or other more flexible models.

**What a PhD would do differently:** Test mixture distributions systematically across all sites and seasons, using formal model selection criteria (BIC, cross-validation).

### Bivariate Copula Only
The solar-wind dependence is modelled with a single bivariate copula (Gaussian). This does not capture:
- Conditional dependence on season or weather regime
- Higher-dimensional dependencies (e.g., temperature effects on both PV output and demand)
- Tail dependence (extreme events where both resources fail simultaneously)

**What a PhD would do differently:** Explore vine copulas, regime-switching models, or weather-type classification to capture conditional dependence structures.

### MCMC Chain Length and Convergence
The Metropolis-Hastings sampler uses relatively short chains and basic convergence diagnostics. More rigorous Bayesian practice would include:
- Formal convergence tests (Gelman-Rubin R-hat across multiple chains)
- Effective sample size calculation
- Sensitivity analysis on prior specification
- Comparison with alternative samplers (NUTS/HMC via Stan or PyMC)

**What a PhD would do differently:** Use a mature probabilistic programming framework (PyMC, Stan) with built-in convergence diagnostics and run multiple independent chains.

### Sobol Sample Size
The Sobol sensitivity analysis uses 512 base samples. While standard, this may be insufficient for reliable estimation of higher-order interaction effects (S_T - S_1). Confidence intervals on some Sobol indices are wide, indicating limited statistical precision.

**What a PhD would do differently:** Use convergence testing on Sobol indices (increasing sample size until indices stabilise) and report effective sample sizes.

---

## 3. Reserve Design Limitations

### Adaptation from Grid-Scale to Mini-Grid
The reserve design methodology is adapted from Walid *et al.* (2024), which was developed for the New York Power Grid — a large, interconnected system with multiple generators, demand response, and interconnection capacity. Applying this framework to an isolated 500-household mini-grid requires several simplifying assumptions:
- No interconnection or demand response capability
- No inertial response from synchronous generators
- Battery storage modelled as perfect (no degradation, round-trip losses simplified)
- No diesel backup generator modelled

**What a PhD would do differently:** Develop a mini-grid-specific reserve framework that accounts for storage limitations, diesel backup, and the fundamentally different risk profile of isolated systems.

### Single-Year Simulation
The reserve and sizing analysis uses a single representative year, not a multi-year sequential simulation. This means:
- Inter-annual resource variability is not fully captured in the operational simulation
- Multi-year dry/low-wind sequences are not tested
- Battery state-of-health degradation over the project lifetime is not modelled

**What a PhD would do differently:** Run multi-year sequential Monte Carlo simulations with battery degradation models.

---

## 4. Scope Limitations

### Breadth vs. Depth
This notebook covers 15 analysis sections and 7 methodological contributions. While this demonstrates the breadth of the problem space, each section necessarily receives less depth than a focused study would provide. A PhD thesis would select 2–3 of these topics and investigate them in much greater detail.

### No Techno-Economic Validation
The LCOE estimates are simplified and do not account for:
- Real equipment costs for the Sierra Leone market
- Import duties, logistics, and installation costs
- Operation and maintenance cost escalation
- Financing structures (debt/equity mix, interest rates)
- Currency risk and inflation

**What a PhD would do differently:** Partner with mini-grid developers to obtain real project cost data and validate economic models against actual project outcomes.

---

## 5. Reproducibility Notes

- The notebook includes a synthetic data fallback when APIs are unavailable. Results generated with synthetic data are illustrative but do not represent real Sierra Leone conditions.
- A fixed random seed (42) ensures reproducibility of stochastic simulations within a single execution environment.
- Results may vary slightly across different Python/numpy/scipy versions due to floating-point implementation differences.

---

## Summary

These limitations do not invalidate the analysis — they define its scope. The core finding (that data quality, not climate variability, dominates uncertainty in Sierra Leone renewable energy projects) is robust to most of these limitations. However, translating this exploratory work into actionable investment decisions would require addressing each of the above points through rigorous PhD-level research.
