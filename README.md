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

## Notes
- The original case datasets (files 01-08) are not included. The notebook reads the
  cleaned quarterly tables in outputs/ instead.
- Step d (3D file exploration) was run once and is kept as non-executable cells.
- Model: PCA + Gaussian Process Regression. A Keras dense network is the benchmark.
- All assumptions (prices, forecast method, windows) are in outputs/assumptions.md.