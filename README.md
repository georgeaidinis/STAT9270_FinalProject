# Bayesian Analysis of NBA 2023–24 Player Performance

This repository contains the final project for STAT 9270 (Bayesian Modeling & Computation), Spring 2025. We perform two hierarchical Bayesian analyses on 314 NBA player‐seasons from 2023–24:

1. **Hierarchical Binomial–Logit Model**  
   Estimates true 3-point shooting skill by position, with position‐level intercepts and an age effect.

2. **Hierarchical Student-t Random‐Slope Model**  
   Assesses how age influences points-per-game (PPG), allowing each position its own intercept and slope, and using a heavy-tailed error model.

All code, data, figures, tables and the write‐up are fully reproducible.

---

## Repository structure

```bash
.
├── Aidinis_HW_4.pdf
├── Aidinis_HW_4.tex # LaTeX source for the 6‐page project report
├── code.ipynb
├── code.R # Main R analysis script (brms models, figures, tables)
├── code.txt
├── figs  # Diagnostic plots & histograms (PNG)
│   ├── 3p_hist.png
│   ├── age_slope_pos.png
│   ├── bb_trace_density.png
│   ├── ppc_bb.png
│   ├── ppc_ppg.png
│   ├── ppg_hist.png
│   ├── ppg_resid.png
│   ├── ppg_trace_density.png
│   └── shrinkage_3p.png
├── LICENCE
├── models # Saved brms model objects and loo results (RDS) 
│   ├── loo_bb.rds
│   └── loo_ppg.rds
├── nba24_totals_clean.csv  # Cleaned data (314 rows × 11 cols)
├── README.md
├── stat9270.homework4.pdf
└── tables # CSV summaries for inclusion in LaTeX 
    ├── bb_fixed_effects.csv
    ├── n_by_position.csv
    ├── pos_3p_summary.csv
    ├── pos_age_slope.csv
    ├── ppg_fixed_effects.csv
    └── session_info.txt
```

---

## Requirements

- **R** ≥ 4.2  
- **R packages**:  

    ```r
        install.packages(c(
            "tidyverse","brms","posterior","bayesplot","loo","janitor","patchwork"
        ), repos="https://cloud.r-project.org")
    ```

- Python 3 (optional, for initial scraping/cleaning):

    ```python
        pip install pandas lxml requests
    ```

## Key results

- 3-Point Accuracy

    > Average log-odds intercept ≈ –0.551 (≈ 36.4 %), age slope ≈ 0.045 log-odds per SD (≈ 1.1 pp).

- Points per Game

    > Baseline PPG ≈ 11.26, age slope ≈ 0.89 PPG per SD (95 % CI overlaps 0).

- Partial pooling

    > Centers ≈ 33.6 %, SGs ≈ 38.9 % (95 % CI ∼ [x,y]), low‐volume players shrink toward position means.

- Model fit

    > No divergent transitions at adapt_delta=0.995, $\widehat R!<!1.01$, ESS > 2 500; PPCs show no major misfit.

Full numerical tables and figures are in tables/ and figs/.

## License & Citation

This work is distributed under the MIT License (see LICENSE if included).
If you use any part of this analysis, please cite:

Aidinis, G. (2025). Bayesian Analysis of NBA 2023–24 Player Performance. STAT 9270 Final Project, University of Pennsylvania.
