# Handedness-Age-at-Death-Intern-Project

**Author:** Praveen S  
**Notebook:** `Handedness_AgeAtDeath_Intern_project.ipynb`  
**Run environment:** Google Colab (recommended) or local Jupyter/Notebook

---

## Project overview

This project reproduces and extends an analysis of handedness (left- vs right-handedness) across ages and birth cohorts and studies how handedness interacts with observed age-at-death distributions. The work is implemented as a step-by-step Colab notebook and includes exploratory data analysis, simple probabilistic modeling (Bayesian-style reasoning), and visualizations.

The notebook is organized into **10 tasks** (Task 1 → Task 10). Each task is self-contained and produces plots and printed results.

---

## Datasets used

The notebook loads two remote datasets (via raw Gist URLs):

1. **Left-handedness by age** (`lh_data.csv`)  
   URL: `https://gist.githubusercontent.com/mbonsma/.../lh_data.csv`  
   Contains columns for age and left-handedness rates by sex.

2. **US death distribution (1999)** (`cdc_vs00199_table310.tsv`)  
   URL: `https://gist.githubusercontent.com/mbonsma/.../cdc_vs00199_table310.tsv`  
   Tab-separated file with age-specific counts of deaths ("Both Sexes").

> Note: the notebook pulls these files directly from the web; no local data files are required.

---

## What each task does (high level)

- **Task 1 — Plot left-handedness by age and sex**  
  Plots left-handed rates for males and females against age.

- **Task 2 — Compute birth year & mean left-handedness**  
  Adds a `Birth_year` column (1986 − Age) and computes the mean left-handedness (mean of male & female) and plots it by birth year.

- **Task 3 — Simple cohort-based probability model `P(LH | A)`**  
  Defines two cohort rates (early vs late 1900s) and returns `P(LH | age)` depending on age threshold ( >70 or ≤70). Demonstrates point examples and a plot.

- **Task 4 — Visualize death distribution (1999)**  
  Loads CDC death distribution and plots `Both Sexes` death counts by age.

- **Task 5 — Compute overall probability of being left-handed using population weights**  
  Uses assumed cohort rates and the death-distribution weights to compute an overall `P(LH)` for the population that died in the dataset.

- **Task 6 — Compute and visualize `P(A | LH)` using Bayes rule**  
  Assumes `P(LH | A)` (here simplified constant or function) and uses Bayes’ formula to compute `P(A | LH)` and plots the distribution.

- **Task 7 — Compute `P(A | RH)` (right-handed) similarly**  
  Using `P(RH | A) = 1 − P(LH | A)`, computes `P(A | RH)` and prints example values.

- **Task 8 — Compare `P(A | LH)` vs `P(A | RH)`**  
  Plots both posterior distributions on the same axis to compare shapes.

- **Task 9 — Compute average age-at-death for LH and RH populations**  
  Uses weighted ages (by `P(LH | A)` and `P(RH | A)`) to compute mean age-at-death for each group and prints the difference.

- **Task 10 — Year-comparison (e.g., 2018 vs 2025) variation**  
  Wraps `P(LH | A)` as a function of study year and plots `P(A | LH)` and `P(A | RH)` for different `study_year` values to show sensitivity.

---

## Key outputs & findings (what the notebook shows)

- Visualizations:
  - Left-handedness rate by age and sex.
  - Mean left-handedness by inferred birth year.
  - Death distribution (1999) by age.
  - Posterior distributions `P(A | LH)` and `P(A | RH)`.
  - Comparison plots for different study years.

- Calculations:
  - Overall population probability of being left-handed (weighted by deaths).
  - Average age-at-death estimates for left- and right-handed groups and the difference.

> The notebook uses simplified assumptions for `P(LH | A)` (constant or stepwise cohort rates) to illustrate Bayesian inversion and the impact of cohort effects on apparent age-at-death patterns.

---

## How to run

### Option A — Google Colab (recommended)
1. Open Colab: https://colab.research.google.com  
2. Click **File → Open notebook → GitHub** and paste the repository URL OR click **File → Upload notebook** and upload `Handedness_AgeAtDeath_Intern_project.ipynb`.  
3. Run cells sequentially (Runtime → Run all). Colab already includes required packages.

### Option B — Locally (Jupyter / JupyterLab)
1. Clone the repo:
   ```bash
