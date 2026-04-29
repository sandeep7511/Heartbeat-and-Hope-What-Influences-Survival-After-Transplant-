# Heartbeat and Hope: What Influences Survival After Transplant?

## Project Overview
Hematopoietic stem cell transplantation (HSCT) is a critical therapy for life-threatening disorders, but predicting survival relies on a complex interplay of clinical and demographic variables. This project leverages a data-driven framework to analyze clinical data and identify the most significant predictors of post-transplant mortality. By understanding these factors, the project aims to augment decision-making and post-transplant treatment strategies.

## Dataset
The dataset was obtained from the Centre for International Blood & Marrow Transplant Research (CIBMTR). 
* **Population**: The cohort consists of 23,665 allogeneic hematopoietic cell transplantation (allo-HCT) recipients treated between 2008 and 2016.
* **Target Variable**: The dependent variable is `dead`, representing the binary survival status of the patient (Alive or Dead).
* **Features**: The dataset utilizes 20 independent variables, including patient age, performance status, comorbidity index, disease severity, and graft type.

## Technologies and Tools
The data mining and analysis were implemented entirely in R, utilizing its robust ecosystem of data science packages. 
* **tidyverse & dplyr**: Used for data manipulation, cleaning, and transformation.
* **ggplot2 & ggcorrplot**: Used for exploratory data visualizations and correlation matrices.
* **caret**: Facilitated data partitioning, model training, and performance evaluation.
* **Boruta**: Applied for rigorous feature selection using a random forest wrapper algorithm.
* **PROC**: Used to compute Receiver Operating Characteristic (ROC) curves and evaluate the Area Under the Curve (AUC).
* **car**: Utilized to assess multicollinearity through the Variance Inflation Factor (VIF).

## Methodology

### 1. Data Preparation and Exploration
The initial phase involved handling missing values and converting relevant categorical and binary data into distinct factors. Exploratory Data Analysis (EDA) was conducted to visualize the distributions of age, sex, and the correlation between variables such as graft-versus-host disease (GVHD) severity and survival rates. 

### 2. Feature Selection
The Boruta algorithm was employed on the training data to isolate relevant predictors. Over 99 iterations, Boruta confirmed 21 attributes as highly important for predicting the outcome (including age and GVHD grades) and rejected 6 attributes as unimportant.

### 3. Model Development
A logistic regression model was built to estimate the likelihood of death based on the selected predictor variables. To ensure the model's efficiency and eliminate redundant features, bidirectional stepwise selection using the Akaike Information Criterion (AIC) was applied. Multicollinearity was also checked, confirming that most variables contributed independent information to the model.

## Key Findings and Results

### Model Performance
The logistic regression model demonstrated excellent discriminative power and calibration. 
* **Accuracy**: The model achieved an overall accuracy of 0.8899 on the testing set.
* **AUC**: The Area Under the Curve reached 0.9474, indicating an exceptional ability to correctly distinguish between survivors and non-survivors.
* **Sensitivity & Specificity**: The model correctly identified 91.49% of actual survivors and 86.18% of deceased patients.

### Significant Risk Factors
* **Renal Failure**: Identified as the strongest risk factor, multiplying the odds of death by an estimated 692%.
* **Severe GVHD**: Acute GVHD Grade 3-4 increases the odds of death by approximately 140%.
* **Age**: Every additional year of patient age increases the odds of death by about 2%.

### Protective Factors
* **Transplant Year**: Survival probability improved over time, with each successive year from 2008 to 2016 associated with a 61% reduction in mortality odds.
* **Donor Type**: Transplants utilizing cord blood with an unknown HLA match reduced the odds of death by 58%.

## Risk Stratification
To enhance clinical utility, the model's predicted probabilities were transformed into a risk-stratification tool. Patients in the test cohort were classified into three discrete risk categories based on their clinical features:
* **Low Risk**: 49% of the cohort.
* **Medium Risk**: 13% of the cohort.
* **High Risk**: 38% of the cohort.
