# Project: Patient Selection for Diabetes Drug Testing

## Project Overview:

You are a data scientist working for an innovative unicorn healthcare startup that has developed a groundbreaking diabetes drug now entering Phase III clinical trials. This unique and sensitive drug requires 5-7 days of hospitalization for administration, frequent monitoring, and patient adherence training via a mobile application. To optimize patient selection for the trial, you have been provided with a patient dataset from a client partner. Your task is to build a predictive model that identifies the most suitable patients for testing—those who are likely to remain in the hospital for the required duration without incurring excessive additional costs for drug administration and monitoring.

## Project Goal:
Develop a regression model to predict a patient's expected hospitalization time and use this prediction to determine eligibility for the clinical trial. The model will be applied to filter and select patients who meet the hospitalization duration criteria.

## Modeling Approach:

* **Dataset:** A synthetic dataset based on the UCI Diabetes readmission dataset, with denormalized data at the encounter level for augmentation.
* **Regression Task:** Predict the expected number of hospitalization days for each patient.
* **Binary Classification:** Convert the regression output into a binary decision:
     - Include patients expected to stay for 5-7 days.
     - Exclude patients who are unlikely to meet this requirement

* **Key Considerations:**
* **Feature Engineering:** Extract and preprocess key medical code sets to ensure effective data representation at the encounter level.
* **Bias Analysis:** Evaluate the model for potential biases across key demographic groups to ensure fair and ethical patient selection.
