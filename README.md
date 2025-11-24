# Kepler Exoplanet Classification (Machine Learning)

A full machine learning pipeline for classifying Kepler Objects of Interest (KOIs) into:

- CONFIRMED exoplanets
- CANDIDATE exoplanets
- FALSE POSITIVES

using NASA’s Kepler cumulative KOI dataset.

This project includes:

- Data cleaning and exploration
- Feature engineering
- Machine Learning modeling
- Comparative evaluation
- Final scientific-style PDF report in LaTeX

## Project Structure

```
kepler-exoplanet-classification
├── data/
│   └── cumulative_2025.11.22_15.28.10.csv
├── notebooks/
│   ├── 01_dataset_overview_and_cleaning.ipynb
│   ├── 02_data_exploration.ipynb
│   └── 03_modeling_and_evaluation.ipynb
├── report/
│   └── kepler_report.pdf
├── requirements.txt
└── README.md
```

## Models Used

* **Logistic Regression (Linear Benchmark):** To establish the linear performance ceiling.
* **Decision Tree:** To confirm the non-linear nature of the data.
* **Random Forest:** The final ensemble method.
* **Neural Network (SHLNN):** Tested as a final non-linear comparison.

## Results Summary

| Model               | Accuracy | F1-Score | AUC Score |
| ------------------- | -------- | -------- | --------- |
| Logistic Regression | 85.69%   | 0.8204   | 0.9344    |
| Decision Tree       | 90.45%   | 0.8623   | 0.9570    |
| Random Forest       | **91.85%**| **0.8818** | **0.9736** |
| Neural Network      | 89.94%   | 0.8603   | 0.9637    |

*Random Forest achieved the best performance.*

## Full Report

The complete scientific report is available here:

**/report/kepler_report.pdf**


## Installation

```bash
# It's recommended to create and activate a virtual environment first.
pip install -r requirements.txt
```


## Usage

```bash
jupyter notebook notebooks/01_dataset_overview_and_cleaning.ipynb
```

From there, proceed through:

1. **01_dataset_overview_and_cleaning.ipynb**
   Load dataset, inspect columns, handle missing values.

2. **02_data_exploration.ipynb**
   Exploring the features if they are significant to exoplanets or not.

3. **03_modeling_and_evaluation.ipynb**
   Train Logistic Regression, Decision Tree, Random Forest, and Neural Network.

## Dataset
NASA Kepler KOI cumulative table:
https://exoplanetarchive.ipac.caltech.edu/

## Acknowledgements

* NASA Exoplanet Archive
* Kepler Mission Team
* **Project Methodology and Structure:** Directly inspired by and replicating the approach detailed in the **DataMining** repository by Alberto Monaco: [https://github.com/AlbertoMonaco/DataMining](https://github.com/AlbertoMonaco/DataMining).


