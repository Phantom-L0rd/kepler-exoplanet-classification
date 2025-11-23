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
.
├── data/
│   └── cumulative_2025.11.22_15.28.10.csv
├── notebooks/
│   ├── 01_dataset_overview_and_cleaning.ipynb
│   ├── 02_feature_engineering_and_preparation.ipynb
│   ├── 03_modeling_and_evaluation.ipynb
│   └── 04_results_analysis_and_visualization.ipynb
├── report/
│   └── kepler_report.pdf
├── output/
│   ├── predictions.csv
│   ├── confusion_matrices/
│   └── feature_importances.png
├── requirements.txt
└── README.md
```

## Models Used

* Logistic Regression
* Decision Tree
* Random Forest
* Neural Network (1 Hidden Layer)

## Results Summary

| Model               | Accuracy | F1-Score |
| ------------------- | -------- | -------- |
| Logistic Regression | XX%      | XX       |
| Decision Tree       | XX%      | XX       |
| Random Forest       | **XX%**  | **XX**   |
| Neural Network      | XX%      | XX       |

*Random Forest achieved the best performance.*

## Full Report

The complete scientific report is available here:

**/report/kepler_report.pdf**


## Installation

```bash
pip install -r requirements.txt
```


## Usage

```bash
jupyter notebook notebooks/01_dataset_overview_and_cleaning.ipynb
```

From there, proceed through:

1. **01_dataset_overview_and_cleaning.ipynb**
   Load dataset, inspect columns, handle missing values.

2. **02_feature_engineering_and_preparation.ipynb**
   Select features, scale/impute values, handle class imbalance.

3. **03_modeling_and_evaluation.ipynb**
   Train Logistic Regression, Decision Tree, Random Forest, and Neural Network.

4. **04_results_analysis_and_visualization.ipynb**
   Generate confusion matrices, feature importance plots, and final predictions.

### **Run requirements**

```bash
pip install -r requirements.txt
```


## Dataset
NASA Kepler KOI cumulative table:
https://exoplanetarchive.ipac.caltech.edu/

## Acknowledgements

* NASA Exoplanet Archive
* Kepler Mission Team
* McCauliff et al. (Random Forest vetting)

