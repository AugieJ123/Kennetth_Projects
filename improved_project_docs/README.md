# Renewable Energy Resource Assessment Under Uncertainty
## A Sierra Leone Mini-Grid Case Study

**Author:** Kenneth Bamba  
**Year:** 2026  
**Status:** Exploratory study / PhD preparation

---

## Overview

This project explores uncertainty quantification (UQ) methods for renewable energy resource assessment in Sierra Leone — one of the world's least electrified countries (~29% national access, <5% rural).

The core question: **How much extra capacity and cost does data uncertainty impose on mini-grid design in data-sparse environments?**

The analysis is implemented as a Jupyter notebook (`SL_UQ_Analysis_V2_RealData.ipynb`) that walks through the full UQ pipeline, from raw data acquisition to policy-relevant sizing recommendations.

---

## Motivation

Sierra Leone faces a "data uncertainty trap": long-term project financing requires P90 yield guarantees based on ≥20 years of ground measurement data, but the country has fewer than 5 operational pyranometer stations. Without rigorous uncertainty quantification, projects are either over-built (raising costs) or under-built (causing chronic supply failures).

This project was developed to explore the problem space and identify promising research directions for a potential PhD.

---

## What the Notebook Covers

| Section | Topic | Method |
|---------|-------|--------|
| 1–2 | Setup & context | Configuration, Sierra Leone energy landscape |
| 3 | Data acquisition | NASA POWER API, PVGIS-SARAH2, multi-source fusion |
| 4 | Exploratory analysis | Time series, seasonal patterns, correlations |
| 5 | Solar UQ | Beta distribution fitting, uncertainty budget decomposition |
| 6 | Wind UQ | Weibull fitting (4 methods compared), wind rose, capacity factor |
| 7 | Joint uncertainty | Copula-based solar-wind dependence modelling |
| 8 | Monte Carlo simulation | 10,000-sample energy yield propagation |
| 9 | Bayesian UQ | Metropolis-Hastings MCMC for Weibull parameters |
| 10 | Reserve design | Adapted from NY Power Grid methodology (Walid et al., 2024) |
| 11 | Optimal sizing | Stochastic mini-grid sizing with LOLP constraint |
| 12 | Sensitivity analysis | Sobol first-order and total-effect indices |
| 13 | Spatial analysis | Five representative districts compared |
| 14 | Policy implications | Uncertainty premium quantification |
| 15 | Conclusions | Summary and future work |

---

## Data Sources

All data is publicly available:

| Source | Type | Period | Access |
|--------|------|--------|--------|
| NASA POWER (MERRA-2) | Daily reanalysis | 2001–2022 | [power.larc.nasa.gov](https://power.larc.nasa.gov/) |
| PVGIS-SARAH2 | TMY satellite | 2005–2020 | [re.jrc.ec.europa.eu](https://re.jrc.ec.europa.eu/pvg_tools/) |
| ERA5 | Hourly reanalysis | Variable | [cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/) |

**Note:** The notebook includes a synthetic data fallback mode for offline execution when APIs are unavailable.

---

## Prerequisites

- Python 3.9+
- Jupyter Notebook or JupyterLab

Dependencies are managed via `requirements.txt`.

---

## How to Run

Please see the [HOW_TO_RUN.md](HOW_TO_RUN.md) file for a complete, step-by-step guide on setting up your environment, installing dependencies, and executing the `SL_UQ_Analysis_V2_RealData.ipynb` notebook.

---

## Key Results (Summary)

- **Solar resource:** ~1,900–2,000 kWh/m²/year GHI at Freetown, with ~13–15% combined uncertainty
- **Wind resource:** Weibull k ≈ 2.0–2.5, c ≈ 5–7 m/s at 50m; capacity factor ~18–25%
- **Uncertainty premium:** ~8–12% LCOE increase vs. deterministic design to maintain 1% LOLP
- **Dominant uncertainty sources:** GHI reanalysis bias and wind speed model bias (>60% of variance)
- **Policy implication:** National weather station network investment could generate 5–10× return through reduced project financing costs

---

## Study Locations

| Site | Province | Lat | Lon |
|------|----------|-----|-----|
| Freetown | Western Area | 8.47°N | 13.23°W |
| Bo | Southern | 7.96°N | 11.74°W |
| Kenema | Eastern | 7.87°N | 11.19°W |
| Makeni | Northern | 8.88°N | 12.04°W |
| Koidu | Eastern | 8.64°N | 10.97°W |

---

## Limitations

See [LIMITATIONS.md](LIMITATIONS.md) for a detailed discussion of the limitations of this analysis.

---

## Acknowledgments

See [ACKNOWLEDGMENTS.md](ACKNOWLEDGMENTS.md) for a full disclosure of tools and assistance used in developing this project.

---

## Key References

1. Walid, K.B. *et al.* (2024). Reserve Procurement in the New York Power Grid with Offshore Wind Farms. *IEEE*.
2. Sankoh *et al.* (2022). HOMER techno-economic study, Sierra Leone rural PV-diesel-battery. *Int. Trans. Electr. Energy Syst.*
3. Saltelli *et al.* (2010). Variance-based sensitivity indices. *Comput. Phys. Commun.*
4. Pfenninger & Staffell (2016). Reanalysis bias correction for solar/wind. *Energy*.

---

## License

This project is shared for academic evaluation purposes.
