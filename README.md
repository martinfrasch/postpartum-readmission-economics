# When does the model pay?

An interactive explorer of the health-economic analysis in *Predicting postpartum readmission from sociodemographic data* (nuMoM2b cohort; manuscript under review at *Machine Learning: Health*).

**Preprint:** [medRxiv 2025.12.16.25342440](https://doi.org/10.1101/2025.12.16.25342440). The link resolves to the latest version; the revised manuscript will be posted there.

**Live page:** https://martinfrasch.github.io/postpartum-readmission-economics/

A risk model earns money only when it beats the two strategies that need no model: contact every new mother after discharge, or contact none. The page lets you vary the cost of one contact, the share of readmissions a contact prevents, the cost of a readmission and the model's running cost, and shows where, if anywhere, acting on a model's predictions adds value.

## Defaults

| Input | Base case | Range | Source |
|---|---|---|---|
| Cost of one readmission | $8,100 | $5,200–11,100 | Mean hospital cost, Nationwide Readmissions Database (Wen et al. 2020), CPI-U to 2024 dollars |
| Readmissions prevented among those contacted | 20% | 10–50% | Remote BP monitoring (Lemon et al. 2024); transitional care (Leppin et al. 2014). 50% is optimistic. |
| Cost per contact | slider | $5–400 | Medicaid pays about $44 per home visit and $47 per physician phone call (T-MSIS, national means per claim line) |
| Model running cost | $3.00 per delivery | $2.30–4.10 | Authors' assumption: development and EHR integration amortised over 5 years plus maintenance |

## Data and privacy

The page contains no participant-level data. nuMoM2b data are held under a NICHD DASH data-use agreement. The only data embedded in `index.html` are Platt-recalibrated test-set risks grouped into four bins per model, each containing at least 11 readmissions and at least 11 non-readmissions (test set: 2,633 participants, 46 readmissions). Because a model can only contact whole bins, its curves are coarser than, and its gains generally smaller than, the patient-level results in the manuscript, which are authoritative.

The dashed "hypothetical better model" is a **simulation**: an idealised, perfectly calibrated binormal model at the same prevalence, not fitted to any data.

## Build

`index.html` is a single self-contained file. It is generated from the manuscript repository by inserting `results/revision/economic_bins_public.json` (written by `src/public_bins.py`) into `scripts/economics_explorer_template.html`.

## Licence

Code: MIT (see `LICENSE`). Figures and text: CC BY 4.0.
