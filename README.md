# 🌀 Atlantic Tropical Storms & Hurricane Analysis (1975–2024)

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![pandas](https://img.shields.io/badge/pandas-Data%20Analysis-150458.svg)](https://pandas.pydata.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E.svg)](https://scikit-learn.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An end-to-end Machine Learning and Exploratory Data Analysis (EDA) project focusing on historical Atlantic tropical cyclone tracks and storm intensity dataset (`storms.csv`, derived from NOAA's HURDAT2 database spanning 1975 through 2024).

---

## 📌 Project Overview

Tropical cyclones pose severe environmental and economic hazards. Accurate modeling of meteorological parameters such as maximum sustained wind speeds, central barometric pressure, cyclone trajectories, and Saffir-Simpson hurricane categories is critical for emergency preparedness.

This project performs comprehensive data preprocessing, handling sentinel missing values (e.g., `-999`, `-1998`), statistical profiling, time-series feature engineering, data visualization, and predictive machine learning models (Random Forest Classifier / Regressor) to classify and estimate cyclone status and strength.

---

## 📊 Dataset Overview

The project uses `storms.csv` containing **22,705 observation rows** and **13 key columns**:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `name` | String | Common name or official identifier of the storm (e.g., *AL011975*, *Sara*, *Katrina*) |
| `year` | Integer | Year of observation (1975 – 2024) |
| `month` | Integer | Month of observation (1 – 12) |
| `day` | Integer | Day of month (1 – 31) |
| `hour` | Integer | UTC hour of observation (0 – 23 / synoptic track points) |
| `lat` | Float | Latitude coordinates of the storm center (degrees North) |
| `long` | Float | Longitude coordinates of the storm center (degrees West/East) |
| `status` | String | Cyclone classification (*tropical depression*, *tropical storm*, *hurricane*, etc.) |
| `category` | Float | Saffir-Simpson Hurricane Category (1 to 5; `NaN` for non-hurricanes) |
| `wind` | Integer | Maximum sustained wind speed in knots |
| `pressure` | Integer | Central atmospheric pressure in millibars (`mb`) |
| `tropicalstorm_force_diameter` | Integer | Diameter (nautical miles) experiencing $\ge 34\text{ kt}$ winds |
| `hurricane_force_diameter` | Integer | Diameter (nautical miles) experiencing $\ge 64\text{ kt}$ winds |

---

## 🛠️ Key Pipeline & Features

1. **Data Ingestion & Quality Inspection**:
   - Automated check of null values, column types, shape (`df.info()`), and summary statistics (`df.describe()`).
2. **Data Cleaning & Normalization**:
   - Replacement of dataset-specific missing value indicators (`-999`, `-1998`) with `np.nan`.
   - Handling bounded timestamps and constructing unified `datetime` columns.
   - Categorical missing value profiling (e.g., `category` NaN handling for non-hurricane entries).
3. **Exploratory Data Analysis (EDA)**:
   - Annual storm record frequency plots (1975–2024).
   - Frequency distribution of storm statuses (*tropical storm*, *tropical depression*, *hurricane*, etc.).
   - Wind speed and central pressure distribution histograms.
   - Spatial distribution (latitude vs. longitude track plotting).
4. **Feature Engineering & Aggregation**:
   - Storm-level grouping by cyclone `name` to extract `wind_max`, `pressure_min`, trajectory centroids, and cyclone `lifetime_hours`.
5. **Machine Learning Pipeline**:
   - Feature Scaling with `StandardScaler`.
   - Data partitioning via `train_test_split`.
   - Model training using `RandomForestClassifier` for storm classification.
   - Evaluation metrics: Accuracy Score, Classification Report (Precision, Recall, F1-Score), and Confusion Matrix.

---

## 📁 Repository Structure

```text
.
├── storms.csv              # Raw hurricane best track dataset (1975-2024)
├── main.py                 # Core analysis script / Google Colab notebook code
├── requirements.txt        # Required Python libraries
└── README.md               # Project documentation
