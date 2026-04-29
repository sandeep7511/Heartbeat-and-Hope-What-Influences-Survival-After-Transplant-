# Heartbeat and Hope: What Influences Survival After Transplant?

## Project Overview
[cite_start]Hematopoietic stem cell transplantation (HSCT) is a critical therapy for life-threatening disorders, but predicting survival relies on a complex interplay of clinical and demographic variables[cite: 636]. [cite_start]This project leverages a data-driven framework to analyze clinical data and identify the most significant predictors of post-transplant mortality[cite: 638, 640]. [cite_start]By understanding these factors, the project aims to augment decision-making and post-transplant treatment strategies[cite: 637].

## Dataset
[cite_start]The dataset was obtained from the Centre for International Blood & Marrow Transplant Research (CIBMTR)[cite: 644]. 
* [cite_start]**Population**: The cohort consists of 23,665 allogeneic hematopoietic cell transplantation (allo-HCT) recipients treated between 2008 and 2016[cite: 649, 653].
* [cite_start]**Target Variable**: The dependent variable is `dead`, representing the binary survival status of the patient (Alive or Dead)[cite: 666, 669].
* [cite_start]**Features**: The dataset utilizes 20 independent variables, including patient age, performance status, comorbidity index, disease severity, and graft type[cite: 664, 666].

## Technologies and Tools
[cite_start]The data mining and analysis were implemented entirely in R, utilizing its robust ecosystem of data science packages[cite: 748, 749]. 
* [cite_start]**tidyverse & dplyr**: Used for data manipulation, cleaning, and transformation[cite: 754, 761].
* [cite_start]**ggplot2 & ggcorrplot**: Used for exploratory data visualizations and correlation matrices[cite: 754, 760].
* [cite_start]**caret**: Facilitated data partitioning, model training, and performance evaluation[cite: 756].
* [cite_start]**Boruta**: Applied for rigorous feature selection using a random forest wrapper algorithm[cite: 758].
* [cite_start]**PROC**: Used to compute Receiver Operating Characteristic (ROC) curves and evaluate the Area Under the Curve (AUC)[cite: 765].
* [cite_start]**car**: Utilized to assess multicollinearity through the Variance Inflation Factor (VIF)[cite: 766].

## Methodology

### 1. Data Preparation and Exploration
[cite_start]The initial phase involved handling missing values and converting relevant categorical and binary data into distinct factors[cite: 672, 711]. [cite_start]Exploratory Data Analysis (EDA) was conducted to visualize the distributions of age, sex, and the correlation between variables such as graft-versus-host disease (GVHD) severity and survival rates[cite: 801, 822, 1408]. 

### 2. Feature Selection
[cite_start]The Boruta algorithm was employed on the training data to isolate relevant predictors[cite: 1080]. [cite_start]Over 99 iterations, Boruta confirmed 21 attributes as highly important for predicting the outcome (including age and GVHD grades) and rejected 6 attributes as unimportant[cite: 1081, 1082].

### 3. Model Development
[cite_start]A logistic regression model was built to estimate the likelihood of death based on the selected predictor variables[cite: 1093, 1308]. [cite_start]To ensure the model's efficiency and eliminate redundant features, bidirectional stepwise selection using the Akaike Information Criterion (AIC) was applied[cite: 1245, 1246, 1247]. [cite_start]Multicollinearity was also checked, confirming that most variables contributed independent information to the model[cite: 1177].

## Key Findings and Results

### Model Performance
[cite_start]The logistic regression model demonstrated excellent discriminative power and calibration[cite: 1577]. 
* [cite_start]**Accuracy**: The model achieved an overall accuracy of 0.8899 on the testing set[cite: 1124].
* [cite_start]**AUC**: The Area Under the Curve reached 0.9474, indicating an exceptional ability to correctly distinguish between survivors and non-survivors[cite: 1163].
* [cite_start]**Sensitivity & Specificity**: The model correctly identified 91.49% of actual survivors and 86.18% of deceased patients[cite: 1128, 1129].

### Significant Risk Factors
* [cite_start]**Renal Failure**: Identified as the strongest risk factor, multiplying the odds of death by an estimated 692%[cite: 1582].
* [cite_start]**Severe GVHD**: Acute GVHD Grade 3-4 increases the odds of death by approximately 140%[cite: 1584].
* [cite_start]**Age**: Every additional year of patient age increases the odds of death by about 2%[cite: 1348].

### Protective Factors
* [cite_start]**Transplant Year**: Survival probability improved over time, with each successive year from 2008 to 2016 associated with a 61% reduction in mortality odds[cite: 1466, 1586].
* [cite_start]**Donor Type**: Transplants utilizing cord blood with an unknown HLA match reduced the odds of death by 58%[cite: 1589].

## Risk Stratification
[cite_start]To enhance clinical utility, the model's predicted probabilities were transformed into a risk-stratification tool[cite: 1571, 1610]. [cite_start]Patients in the test cohort were classified into three discrete risk categories based on their clinical features[cite: 1571]:
* [cite_start]**Low Risk**: 49% of the cohort[cite: 1573].
* [cite_start]**Medium Risk**: 13% of the cohort[cite: 1573].
* [cite_start]**High Risk**: 38% of the cohort[cite: 1573].
