# Forest Fire Prediction — Algerian Dataset

A data-driven study of forest fire prediction using exploratory 
analysis, multicollinearity diagnosis, dimensionality reduction, 
and machine learning classification.

Presented at **Advanced Data Analytics - Evaluation** (college course).

## Overview

Forest fires cause irreversible ecological and socioeconomic 
damage. This project investigates the Algerian Forest Fires 
Dataset (243 records, two regions: Bejaia and Sidi Bel-Abbes, 
June–September 2012) to identify key fire predictors and build 
stable, interpretable classification models.

The core challenge: fire weather indices (FWI, BUI, DMC, DC, 
FFMC, ISI) are mathematically derived from the same base 
measurements, causing severe multicollinearity that makes 
standard models unstable. This study addresses that directly.

## Pipeline

1. **Data Cleaning & Preprocessing** — region splitting, 
   missing value handling, label encoding
2. **EDA** — correlation heatmaps, boxplots, violin plots, 
   bivariate analysis, seasonal patterns
3. **Multicollinearity Diagnosis** — VIF analysis (BUI, DMC, 
   DC all VIF >> 100), Mahalanobis Q-Q plot
4. **Dimensionality Reduction** — PCA (3 components, 82.3% 
   variance) and Factor Analysis with Varimax rotation
5. **Classification** — Logistic Regression on Raw, PCA, and 
   FA features compared

## Key Results

| Model | Accuracy | AUC | 5-Fold CV |
|-------|----------|-----|-----------|
| Raw (10 features) | 97.26% | ~0.99 | ~96.5% |
| PCA (3 components) | 89.04% | 0.94 | 88.05% ± 6.64% |
| **FA (3 factors)** | **97.26%** | **0.99** | **95.48% ± 3.52%** |

**Factor Analysis is the recommended approach** — matches raw 
accuracy while eliminating multicollinearity and providing 
physically interpretable latent factors:
- **F1 — Dryness** (BUI, DC, DMC): long-term fuel moisture
- **F2 — Atmospheric** (ISI, FWI, FFMC): current weather conditions  
- **F3 — Spread** (Temperature, Wind, Rain): fire propagation

## Key Findings

- FFMC (r=0.77), ISI (r=0.74), FWI (r=0.72) are the strongest 
  fire predictors
- Rain acts as a near-binary suppressor: fires on only 20.9% 
  of rainy days vs majority of dry days
- Danger zone identified: FFMC > 80 + Wind > 15 km/h → 
  98.4% fire probability
- Sidi Bel-Abbes has higher baseline fire risk than Bejaia

## Tech Stack

Python, Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn, SciPy

## Files

- `ForestFire_initial_.ipynb` — full analysis notebook
- `Forest_Fire_Report.pdf` — detailed research paper
- `Forest_fires_ppt.pdf` — presentation slides

## Dataset & Citation

**Source:** UCI Machine Learning Repository — Algerian Forest Fires Dataset

Donated by Faroudja ABID, Microelectronic & Nanotechnology Division,  
Center for Development of Advanced Technologies (CDTA), Algeria.

If using this dataset, please cite:

> Faroudja ABID et al., "Predicting Forest Fire in Algeria using Data 
> Mining Techniques: Case Study of the Decision Tree Algorithm," 
> International Conference on Advanced Intelligent Systems for 
> Sustainable Development (AI2SD 2019), 08–11 July 2019, Marrakech, 
> Morocco.
