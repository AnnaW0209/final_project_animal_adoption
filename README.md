# Shelter Animal Outcome Prediction
**Multiclass Machine Learning Project**

<<<<<<< HEAD
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
=======
This project predicts the first recorded outcome of animals at the Austin Animal Center (Adoption, Transfer, Return to Owner, Euthanasia, or Other) using solely intake-level information. The task is formulated as a multiclass classification problem with strong class imbalance.

---

## Dataset
The dataset is publicly available from the Austin Animal Center: https://data.austintexas.gov/
Two tables (intakes and outcomes) are temporally matched to construct labels corresponding to each animal’s first observed outcome.

---

## Data Pipeline
1. **Download** the *Intakes* and *Outcomes* datasets via Socrata API
2. **Clean** and convert key fields: timestamp, age in days, missing values
3. **Pair** intake and outcome events by 'animal_id' and nearest future event time
4. **EDA**:
    Outcome classes distribution.
    Intake features vs Outcomes.
5. **Splitting&Preprocessing**
6. **Modeling**:
    - CV, Hyperparameter tuning, and Model selection
    - Logistic Regression, Decision Tree, Random Forest, XGBoost
7. **Results**:
    - Compare baseline prediction with the best model.
    - Interprete globally and locally
    
---

## Methods
- Group-aware train/test splitting to prevent leakage across records from the same animal
- Consolidation of rare outcome categories into a single *Other* class
- Feature preprocessing with one-hot encoding and scaling
- Models evaluated: Logistic Regression, Decision Tree, Random Forest, and XGBoost
- Early stopping for XGBoost using a group-aware validation split
- Repeated group-based test splits to estimate test-time uncertainty
- Model interpretability via permutation importance and SHAP values
>>>>>>> f9c8774 (Final Updates)

---

## Results
<<<<<<< HEAD
XGBoost achieves the strongest overall performance and consistently outperforms the baseline classifier across repeated group-based test splits.

All generated artifacts are stored as follows:
- Trained models, predictions, and metrics: `results/`
- Figures and plots: `figures/`
- Final report (PDF): `report/`
=======
Model performance is evaluated using the macro-averaged F1 score.
XGBoost achieves the strongest overall performance and consistently outperforms a baseline classifier across repeated test splits. 
Final predictions, metrics, and trained model artifacts are stored in the `results/` directory.
>>>>>>> f9c8774 (Final Updates)

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
