# CRP and temperature in pediatric appendicitis

This repository contains the analysis notebook accompanying *Does Body Temperature Change the Association Between C-Reactive Protein and Pediatric Appendicitis Diagnosis?* The analysis is a secondary, observational study of the public Regensburg Pediatric Appendicitis Dataset (version 1.01).

## Research question

Does body temperature modify the diagnostic association between CRP and appendicitis among children admitted with suspected appendicitis? The main estimates describe statistical associations, not causal effects or validated clinical decision rules.

## Data

Obtain the original dataset from Zenodo: https://doi.org/10.5281/zenodo.7669442. Place the source Excel workbook in this directory as `app_data.xlsx`. The notebook expects the 782-row source dataset and the original named columns. Confirm the downloaded version and worksheet schema before execution. Patient-level data have not been redistributed here.

## Run

Using Python 3.11 or a compatible version:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
jupyter lab
```

Open `appendicitis_analysis.ipynb` and run all cells in order. Computation includes 253 pairwise tests, resampling, repeated cross-validation, and multiple imputation; these steps are computationally intensive.

The notebook writes output files to `interaction_outputs_final_clean/` (tables, figures, model outputs and package versions). The repository excludes these generated outputs and the source workbook.

## Analysis outline

- Quality-control audit, variable eligibility and descriptive analyses
- Modified Poisson interaction estimates with robust standard errors
- Logistic regression, marginal standardization and bootstrap uncertainty
- Missing-data and functional-form checks, ultrasound sensitivity analyses
- Discrimination, clinical threshold summaries and repeated cross-validation
- Exploratory all-pairs interaction screen with false-discovery-rate correction

## Verification status

The notebook was reviewed structurally and Python code cells were syntax-checked, but **the complete analysis was not re-executed** in this preparation because `app_data.xlsx` was not supplied with the notebook. Results in the manuscript must be compared against a fresh end-to-end execution before submission. In particular, check the multiple-imputation estimates in the manuscript's Table S17 against Table S22 and the final exported results.

## Citation

Regensburg Pediatric Appendicitis Dataset, version 1.01: https://doi.org/10.5281/zenodo.7669442.

Please cite the dataset creators and the associated study according to the dataset's citation instructions, alongside the research article if published.
