# Weather Data Analysis

A Python script for analyzing historical weather data spanning **1969–2026**, producing summary statistics, visualizations, and long-term climate trend insights.

## Overview

This tool ingests daily weather records from an Excel file and generates:

- Summary statistics across all weather variables
- Annual temperature trends with a 10-year rolling mean and linear regression
- Monthly and seasonal breakdowns of temperature and precipitation
- Detection and reporting of extreme weather events
- A multi-panel chart saved as a PNG

## Requirements

- Python 3.8+
- `pandas`
- `numpy`
- `matplotlib`
- `scipy`
- `openpyxl` (for reading `.xlsx` files)

Install dependencies:

```bash
pip install pandas numpy matplotlib scipy openpyxl
```

## Input

Place a file named `weather_data.xlsx` in the same directory as the script. It must contain the following columns:

| Column | Description             | Unit |
|--------|-------------------------|------|
| `Date` | Calendar date           | —    |
| `PRCP` | Precipitation           | mm   |
| `TMAX` | Maximum temperature     | °C   |
| `TMIN` | Minimum temperature     | °C   |
| `RAIN` | Rainfall                | mm   |

## Usage

```bash
python weather_analysis.py
```

The script prints a report to the console and saves a chart to `weather_analysis.png` in the working directory.

## Output

### Console Report

- Date range and record count
- Descriptive statistics (mean, std, min/max, quartiles) for all variables
- Seasonal averages for TMAX, TMIN, and precipitation
- Extreme event counts and dates (hottest, coldest, wettest days)
- Linear regression results for the long-term temperature trend (slope, R², p-value)

### Chart (`weather_analysis.png`)

A 3×3 grid of panels covering:

1. Annual mean temperature with trend line and 10-year rolling mean
2. Annual total precipitation
3. Monthly temperature profile (TMAX/TMIN range)
4. Average monthly precipitation
5. Seasonal TMAX box plots
6. Daily temperature range histogram
7. Precipitation distribution on wet days
8. Correlation heatmap (PRCP, TMAX, TMIN, RAIN, ΔT)

## Definitions

- **TempRange** — daily spread computed as `TMAX − TMIN`
- **Seasons** — meteorological (Dec–Feb = Winter, Mar–May = Spring, Jun–Aug = Summer, Sep–Nov = Autumn)
- **Extreme thresholds** — hot day: TMAX ≥ 35 °C; cold day: TMIN ≤ −10 °C; heavy rain: PRCP ≥ 30 mm
