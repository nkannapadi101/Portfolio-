# Determining Factors for Delaying Medical Treatment
 
**Multivariable logistic regression analysis of NHIS 2024**
 
> Insurance coverage — not race — is the dominant driver of cost-related delays in medical care.
 
## Problem
 
Many U.S. adults delay medical care due to cost, and raw statistics show higher delay rates among minority and uninsured adults. But race, insurance, and education are entangled — policymakers need to know which lever actually matters. This project uses multivariable logistic regression to separate their independent effects.
 
## Methodology
 
A reproducible R Markdown pipeline built on the CDC's [2024 NHIS Sample Adult file](https://www.cdc.gov/nchs/nhis/documentation/2024-nhis.html) (n = 19,303):
 
- Codebook-driven data cleaning with variable-specific missing-value handling
- Descriptive analysis with insurance-stratified breakdowns
- Likelihood ratio tests comparing bivariate models to a null model
- Multivariable logistic regression reported as adjusted odds ratios with 95% CIs
All statistics in the written interpretation are computed inline from the fitted model objects, so the narrative can't drift from the results.
 
## Key Findings
 
| Predictor | Adjusted OR | 95% CI | p-value |
|---|---|---|---|
| Uninsured (vs. covered) | **6.55** | [5.60, 7.65] | < .001 |
| Black/African American (vs. White) | 0.91 | [0.74, 1.11] | .348 |
| Asian (vs. White) | 0.45 | [0.33, 0.59] | < .001 |
| Hispanic (vs. White) | 0.91 | [0.77, 1.08] | .296 |
| Bachelor's (vs. High School) | 1.21 | [1.06, 1.38] | .005 |
| Master's (vs. High School) | 1.29 | [1.10, 1.52] | .002 |
| Doctoral (vs. High School) | 0.76 | [0.56, 1.01] | .067 |
 
- **Insurance is overwhelmingly the strongest predictor** — uninsured adults have 6.55× the odds of delaying care.
- **After controlling for insurance, Black–White and Hispanic–White disparities disappear**, suggesting coverage expansion is both an access *and* equity intervention.
- **Unexpectedly, Bachelor's and Master's degree holders delay care more** than high school graduates.
## Repository Structure
 
```
├── NHIS_FinalPaper_Analysis.Rmd   # Full reproducible analysis
├── NHIS_FinalPaper_Analysis.pdf   # Knitted output
├── writeup/
│   └── NHIS_Writeup.docx          # Policy and Analysis writeup with discussion
└── README.md
```
 
## Reproducing the Analysis
 
1. Download the 2024 Sample Adult CSV from the [NHIS website](https://www.cdc.gov/nchs/nhis/documentation/2024-nhis.html) (Sample Adult Interview → Public use data) and save it as `national_health_interview_survey.csv` in the repo root.
2. Install dependencies:
```r
   install.packages(c("dplyr", "ggplot2", "broom", "readr", "rmarkdown", "scales"))
```
3. Knit:
```r
   rmarkdown::render("NHIS_FinalPaper_Analysis.Rmd")
```
 
 
## Reflection
 
This project taught me how to work with large federal survey datasets — navigating NHIS codebooks, handling variable-specific missing-value schemes, and managing deliberate sample restrictions across a 32,000-row file. The biggest lesson was to interrogate odd-looking statistics rather than take them at face value: a race/ethnicity distribution that didn't match known NHIS demographics led me to catch a mislabeled recode that clean-running code had hidden. To improve, I'd apply NHIS survey weights for population-representative estimates and add income and employment covariates to probe the surprising education finding.
 
## Limitations
 
Unweighted estimates (no NHIS survey weights, so results describe the analytic sample rather than the U.S. population); complete-case analysis; cross-sectional design — associations, not causal claims.
 
---
