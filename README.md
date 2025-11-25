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
│   └── kepler_exoplanet_classification.pdf
├── requirements.txt
└── README.md
```
### Key Pipeline Steps

* **Feature Selection:** Initial 141 features were reduced to 21 through filtering, then further reduced to 13 high-impact features based on **Decision Tree Feature Importance**.
* **Preprocessing:** Handled missing values, removed anomalies, applied **Standard Scaling**, and performed a **stratified** train/test split.
* **Modeling:** Focused on confirming the non-linear relationship in the data, concluding that the **ensemble approach** was superior to both linear and single-layer neural network architectures.

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

[**/report/kepler_exoplanet_classification.pdf**](report/kepler_exoplanet_classification.pdf)


## Installation
### 1\. Installation

```bash
# It is recommended to create and activate a virtual environment first.
pip install -r requirements.txt
```

### 2\. Usage

You can step through the analysis using the Jupyter notebooks:

```bash
# Start Jupyter Lab
jupyter lab
```

From the interface, proceed through the notebooks in order:

1.  **`01_dataset_overview_and_cleaning.ipynb`**: Load, inspect, and clean the raw dataset; perform initial feature engineering.
2.  **`02_data_exploration.ipynb`**: Explore the relationships between features and the target disposition.
3.  **`03_modeling_and_evaluation.ipynb`**: Train all four models, perform Grid Search tuning, and generate final metrics.


## Acknowledgements

* **NASA Exoplanet Archive** and **Kepler Mission Team** for providing the data: [DataSource](https://exoplanetarchive.ipac.caltech.edu/).
* **Project Inspiration:** This project was initiated through the educational guidance of **Dr. Thomas Albin's YouTube channel, Astroniz**: [https://www.youtube.com/c/Astroniz]().
* **Methodology Source:** The project structure and core replication approach were inspired by the work found in the **DataMining** repository by Alberto Monaco: [https://github.com/AlbertoMonaco/DataMining](https://github.com/AlbertoMonaco/DataMining).