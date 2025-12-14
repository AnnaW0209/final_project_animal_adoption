# Shelter Animal Outcome Prediction
**Multiclass Machine Learning Project**

This project predicts the **first recorded outcome** of animals entering the Austin Animal Center using intake-level information.  
Possible outcomes include **Adoption, Transfer, Return to Owner, Euthanasia, and Other**.
The task is formulated as a **multiclass classification problem** with significant class imbalance.  
The goal is to build a **reproducible, leakage-aware ML pipeline** and compare multiple models using appropriate evaluation metrics.

---

## Project Overview
Animal shelters must make timely and informed decisions under resource constraints.  
Using publicly available intake and outcome records from the Austin Animal Center, this project builds and evaluates machine learning models to predict an animal’s first observed outcome after intake.

Key characteristics of the project:
- Multiclass classification with imbalanced classes
- Group-aware data splitting to avoid leakage across repeated animal records
- Emphasis on reproducibility and uncertainty estimation
- Model interpretability using global and local feature importance methods

---

## Dataset
The data are publicly available from the **Austin Animal Center** via the City of Austin Open Data Portal:  
https://data.austintexas.gov/

Two datasets are used:
- **Intakes**
- **Outcomes**

These tables are temporally matched to assign each animal its **first recorded outcome** following intake.

---

## Methods
### Data Processing
- Download intake and outcome tables via the Socrata API
- Convert timestamps and transform age to numeric (days)
- Handle missing values and inconsistent categorical fields
- Match intake events with the nearest future outcome by `animal_id`

### Modeling Pipeline
- Group-aware train/test splitting to prevent data leakage
- Feature preprocessing with scaling and one-hot encoding
- Consolidation of rare outcome categories into an **Other** class
- Models evaluated:
  - Logistic Regression
  - Decision Tree
  - Random Forest
  - XGBoost
- Early stopping for XGBoost using a group-aware validation split
- Repeated group-based test splits to estimate test-time uncertainty

### Evaluation & Interpretation
- Primary metric: **macro-averaged F1 score**
- Baseline comparison
- Global feature importance via permutation importance
- Local interpretability using SHAP values

---

## Results
XGBoost achieves the strongest overall performance and consistently outperforms the baseline classifier across repeated group-based test splits.

All generated artifacts are stored as follows:
- Trained models, predictions, and metrics: `results/`
- Figures and plots: `figures/`
- Final report (PDF): `report/`

---

## Reproducibility
This project was developed using Python 3.11.
All required packages and versions are specified in `environment.yml`.

To recreate the environment:
```
conda env create -f environment.yml
conda activate adopt
```
To reproduce the results, run the notebook in src/.

---

## Repository Structure
final_project_animal_adoption/  
.
├── data/        # Raw input data
├── figures/     # Generated figures
├── results/     # Predictions, metrics, and trained models
├── report/      # Final project report (PDF)
├── src/         # Source code and notebooks
│   └── intermediate/        # Intermediate analysis files (not final results)
├── environment.yml
├── .gitignore
├── LICENSE
└── README.md

---

## License
This project is released under the MIT License.

---

## Author
**Yiqing Wang**  
DSI, Brown University  
[Github Repository Link](https://github.com/AnnaW0209/final_project_animal_adoption)
