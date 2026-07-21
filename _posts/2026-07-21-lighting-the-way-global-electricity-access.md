---
layout: post
title: "Lighting the Way: What Helps Countries Gain Better Access to Electricity?"
date: 2026-07-21
author: Przemysław Jędruch
categories: [data-science, machine-learning]
tags: [electricity-access, world-bank, random-forest, shap]
---

Electricity is part of almost everything we do. It powers homes, schools, hospitals, businesses, phones, and the internet.

However, access to electricity is still very different from one country to another. In some countries, almost everyone has electricity. In others, many people still live without a reliable connection.

In this project, I used World Bank data to explore a simple question:

> **What can country-level data tell us about access to electricity?**

I also built a machine learning model to check whether electricity access could be estimated from a small group of development indicators.

![Indicators connected with electricity access]({{ '/assets/images/correlation-with-target.png' | relative_url }})

*Internet use, secondary education, mobile subscriptions, and urban population had the strongest relationships with electricity access.*

## Questions explored in this project

The analysis focuses on three practical questions:

1. **Which development factors are most closely connected with electricity access?**
2. **Can a machine learning model estimate electricity access with useful accuracy?**
3. **How could electricity access change if selected development indicators improved?**

Each question is answered below using charts, model results, and a plain-language explanation of what the result may mean.

## Question 1: Which factors are most closely connected with electricity access?

### How I answered the question

I compared electricity access with a range of economic, educational, technological, and population indicators.

The four strongest positive relationships were:

- **Internet usage:** 0.67
- **Secondary school enrollment:** 0.64
- **Mobile cellular subscriptions:** 0.63
- **Urban population:** 0.62

A value closer to 1 means that two indicators often rise together. For example, countries with higher internet use also tended to have higher electricity access.

This does not prove that internet use directly causes electricity access to improve. It shows that the two are strongly connected in the data.

### What the model found

I also used a Random Forest model. A Random Forest is a machine learning method that combines many decision trees to produce a prediction.

![Factors used most often by the model]({{ '/assets/images/feature-importance.png' | relative_url }})

Internet usage was the most important factor in the model. Urban population, secondary school enrollment, and mobile subscriptions were also useful.

To better understand the predictions, I used SHAP. SHAP is a tool that shows which factors pushed a model prediction higher or lower.

![How different factors influenced the model]({{ '/assets/images/shap-summary.png' | relative_url }})

### What this means

Electricity access appears to be part of a wider development picture.

Countries with stronger education systems, better digital access, more mobile connections, and greater urban development also tend to have better access to electricity.

For governments and development organizations, this suggests that electricity projects should not always be planned in isolation. Energy, education, communications, and local development may need to be considered together.

## Question 2: Can electricity access be estimated accurately?

### How I answered the question

I trained the Random Forest model using four indicators:

- internet usage;
- secondary school enrollment;
- mobile subscriptions;
- urban population.

The model was trained on one part of the dataset and tested on data it had not seen during training.

### Results

| Measure | Result | Meaning in simple terms |
|---|---:|---|
| R² | **0.88** | The model explained about 88% of the differences in electricity access found in the validation data. |
| Average error | **5.63 percentage points** | A typical prediction was about 5.6 percentage points away from the real value. |

![Real values compared with model predictions]({{ '/assets/images/actual-vs-predicted.png' | relative_url }})

Most points are close to the diagonal line. This means that many model predictions were reasonably close to the real values.

### What this means

The model could be useful as a **supporting tool**.

For example, an organization could use it to:

- compare countries;
- identify unusual results;
- support early planning;
- decide where a closer investigation may be needed.

However, the model should not replace official statistics or local knowledge.

An average error of around 5.6 percentage points can still be important, especially when decisions affect budgets, infrastructure projects, or vulnerable communities.

## Question 3: How could electricity access change in a future scenario?

### How I answered the question

I created a simple five-year scenario for India.

In this scenario, internet usage, education, mobile access, and urbanization gradually improved. The model then estimated the electricity access level connected with those assumptions.

![Example future scenario for India]({{ '/assets/images/india-forecast.png' | relative_url }})

The model estimates increased from about **86.3% in 2017** to about **96.8% in 2021**.

### What this means

This example shows how a model can be used to explore a “what if” question:

> **What might the model expect if several development indicators continued to improve?**

This result is not an official forecast and should not be treated as a verified historical estimate.

It is only a scenario based on:

- patterns found in the 2007–2016 dataset;
- assumed improvements in selected indicators;
- the behavior of the trained model.

Real electricity access can also be affected by government policy, conflict, investment, geography, fuel prices, natural disasters, and many other factors that are not included here.

## How the project was completed

The project followed the CRISP-DM process, which is a common framework for data science projects.

In practical terms, the work included:

1. defining the questions;
2. understanding the World Bank data;
3. cleaning and preparing the data;
4. comparing several machine learning models;
5. evaluating the best model;
6. explaining the results for non-technical readers.

Missing numeric values were filled using the median value. The final model was a tuned Random Forest regressor.

## Main findings

The analysis produced three main findings:

1. **Electricity access is strongly connected with wider development.**  
   Internet use, education, mobile connectivity, and urbanization were the strongest indicators in this project.

2. **The model produced useful estimates.**  
   It explained about 88% of the differences in the validation data, with an average error of around 5.6 percentage points.

3. **Scenario analysis can support discussion, but it is not a guaranteed forecast.**  
   The India example shows how the model can explore possible outcomes under selected assumptions.

## Recommendations

### For governments and policymakers

Consider electricity access together with education, digital infrastructure, and local economic development.

### For development organizations

Use the model to support early screening and prioritization, but confirm the results with recent local data before making funding decisions.

### For analysts

Update the project with newer data, compare different regions separately, and check whether the model performs equally well in countries with low and high electricity access.

## Limitations

This project has several important limitations:

- The dataset covers **2007–2016**, so it does not show current conditions.
- The model finds patterns, but it does not prove cause and effect.
- Country-level averages can hide large differences between cities and rural areas.
- Filling missing values with the median simplifies the data.
- The future scenario is not a formal time-series forecast.
- Important events such as conflict, policy reform, economic crisis, or major infrastructure investment were not modeled directly.

## Conclusion

The project shows that access to electricity is closely linked with broader social and technological development.

Internet usage, secondary education, mobile connectivity, and urbanization were the strongest predictors in the analysis.

The machine learning model produced useful estimates, but its role should be to support decisions rather than replace official data or expert knowledge.

The most important lesson is that improving electricity access may require more than building energy infrastructure. Progress is often connected with education, communications, economic development, and the wider conditions in which people live.

## Project files and acknowledgements

The complete technical analysis is available in the project files:

- [Project notebook]({{ '/Project.ipynb' | relative_url }})
- [Project README]({{ '/README.md' | relative_url }})
- [Python requirements]({{ '/requirements.txt' | relative_url }})

The data was obtained from the World Bank World Development Indicators.

This independent educational project was completed as part of the Udacity Data Scientist Nanodegree project framework.
