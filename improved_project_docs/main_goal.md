# Research Motivation and PhD Alignment
**Kenneth Bamba — Sierra Leone Renewable Energy Uncertainty Analysis**

---

## Personal Motivation

I am originally from Sierra Leone, where we are richly endowed with solar and hydro resources, yet power supply remains unreliable and a large portion of the population still lacks access to electricity. With ongoing developments such as the Nant Power project and emerging renewable initiatives like the Bonthe wind project, the system is evolving into a mix of thermal and renewable generation. However, uncertainty in both generation and demand, along with limited and often poorly coordinated reserves, continues to affect system reliability.

This personal experience motivated me to explore how data-driven uncertainty modelling could improve power system planning in data-sparse environments like Sierra Leone.

---

## What I Did

To demonstrate my interest and explore the problem space, I developed a computational notebook that applies uncertainty quantification (UQ) methods to renewable energy resource assessment for Sierra Leone mini-grids.

The analysis covers:
- Multi-source data acquisition (NASA POWER, PVGIS-SARAH2, ERA5)
- Statistical characterisation of solar and wind resources
- Monte Carlo simulation of energy yield under uncertainty
- Bayesian parameter estimation for wind speed distributions
- Sensitivity analysis to identify dominant uncertainty drivers
- Reserve sizing adapted from published grid-scale methodologies

This work was developed as an exploratory study to understand the problem landscape and identify promising research directions. It is **not** a finished research contribution — it is a starting point.

---

## What I Learned

Key findings from this exploratory analysis:

1. **Data quality dominates uncertainty** — Reanalysis model bias and satellite retrieval error, not natural climate variability, are the largest contributors to the uncertainty budget for Sierra Leone renewable energy projects.

2. **The "uncertainty premium" is significant** — Extra capacity needed to maintain reliability under data uncertainty adds approximately 8–12% to the levelised cost of electricity compared to a deterministic design.

3. **Meteorological investment has high returns** — Investing in ground-truth measurement stations could significantly reduce project financing costs across Sierra Leone's planned mini-grid portfolio.

4. **Solar-wind complementarity exists** — Solar and wind resources show mild anti-correlation in Sierra Leone, providing a small but real diversification benefit for hybrid systems.

---

## Honest Limitations

This exploratory study has significant limitations that I am aware of:

- The analysis relies entirely on reanalysis/satellite data with no ground-truth validation from Sierra Leone weather stations.
- The mini-grid model is simplified and does not capture detailed electrical dynamics, battery degradation, or diesel backup operation.
- Load profiles are synthetic, not based on measured community demand.
- I am still developing my understanding of several advanced methods used in this analysis (Bayesian MCMC, copulas, Sobol sensitivity).
- AI tools were used to assist with code development and documentation (see [ACKNOWLEDGMENTS.md](ACKNOWLEDGMENTS.md) for details).

These limitations represent exactly the kind of gaps that PhD-level research would address rigorously.

---

## PhD Alignment

I am planning to pursue a PhD focused on developing models for uncertainty quantification and optimisation in emerging power systems. Specific research questions I would like to explore include:

1. How can we systematically quantify and reduce the "data uncertainty trap" that raises financing costs for renewable energy in Sub-Saharan Africa?

2. What is the optimal investment in meteorological infrastructure to minimise aggregate project risk across a national mini-grid portfolio?

3. How should reserve design methodologies developed for large interconnected grids (like the NY Power Grid) be adapted for isolated mini-grids in data-sparse environments?

I would appreciate the opportunity to discuss potential research alignment and explore how my background and motivation could contribute to your research group.

---

## Contact

**Kenneth Bamba**  
Email: *[to be added]*
