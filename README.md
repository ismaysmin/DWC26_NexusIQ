# DWC26 - Reservoir proxy model and 20-year forecast

Team: NexusIQ

Members: Chua Siew Tze, Chan Shan Wen, Aisyah Binti Shaaroni, Isma Yasmin Binti Ramli

## What this does
1. Builds a proxy model that maps 4 reservoir parameters (fault transmissibility,
   porosity multiplier, permeability multiplier, aquifer pore volume) to cumulative
   oil, gas and water production.
2. History-matches the model to the observed field data (1998-2008).
3. Forecasts oil, gas and water to 1 Jan 2028 for the 10 selected cases, fills the
   updated forecast template, and estimates revenue under low/base/high prices.

## How to run
1. Python 3.12. Install packages: pip install -r requirements.txt
2. Open DWC26_central_notebook.ipynb in Jupyter from this folder.
3. Kernel -> Restart & Run All. Runtime: a few minutes.

## Folders
- data: 09 Template Deliverable.xlsx (the organizers' template, needed for the forecast fill step)
- outputs: cleaned quarterly tables, trained models, charts, the filled template (forecast_filled_template.xlsx), revenue_scenarios.csv and assumptions.md
- Trained model: outputs/pca_gpr_model.joblib (PCA + Gaussian Process, the final model) and outputs/dense_model.keras (benchmark)

## Which file belongs to which part of the solution

| Part of the solution | Files |
|---|---|
| Input tables for the models (cleaned, quarterly) | outputs/case_settings.csv, outputs/oil_cumulative_quarterly.csv, outputs/gas_cumulative_quarterly.csv, outputs/water_cumulative_quarterly.csv |
| Benchmark model: Keras dense neural network | outputs/dense_model.keras, outputs/scaling.npz |
| Final model: PCA + Gaussian Process Regression | outputs/pca_gpr_model.joblib |
| Model comparison (validation errors) | outputs/model_comparison_validation.csv, outputs/model_comparison_oil.png, outputs/model_comparison_all_fluids.png |
| History matching and choice of the 10 cases | outputs/best10_given_cases.csv: the 10 cases from the 100 provided cases that we put in the template (the submission). outputs/best10_settings.csv: 10 parameter combinations the model found by itself, not in the provided cases. These were not submitted and are for reference only. |
| 20-year forecast (to 1 Jan 2028) | outputs/quarterly_volumes_and_rates.csv, outputs/forecast_rates.png, outputs/forecast_charts.png |
| Updated forecast template (deliverable) | outputs/forecast_filled_template.xlsx, outputs/template_case_mapping.csv (template sheet to provided case) |
| Revenue scenarios (low / base / high price) | outputs/revenue_scenarios.csv |
| Assumptions | outputs/assumptions.md |

## Notes
- The original case datasets (files 01-08) are not included. The notebook reads the
  cleaned quarterly tables in outputs/ instead.
- Step d (3D file exploration) was run once and is kept as non-executable cells.
- Model: PCA + Gaussian Process Regression. A Keras dense network is the benchmark.
- All assumptions (prices, forecast method, windows) are in outputs/assumptions.md.