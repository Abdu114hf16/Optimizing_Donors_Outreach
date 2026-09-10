# CharityML Donor Outreach Optimization

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)

A supervised learning project that predicts whether an individual earns more than $50,000/year using U.S. census data, helping CharityML prioritize donor outreach.

## Project Overview

Charity outreach campaigns are expensive when sent broadly. Charity is a fictitious charity organization located in the heart of Silicon Valley. With advanced statistical methods, CharityML has decided to send letters only pepole with +50K income those who most likely to donate to the charity. This project explores analyze and explore correlations and distributions of dataset variables. Compare candidate Machine Learning models and tunes/optimize the best model (AdaBoost) to binary classify to identify high-income individuals (income >50K), who are more likely to donate.

## Repository Structure

- `finding_donors.ipynb` - Complete notebook with analysis, feature engineering, model training, tuning, and conclusions.
- `finding_donors_report.html` - Exported HTML report version of the final notebook.
- `census.csv` - Input dataset used for training and evaluation.
- `visuals.py` - Helper plotting utilities used by the notebook.

## Problem Statement

Given demographic and employment features, predict whether income is above $50K.

- Type: Binary classification
- Positive class: `>50K`
- Business goal: Improve precision-focused donor targeting for cost-effective outreach

## Dataset

The modified census dataset contains around 32,000 records and 13 features.

Examples of features:
- age
- workclass
- education_level
- occupation
- hours-per-week
- native-country

Target variable:
- income (`<=50K` or `>50K`)

Source references:
- UCI Adult Census Income dataset
- Kohavi, "Scaling Up the Accuracy of Naive-Bayes Classifiers: a Decision-Tree Hybrid"

## Methods

Main pipeline in the notebook:

1. Data loading and exploration
2. Skew handling with log transforms
3. One-hot encoding for categorical variables
4. Train/test split and feature scaling
5. Baseline comparison against a naive predictor
6. Training multiple candidate models
7. Selection of AdaBoost as the best tradeoff
8. Hyperparameter tuning with GridSearchCV and F-beta scorer (beta = 0.5)

## Model Results

From the notebook's final evaluation:

- Unoptimized model:
  - Accuracy: 0.8483
  - F-score: 0.7029
- Optimized model:
  - Accuracy: 0.8568
  - F-score: 0.7223

The tuned model improves precision-oriented performance, which better aligns with CharityML's outreach cost constraints.

## Requirements

- Python 3.9+
- Jupyter Notebook / JupyterLab
- numpy
- pandas
- scikit-learn
- matplotlib

Install dependencies:

```bash
pip install -r requirements.txt
```

## How to Run

1. Clone this repository.
2. Move into the project folder.
3. Launch Jupyter and open the notebook.

```bash
jupyter notebook finding_donors.ipynb
```

## Acknowledgment

This project is based on the Finding Donors for CharityML project from the Udacity Data Scientist Nanodegree. Appreciation to Udacity for the original project structure and learning framework that guided this work.

## Reproducibility

`requirements.txt` pins the dependencies and `census.csv` is included, so the
notebook runs end to end without external downloads. The split is seeded and
the reported accuracy and F0.5 figures reproduce.

## Why F0.5 rather than accuracy

The two mistakes do not cost the same. A false positive spends a letter, an
envelope and a follow-up on someone who was never going to give; a false
negative misses a prospect. When the campaign budget is the binding constraint,
the first is the cost being managed, so precision is weighted twice as heavily
as recall. That is exactly what F-beta with beta = 0.5 does. It was chosen
before the models were run.

## Limitations and responsible use

- **Income is a proxy for capacity, not a record of anyone donating.** The
  target is a census income threshold. The model ranks predicted earnings, and
  treating that ranking as generosity is a leap the data cannot support.
- Demographic targeting can reinforce historical inequities. A real deployment
  would need consent, fairness analysis across the protected attributes present
  in the data, and policy review before it touched a live list.
- The model outputs a score, not a calibrated probability. Any contact
  threshold would need to be set and reviewed deliberately.
- The exercise ends at model selection. It was never evaluated against real
  campaign outcomes, which is the only test that would show whether the ranking
  works.
- **Guided project.** The dataset, framing and objective come from Udacity's
  CharityML exercise; the analysis and implementation are mine.

## Case study

A full write-up: the business question, the method, the evidence, and what the
result does not support.

<https://alshammari.dev/projects/optimizing-donor-outreach/>

## License

MIT. See [LICENSE](LICENSE).
