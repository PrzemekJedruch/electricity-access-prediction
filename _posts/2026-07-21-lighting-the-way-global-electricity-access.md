---
layout: post
title: "Lighting the Way: What Machine Learning Reveals About Global Electricity Access"
date: 2026-07-21
author: Przemysław Jędruch
categories: [data-science, machine-learning]
tags: [electricity-access, world-bank, random-forest, shap]
---

Electricity is more than an infrastructure service. It supports education, healthcare, communication, business activity, and everyday quality of life. Yet access remains uneven across countries.

This project uses World Bank development indicators from 2007–2016 to investigate which socioeconomic and technological factors are most closely associated with electricity access, how accurately access can be predicted, and how a model can be used to explore possible future scenarios.

![Development indicators correlated with electricity access]({{ '/assets/images/correlation-with-target.png' | relative_url }})

*The strongest correlations with electricity access were observed for internet usage, secondary school enrollment, mobile subscriptions, and urban population.*

## The business problem

Policymakers and development organizations need to understand where limited electricity access is likely to persist and which broader development conditions tend to accompany improvement.

The analysis therefore addresses three practical business questions:

1. **Which factors are most strongly associated with electricity access across countries?**
2. **How accurately can electricity access be predicted using socioeconomic and technological indicators?**
3. **How might electricity access change under a simple future-development scenario?**

The corresponding solutions combine exploratory analysis, a Random Forest regression model, feature importance, SHAP interpretation, and scenario-based prediction.

## Question 1: Which factors matter most?

### Solution

I first calculated correlations between each numeric indicator and electricity access. The strongest positive relationships were:

- **Internet usage:** 0.67
- **Secondary school enrollment:** 0.64
- **Mobile cellular subscriptions:** 0.63
- **Urban population:** 0.62

These results indicate that countries with stronger digital connectivity, educational participation, and urban development also tend to have higher electricity access.

Correlation alone does not show causation, so I also examined feature importance from the Random Forest model.

![Random Forest feature importance]({{ '/assets/images/feature-importance.png' | relative_url }})

Internet usage contributed the largest share of the model's predictive importance. Urban population, secondary school enrollment, and mobile subscriptions were also influential.

SHAP analysis provided an additional consistency check by showing how feature values affected individual predictions.

![SHAP summary plot]({{ '/assets/images/shap-summary.png' | relative_url }})

### What this means for stakeholders

Electricity access should not be treated as an isolated engineering problem. The findings suggest that energy expansion is closely connected with digital inclusion, education, and urban development.

For policymakers and development organizations, this supports a coordinated approach: energy infrastructure programs may be more effective when considered alongside investments in schools, communications, and local economic development.

These relationships are statistical associations, not proof that increasing one indicator will directly cause electricity access to rise.

## Question 2: Can electricity access be predicted accurately?

### Solution

A Random Forest regression model was trained using internet usage, secondary school enrollment, mobile subscriptions, and urban population.

On the validation dataset, the model achieved:

| Metric | Result | Practical interpretation |
|---|---:|---|
| R² | **0.88** | The model explained about 88% of the observed variation in electricity access. |
| Mean Absolute Error | **5.63 percentage points** | A typical prediction differed from the observed value by about 5.63 points. |

![Actual versus predicted electricity access]({{ '/assets/images/actual-vs-predicted.png' | relative_url }})

Most predictions followed the ideal prediction line reasonably closely, although larger errors remained for some observations.

### What this means for stakeholders

The model is accurate enough to support **screening, prioritization, and exploratory planning**. For example, an organization could use it to identify countries whose predicted electricity access appears unusually low relative to their broader development indicators.

It should not replace official measurement or local field data. A five-to-six percentage point error can still be important when programs, budgets, or vulnerable populations are being evaluated.

## Question 3: How might access change in a future scenario?

### Solution

To demonstrate a possible planning use case, I created a five-year scenario for India following the final year of the dataset.

The values of selected predictors were gradually increased, and the trained model was used to estimate electricity access under those assumptions.

![Scenario-based electricity access estimates for India]({{ '/assets/images/india-forecast.png' | relative_url }})

The estimated values increased from approximately **86.3% in 2017** to **96.8% in 2021**.

### What this means for stakeholders

The scenario shows how a predictive model can support discussions about possible development paths. It can help stakeholders test questions such as:

> What level of electricity access would the model expect if digital connectivity, education, mobile access, and urbanization continued to improve?

This is **not a formal time-series forecast** and should not be interpreted as a verified historical estimate or a current prediction. It is an illustrative scenario based on simplified assumptions and patterns learned from the 2007–2016 data.

## How the analysis was built

The project followed the CRISP-DM process:

1. **Business understanding:** define decision-oriented questions.
2. **Data understanding:** inspect World Bank country-level indicators.
3. **Data preparation:** reshape the data into country-year observations and handle missing numeric values with median imputation.
4. **Modeling:** train and tune a Random Forest regressor.
5. **Evaluation:** assess R², Mean Absolute Error, prediction plots, feature importance, and SHAP values.
6. **Communication:** translate results into stakeholder implications and limitations.

## Recommendations

### For policymakers

Coordinate electricity expansion with education, digital connectivity, and urban-development initiatives rather than treating these areas as unrelated programs.

### For development organizations

Use predictive models as an early-warning or prioritization tool, then validate model signals with recent local data before allocating resources.

### For analysts

Update the dataset with newer years, examine regional models, test alternative missing-data strategies, and evaluate performance separately for low-access and high-access countries.

## Limitations

The analysis has several important limitations:

- The data covers **2007–2016**, so it does not represent current conditions.
- Missing numeric values were filled using median imputation, which simplifies differences between countries.
- Statistical relationships do not establish causation.
- Country-level data can hide major regional and local inequalities.
- The India projection is scenario-based rather than a formal time-series forecast.
- Policy changes, conflict, economic shocks, and major infrastructure investments are not explicitly modeled.

## Conclusion

The analysis shows that electricity access is strongly connected with broader development patterns. Internet usage, secondary education, mobile connectivity, and urbanization consistently appeared as the most informative predictors.

The Random Forest model achieved strong validation performance, demonstrating that machine learning can provide useful estimates and decision-support signals. Its greatest value is not in replacing official statistics, but in helping stakeholders identify patterns, compare scenarios, and decide where deeper investigation may be needed.

## Project files and acknowledgements

The complete analysis is available in the project notebook and repository documentation:

- [Project notebook]({{ '/Project.ipynb' | relative_url }})
- [Project README]({{ '/README.md' | relative_url }})
- [Python requirements]({{ '/requirements.txt' | relative_url }})

Data was obtained from the World Bank World Development Indicators. This independent educational project was completed as part of the Udacity Data Scientist Nanodegree project framework.
