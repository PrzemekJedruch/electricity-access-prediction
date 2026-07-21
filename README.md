---
layout: post
title: "Predicting Global Electricity Access Using Machine Learning"
date: 2026-07-17
---
# Predicting Global Electricity Access Using Machine Learning

## Project Motivation
Access to electricity is a key indicator of economic and social development. In many countries, electricity access is closely linked to infrastructure, education, technology adoption, and urbanization. The goal of this project is to explore which factors are most strongly associated with electricity access and to build a machine learning model that can predict electricity access levels across countries.

This project follows the CRISP-DM process and communicates the findings in a way that is useful for stakeholders interested in development, infrastructure, and policy planning.

## CRISP-DM Structure
This notebook follows the CRISP-DM process:
1. Business Understanding
2. Data Understanding
3. Prepare Data
4. Modeling
5. Evaluation
6. Conclusion and Communication

## Business Questions
This analysis is guided by the following questions:

1. Which factors most strongly influence electricity access across countries?
2. How accurately can electricity access be predicted using socioeconomic and technological indicators?
3. How might electricity access change in the future for selected countries?

## Dataset
The dataset was obtained from the World Bank and includes cross-country development indicators related to economics, energy, technology, demographics, education, labor, and the environment.

The target variable is:

- **Access to electricity (% of population)**

Selected predictor variables include:

- GDP per capita
- Domestic credit to private sector
- Gross capital formation
- Electric power consumption
- Renewable energy consumption
- Individuals using the Internet
- Mobile cellular subscriptions
- Urban population
- Population density
- School enrollment, secondary
- Employment in industry
- CO2 emissions

## Project Structure

- `P_Data_Extract_From_Jobs.zip` — dataset files used in the analysis
- `Project.ipynb` — Jupyter notebook containing the full analysis
- `requirements.txt` — Python dependencies required to run the project

## Libraries Used
The main Python libraries used in this project are:

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- shap

## Summary of Results
The analysis found that internet usage, education, urbanization, and energy-related indicators were among the strongest predictors of electricity access.

A Random Forest regression model was used to predict electricity access and achieved:

- **R² = 0.86**
- **MAE = 5.80**

The model performed well overall and provided useful insight into the relative importance of different development indicators. SHAP analysis was also used to improve interpretability and explain how features influenced predictions.

In addition, the model was used to explore future electricity access scenarios for selected countries.

## Key Takeaways
- Electricity access is strongly associated with broader development patterns.
- Technology and education indicators appear to play an important role in prediction.
- Machine learning can provide useful support for understanding and forecasting development outcomes.
- Model interpretability tools such as SHAP help make predictions more transparent and stakeholder-friendly.

## How to Run the Project

1. Clone this repository:

```bash
git clone <your-repo-link>
cd predicting-electricity-access
```

2. Install the required libraries:
 
```bash
pip install -r requirements.txt
```
3. Launch Jupyter Notebook:

```bash
jupyter notebook
```
   
