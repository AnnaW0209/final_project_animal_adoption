# Shelter Animal Outcome Prediction (Multiclass ML Project)

This project predicts **Austin Animal Center animal outcomes** (Adoptioon, Transfer, Return to Owner, Euthanasia, Other)
based solely on **intake information** using a machine learning pipeline.

---

## Project Overview
- **Goal:** Predict each animal's outcome category at intake time.
- **Type:** Multiclass classification
- **Data Source:** [Austin Animal Center Open Data Portal](https://data.austintexas.gov/Health-and-Community-Services/Austin-Animal-Center-Outcomes-10-01-2013-to-05-05-/9t4d-g238)
- **Methods:** Logistic Regression (L2 Regularization), One-Hot Encoding, Standardization
- **Split:** 70% Train / 15% Validation / 15% Test (Group-based by 'animal_id')
- **Libraries:** pandas, numpy, scikit-learn, matplotlib

---

## Data Pipeline
1. **Download** the *Intakes* and *Outcomes* datasets via Socrata API
2. **Clean** and convert key fields: timestamp, age in days, missing values
3. **Pair** intake and outcome events by 'animal_id' and nearest future event time
4. **EDA**:
    - Distribution of intake types vs. outcomes
    - Breed composition vs. outcome rates
    - Shelter stay duration (long-taial pattern)
    - Age vs. outcome patterns
5. **Modeling**:
    - Logistic Regression (multiclass, 'lbfgs', 'class_weight=balanced')
    - Compared against majority baseline and random baseline
    - Evaluation using Accuracy, Macro-F1, Confusion Matrix
    
---

## Key Insights
- Intake Type strongly influences outcome composition
- Shelter stay duration has a heavy right-skew, with most animals stay < 10 days
- Model performance limited by non-IID structure & high-cardinality categorical features
- Macro-F1 improves over random baseline but still constrained by the data imbalance

---

## Repository Structure
final_project_animal_adoption/  
|  
|---- script/ # Python scripts for data cleaning & pairing  
|---- figures/ # All generated plots for EDA and presentation  
|---- raw_data/ # CSV data  
|---- README.md # This file  

---

## Author
**Yiqing Wang**  
DSI, Brown University  
[Github Repository Link](https://github.com/AnnaW0209/final_project_animal_adoption)
