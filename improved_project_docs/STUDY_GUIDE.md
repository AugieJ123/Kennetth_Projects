# Study Guide: Preparing for a PhD Supervisor Meeting

This guide lists the key concepts Kenneth must be able to explain confidently and in his own words before presenting this project to a PhD supervisor. Each topic includes the core question a supervisor is likely to ask and suggested study resources.

---

## Priority 1: MUST Know (Supervisor will definitely ask)

### Why Sierra Leone? Why Mini-Grids?
- **Likely question:** "What makes Sierra Leone different from other Sub-Saharan African countries for this research?"
- **What to know:**
  - Sierra Leone's electrification rate (~29% national, <5% rural)
  - The "data uncertainty trap" — why lack of ground measurements raises financing costs
  - Why mini-grids (vs. grid extension) are the appropriate solution for rural Sierra Leone
  - The Multi-Tier Framework for energy access (what is Tier 2?)
- **Study:** Read Sankoh et al. (2022) and Kamara & Kanu (2025) in full

### What is Uncertainty Quantification?
- **Likely question:** "What do you mean by 'uncertainty' in this context? What types of uncertainty are you dealing with?"
- **What to know:**
  - Aleatory uncertainty (inherent randomness — weather variability) vs. epistemic uncertainty (lack of knowledge — measurement bias)
  - Why the distinction matters: aleatory uncertainty cannot be reduced, epistemic can
  - The five components of the solar uncertainty budget and which category each falls into
- **Study:** Any introductory UQ textbook, or Smith (2013) "Uncertainty Quantification" Ch. 1–2

### What is P50/P75/P90?
- **Likely question:** "Explain P90 to me. Why do lenders care about it?"
- **What to know:**
  - P90 means "there is a 90% probability that the actual yield will exceed this value"
  - Debt lenders use P90 because they need high confidence the project will generate enough revenue to service debt
  - The P90/P50 ratio quantifies how much "haircut" uncertainty imposes on project economics
  - In Sierra Leone, the P90/P50 ratio is ~0.87 — meaning ~13% revenue reduction from uncertainty
- **Study:** Any renewable energy project finance guide (e.g., IRENA guidelines)

### What is Monte Carlo Simulation?
- **Likely question:** "Why 10,000 samples? How do you know that's enough?"
- **What to know:**
  - Monte Carlo propagates uncertainty by sampling input distributions many times
  - The law of large numbers — more samples = better approximation of the true distribution
  - Convergence: you check by running with increasing N and seeing when results stabilise
  - 10,000 is a common choice for energy yield assessment (industry standard)
  - The standard error of the mean decreases as 1/√N
- **Study:** Any introductory statistics textbook on Monte Carlo methods

---

## Priority 2: SHOULD Know (Supervisor will likely probe)

### Weibull Distribution for Wind
- **Likely question:** "Why Weibull and not something else? What do k and c mean physically?"
- **What to know:**
  - k (shape): controls the width/shape. k=1 is exponential, k≈2 is Rayleigh (typical for wind), k≈3.5 is nearly Gaussian
  - c (scale): related to mean wind speed. Higher c = windier site
  - Weibull is used because it has a theoretical basis in extreme value theory and fits wind speed data well empirically
  - When it fails: bimodal distributions (monsoon/trade wind), very calm sites, complex terrain
  - Four estimation methods (MLE, MOM, EPF, Empirical) — know what MLE means at minimum
- **Study:** Parajuli (2016) — referenced in the notebook

### Beta Distribution for Solar
- **Likely question:** "Why Beta distribution for clearness index?"
- **What to know:**
  - Clearness index (Kt) is bounded between 0 and 1 — Beta is a natural choice for bounded distributions
  - α and β control the shape: α > β = right-skewed (more clear days), α < β = left-skewed (more cloudy)
  - The seasonal shift: dry season has α > β (more sunshine), wet season is more symmetric
- **Study:** Wikipedia article on Beta distribution + any solar resource assessment guide

