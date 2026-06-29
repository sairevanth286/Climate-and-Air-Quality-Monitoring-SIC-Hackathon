# Climate and Air Quality Monitoring System

This project is an end-to-end air-quality monitoring solution built with Python. It cleans raw pollution sensor data, computes AQI values, detects critical pollution alerts, generates visual dashboards, and creates an interactive AQI risk map for Indian cities.

Report : https://docs.google.com/document/d/1PAdj9b2jHLSyauRNU480erc17ib5kvRLH5TL2Ss4oso/edit?usp=sharing 

## Problem Statement

Air pollution data collected from sensors often contains missing timestamps, invalid readings, inconsistent city names, unit suffixes, and extreme sensor spikes. The objective of this project is to convert noisy air-quality data into meaningful insights that can support pollution monitoring, health-risk analysis, and city-wise AQI reporting.

## Features

- Cleans and preprocesses raw AQI sensor data.
- Handles missing timestamps, invalid values, and sensor spikes.
- Computes AQI using `PM25`, `PM10`, `NO2`, `SO2`, `CO`, and `O3`.
- Classifies AQI into health-risk categories.
- Detects rush-hour pollution patterns.
- Uses Stack and Priority Queue data structures for alert detection.
- Generates a Matplotlib climate dashboard.
- Creates an interactive Folium AQI risk map.
- Exports daily city-wise AQI summary as CSV.

## Project Tasks

### Task 1: AQI Data Pipeline

The ETL pipeline cleans the dataset and prepares it for analysis.

- Drops rows with missing timestamps.
- Removes the `ug/m3` or `µg/m³` suffix from PM10 values.
- Replaces invalid CO readings such as `-9999` with `NaN`.
- Caps PM25 sensor spikes using the 99th percentile.
- Normalizes city names to Title Case.
- Fills missing pollutant values using city-wise medians.
- Computes AQI and AQI categories.
- Adds rush-hour and time-based columns.
- Exports `daily_aqi.csv`.

### Task 2: Pollution Alert System

This task applies DSA concepts to pollution monitoring.

- Implements a Stack from scratch.
- Implements a Priority Queue using a max-heap.
- Pushes AQI readings greater than `200` into the Stack.
- Transfers alerts to the Priority Queue based on AQI severity.
- Displays the top 10 most critical pollution alerts.
- Detects cities with 3 or more consecutive critical AQI hours.

### Task 3: Climate Dashboard

This task creates a Matplotlib dashboard containing:

- Daily average AQI time-series chart.
- AQI critical threshold visualization.
- Hour-of-day vs day-of-week AQI heatmap.
- Normalized pollutant comparison bar chart.
- City-wise AQI category pie charts.

The dashboard is saved as:

```text
climate_dashboard.png
```

### Task 4: AQI Risk Map

This task creates an interactive Folium map for AQI risk visualization.

- Displays city-wise AQI markers.
- Colors markers according to AQI severity.
- Shows popup details such as average AQI, category, worst pollutant, and rush-hour AQI difference.
- Adds a heatmap layer for pollution intensity.
- Saves the map as:

```text
aqi_risk_map.html
```

## System Requirements

### Hardware

- Processor: Intel i3 or higher
- RAM: Minimum 4 GB, recommended 8 GB
- Storage: At least 500 MB free space

### Software

- Python 3.8 or above
- VS Code, PyCharm, Jupyter Notebook, or any Python IDE
- Web browser for viewing the Folium map

## Python Libraries

The project uses the following Python libraries:

```text
pandas
numpy
matplotlib
folium
branca
```

Depending on the environment, the project may also use:

```text
seaborn style from matplotlib
folium.plugins.HeatMap
matplotlib.gridspec
matplotlib.patches
```

## How to Run

1. Install the required Python libraries:

```bash
pip install pandas numpy matplotlib folium branca
```

2. Run the main solution file:

```bash
python solution.py
```

3. After execution, the following output files are generated:

```text
daily_aqi.csv
climate_dashboard.png
aqi_risk_map.html
```

4. Open `aqi_risk_map.html` in a browser to view the interactive AQI risk map.

## Output Files

| File | Description |
| --- | --- |
| `daily_aqi.csv` | Daily city-wise average AQI summary |
| `climate_dashboard.png` | Static Matplotlib dashboard |
| `aqi_risk_map.html` | Interactive Folium AQI risk map |

## AQI Categories

| AQI Range | Category |
| --- | --- |
| Less than 50 | Good |
| 50 to 99 | Moderate |
| 100 to 199 | Unhealthy |
| 200 to 299 | Very Unhealthy |
| 300 and above | Hazardous |

## Conclusion

The Climate and Air Quality Monitoring System converts raw and noisy pollution data into useful AQI insights. It combines data cleaning, AQI computation, alert generation, dashboard visualization, and interactive mapping. The project demonstrates how Python, Pandas, Matplotlib, Folium, and basic data structures can be used together to solve a real-world environmental monitoring problem.
