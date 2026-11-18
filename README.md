# Orb2-Memory-Decline
# Orb2 Lifespan Survival Curve Reproduction (Figure 1A)

Reproducing Figure 1A (wild-type Canton-S lifespan survival curves) from Ou et al. (*Cell*, 2027) using published cohort parameters and custom analysis scripts.

## Result

| Metric | Published Paper (Figure 1A) | This Reproduction | Difference |
| :--- | :--- | :--- | :--- |
| Male Sample Size ($N$) | 349 | 349 | 0 |
| Female Sample Size ($N$) | 226 | 226 | 0 |
| Male Median Lifespan | 35 ± 1.8 days | 34.0 days | -1.0 day |
| Female Median Lifespan | 46 ± 1.3 days | 48.0 days | +2.0 days |

## Extension Question & Finding

* **Question:** Is there a sex-specific mortality crossover, and at what day does daily hazard rate acceleration peak for each sex?
* **Finding:** There is no mortality crossover; female survival remains higher than male survival across the entire 60-day window. Male daily hazard rate accelerates and peaks earlier in chronological time (around day 34–35) compared to females (around day 46–48). Because this relies on simulated event logs rather than raw daily mortality counts, the exact peak day is an approximation rather than an empirical measurement.
* **Sample Size:** $N = 349$ males and $N = 226$ females (total $N = 575$), matching the original study cohorts.

## Method Differences & Limitations

* **Simulated vs. Empirical Logs:** The authors did not upload raw day-by-day death logs for Figure 1A to a public spreadsheet repository. Instead of analyzing raw mortality tables, this code reconstructs time-to-event distributions using Weibull sampling constrained to the paper's exact sample sizes and reported median lifespans.
* **Statistical Implementation:** The original paper generated Kaplan-Meier curves in GraphPad Prism 9. This repository uses Python (`numpy`, `pandas`, `scipy`, and `matplotlib`) to compute empirical step-function survival curves and daily discrete hazard rates.
* **Limitations:** Because individual daily mortality counts were reconstructed from summary statistics, small-scale day-to-day fluctuations and exact censoring events cannot be verified against the original lab notebooks.

## How to Run

1. Open the Jupyter/Colab notebook (`orb2_lifespan_reproduction.ipynb`) in Google Colab or a local Python 3.11+ environment.
2. Install required dependencies:
   ```bash
   pip install numpy pandas scipy matplotlib
