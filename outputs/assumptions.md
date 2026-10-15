# Assumptions - DWC26 forecast (1 Jan 2008 to 1 Jan 2028)

## Model and case selection
- Proxy model: PCA (4 components) + Gaussian Process Regression, trained on cases 1-70,
  validated on 71-85, tested on 86-100. A Keras dense network was the benchmark (about 18x less accurate).
- History matching: 100,000 random parameter combinations scored against observed production 1998-2008.
- The 10 submitted cases are the provided cases closest to the observed history: 11, 76, 40, 6, 50, 97, 20, 73, 26, 4.
- No CNN: the static maps of all cases are scaled copies of one template, so they add no new information.

## Forecast method
- Operating conditions stay unchanged after 2008 (organizer FAQ).
- Total liquid, water-to-oil ratio (WOR) and gas-to-oil ratio (GOR) are extrapolated with log-linear fits
  over the last 12 quarters (base case). A 8-quarter window is the upside case.
- Oil = liquid / (1 + WOR). Gas = oil x GOR. Water = liquid - oil.
- Window length was chosen by hiding the last 2 years and comparing the forecast to what actually happened.

## Prices (revenue scenarios)
- Oil: USD 94.302 per STB, WTI crude, 15 Oct 2026, 9am MYT.
- Gas: USD 3.2675 per MSCF, natural gas futures, quoted in USD/MMBtu, 15 Oct 2026, 9am MYT.
  MMBtu is treated as MSCF (1 MSCF is about 1.037 MMBtu).
- Low / base / high = 80% / 100% / 120% of today's price, held constant for 20 years.

## Revenue
- Revenue = oil volume x oil price + gas volume x gas price.
- Undiscounted, no costs, taxes or royalties, so this is revenue, not profit.
- Base revenue across the 10 cases: USD 1221 million to 1316 million.
- Oil is about 98.8% of base revenue.

## Limits
- History fixes porosity well but not permeability, so the 10 cases give near-identical forecasts.
- Rates are extrapolated trends, not a new reservoir simulation.
