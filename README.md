# CharityML Donor Outreach Optimization

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikitlearn&logoColor=white)

A supervised learning project that predicts whether an individual earns more than $50,000/year using U.S. census data, helping CharityML prioritize donor outreach.

## Project Overview

Charity outreach campaigns are expensive when sent broadly. This project builds and tunes a binary classifier to identify high-income individuals (income >50K), who are more likely to donate.

This work is based on the Finding Donors for CharityML project from the Udacity Data Scientist Nanodegree, with custom analysis, model comparison, and optimization steps.

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

## Reproducibility Notes

- Random seeds are set where appropriate (for example, model initialization and train/test split) to improve reproducibility.
- Results can vary slightly depending on package versions.

## Future Improvements

- Add a standalone training script (CLI) outside the notebook
- Export and version the best model artifact
- Add SHAP-based explainability for donor targeting transparency
- Track experiments with MLflow or Weights & Biases

## Acknowledgment

This project is based on the Finding Donors for CharityML project from the Udacity Data Scientist Nanodegree. Appreciation to Udacity for the original project structure and learning framework that guided this work.

## License

This repository is for educational purposes. Dataset and project framing follow the original sources listed above.
