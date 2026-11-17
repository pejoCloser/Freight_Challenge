# The Rhine Freight Challenge

Predicting the Rhine barge freight price **5 business days ahead**.

## Background

The challenge was created by a European energy company that manufactures, stores and distributes conventional fuels and sustainable energies and services.

The Rhine is one of the most frequented inland waterways in Europe and the main route from the Amsterdam-Rotterdam-Antwerp (ARA) region to Germany and Switzerland.

- The fleet is estimated at about 6,900 vessels.
- About 200 million tonnes are transported at the German-Dutch border, and about 310 million tonnes on the Dutch section of the river.

The freight price is one of the components of transportation cost. It influences:

- How logistics teams book barges for transportation.
- Trading decisions, since freight prices are a major driver of product prices in Germany, for example.

## The Challenge

Freight prices have extreme periods in which the price rises significantly. The business wants to better understand and predict these periods, because that is where most opportunities lie.

The business believes the freight price depends on:

1. **Rhine water levels.** Low water at the choke points limits the number of vessels that can pass and the cargo each vessel can carry.
2. **Supply and demand.**

> **Question: What is the freight price, 5 business days ahead?**

## Data

| File | Description | Period |
|------|-------------|--------|
| `RhineFreightData.csv` | Freight prices and Rhine water levels | 2013 - 2018 (development data) |
| `WeatherDataBasel.csv` | Weather data for Basel | 2013 - 2018 (development data) |
| Test data | To be supplied later | 2019 |

**Note:** the CSV files use `;` as the separator. Load them with:

```python
import pandas as pd

df = pd.read_csv("data/WeatherDataBasel.csv", sep=";")
```

If numbers appear with decimal commas (e.g. `8,7`), add `decimal=","`.

## Repository Structure

```
.
├── data/               # Raw CSV files (RhineFreightData.csv, WeatherDataBasel.csv)
├── notebooks/          # Exploration and modelling notebooks
├── reports/            # Generated data profiling reports
├── README.md
└── requirements.txt
```

Adjust this to match your actual layout.

## Getting Started

```bash
# Clone the repository
git clone <your-repo-url>
cd Challenge2

# Create and activate a virtual environment (Windows)
python -m venv .venv
.venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

Suggested `requirements.txt`:

```
pandas
numpy
scikit-learn
matplotlib
seaborn
ydata-profiling
setuptools<81
jupyter
```

`setuptools<81` is needed because `ydata-profiling` imports `pkg_resources`, which newer setuptools versions removed.

### Generating a data profile

```python
from ydata_profiling import ProfileReport

profile = ProfileReport(df, title="Rhine Freight - Data Profile")
profile.to_file("reports/profile.html")
```

## Approach

- [ ] Explore and profile the freight, water level and weather data
- [ ] Merge the datasets on date
- [ ] Engineer features (lagged prices, water level trends, weather, seasonality)
- [ ] Build a baseline model and a forecasting model for t + 5 business days
- [ ] Evaluate performance, with attention to the extreme price periods
- [ ] Predict on the 2019 test data once supplied

## Evaluation

Model performance is assessed on the held-out 2019 test data. Metrics to be defined (for example MAE, RMSE, and performance during extreme price periods).

## Author

Pedro Jorge, Closer Consultoria Lda