### Bayesian Inference (Basic Level)
- **Likely question:** "What does the Bayesian approach add over MLE?"
- **What to know:**
  - Bayes' theorem: posterior ∝ likelihood × prior
  - Prior: what we believe before seeing data (from regional literature)
  - Likelihood: probability of observed data given parameters
  - Posterior: updated belief after seeing data
  - Why Bayesian is valuable for Sierra Leone: with limited data, priors from regional studies help regularise estimates
  - The key result: Bayesian credible intervals are ~15-20% wider than bootstrap CIs — this is MORE conservative and BETTER for risk assessment in data-sparse contexts
- **Study:** McElreath "Statistical Rethinking" Ch. 1–3, or any gentle Bayesian intro

### MCMC (Conceptual Level)
- **Likely question:** "How does Metropolis-Hastings work, roughly?"
- **What to know:**
  - We want to sample from the posterior, but can't compute it analytically
  - MH proposes a random jump, accepts or rejects based on whether the new point has higher posterior probability
  - "Burn-in" = discard early samples before the chain reaches the high-probability region
  - Convergence = the chain is exploring the posterior properly (trace plots should look like "hairy caterpillars")
  - DON'T need to know: detailed math, acceptance ratio derivation, or comparison with HMC/NUTS
- **Study:** YouTube "Metropolis-Hastings explained" (many good visual tutorials)

---

## Priority 3: GOOD to Know (Shows depth if asked)

### Copulas
- **Likely question:** "Why did you need copulas? What does the Gaussian copula assume?"
- **What to know:**
  - Copulas separate marginal distributions from dependence structure
  - Why needed: solar and wind are correlated (mild anti-correlation in Sierra Leone)
  - If you ignore the correlation and treat them as independent, you overestimate worst-case scenarios
  - Gaussian copula assumes the dependence can be described by a multivariate normal distribution on the probability-transformed data
  - Limitation: Gaussian copula has symmetric tail dependence (may miss extreme co-occurrence events)
- **Study:** Wikipedia "Copula (probability theory)" introduction section

### Sobol Sensitivity Analysis
- **Likely question:** "What's the difference between S₁ and Sₜ?"
- **What to know:**
  - S₁ (first-order): variance in output caused by that input alone, ignoring interactions
  - Sₜ (total-effect): variance caused by that input including all interactions with other inputs
  - If Sₜ >> S₁, there are significant interaction effects
  - The key finding: GHI bias and wind speed bias dominate (each Sₜ > 0.4)
  - Policy meaning: fixing data quality is more impactful than improving models
- **Study:** Saltelli et al. (2010) — at least the introduction and examples

### Reserve Design
- **Likely question:** "How did you adapt the NY Power Grid methodology?"
- **What to know:**
  - The Walid et al. (2024) paper sizes reserves for a large grid with many generators
  - A Sierra Leone mini-grid is fundamentally different: no interconnection, limited storage, no inertia
  - The adaptation: separate reserves into "variability" (natural load/resource fluctuation) and "uncertainty" (data quality), then combine as root-sum-square
  - Limitation: this is a simplified adaptation — a proper mini-grid reserve framework would need to account for battery state-of-charge constraints
- **Study:** Read Walid et al. (2024) abstract and methodology section

---

## Interview Practice

Before the meeting, practice answering these questions out loud (not in writing):

1. "Walk me through your analysis in 3 minutes."
2. "What is the single most important finding?"
3. "If you could only improve one thing about this analysis, what would it be?"
4. "How did you choose your methodology?"
5. "What surprised you most in the results?"
6. "Where did you use AI tools, and where did you work independently?"
7. "What would you do differently in a PhD with 3-4 years of full-time research?"

> **Critical tip:** It's OK to say "I'm still learning about that" or "I'd need to study that more deeply in a PhD." It is NOT OK to pretend you understand something you don't. Supervisors can tell immediately.

---

## Recommended Reading Order

1. **Walid et al. (2024)** — Read the full paper. This is the methodological anchor.
2. **Sankoh et al. (2022)** — Understand the Sierra Leone energy context.
3. **Saltelli et al. (2010)** — At least the introduction to variance-based sensitivity.
4. **Pfenninger & Staffell (2016)** — Understand reanalysis bias issues.
5. **McElreath "Statistical Rethinking" Ch. 1–3** — For Bayesian foundations.
6. A good YouTube series on Monte Carlo methods and MCMC.
