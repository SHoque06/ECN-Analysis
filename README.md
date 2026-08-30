# UK ECN Statistical Analysis & Ecological Modelling

An applied statistical analysis of terrestrial and invertebrate monitoring data from the UK Environmental Change Network (ECN). This repository demonstrates end-to-end data processing for observational datasets, focusing on extracting reliable signals from noisy ecological records using robust data wrangling and statistical modelling. 

## Data Wrangling & Cleaning
Handling the real-world inconsistencies of the ECN datasets required extensive pre-processing using Tidy R (`dplyr`, `tidyr`):
* **Data Restructuring:** Utilized `pivot_wider()` to convert long-format ecological recordings into tidy, analysis-ready data frames, isolating variables like tree diameter and height for individual analysis.
* **Cross-Dataset Integration:** Performed aggregate joins across independent vegetation and invertebrate datasets to evaluate biological dependencies (e.g., woodland diversity vs. moth abundance).
* **Outlier & Anomaly Handling:** Systematically identified and removed high-leverage outliers (such as extreme weather anomalies and recording errors) that skewed Ordinary Least Squares (OLS) regression fits, verifying removal via scale-location and Residuals vs Leverage diagnostic plots.
* **Temporal Feature Engineering:** Parsed raw date strings into discrete calendar weeks and seasonal windows to track annual biological cycles.

## Statistical Modelling & EDA
* **Exploratory Data Analysis:** Built robust `ggplot2` visualizations to uncover spatial heterogeneity, temporal stability, zero-inflation, and uneven sampling efforts across 12 UK monitoring sites.
* **Advanced Regression Techniques:** Addressed heteroscedasticity and non-linearity by implementing Weighted Least Squares (WLS) and polynomial regression, evaluating models via $R^{2}$, RMSE, and AIC/BIC metrics.
* **Parameter Estimation:** Derived Method of Moments (MoM) estimators to fit Poisson, Gamma, and Negative Binomial distributions for overdispersed, right-skewed count data.
* **Site-Specific Modelling:** Contrasted global linear models with site-separated models to demonstrate how spatial heterogeneity and specific habitat factors mask broader trends.

## Tech Stack
* **Language:** R
* **Libraries:** `dplyr`, `tidyr`, `ggplot2`, `gridExtra`, `knitr`, `lubridate`
* **Documentation:** RMarkdown for reproducible reporting, featuring LaTeX for mathematical derivations

## Data Sources
The analysis relies on public data from the UK Centre for Ecology & Hydrology (UKCEH):
* **Vegetation:** Fine-grain (1994-2015), Woodland (1993-2014), and Baseline (1991-2000) surveys.
* **Invertebrates:** Butterflies (1993-2015) and Moths (1992-2015).
