# 🤖 DevelopersHub Corporation — AI/ML Engineering Internship Tasks

**Intern:** Saif Ullah  
**Organization:** DevelopersHub Corporation  
**Domain:** Artificial Intelligence

---

## Task 1 — Exploring & Visualizing a Dataset

### 🎯 Objective
Perform comprehensive exploratory data analysis (EDA) on a structured dataset to understand its shape, distributions, correlations, and class separability through statistical summaries and rich visualizations.

### 📦 Dataset
| Property | Details |
|---|---|
| Name | Iris Dataset |
| Source | Seaborn built-in (`sns.load_dataset('iris')`) |
| Size | 150 samples × 5 features |
| Features | `sepal_length`, `sepal_width`, `petal_length`, `petal_width`, `species` |
| Classes | 3 species — *setosa*, *versicolor*, *virginica* |

### 🛠️ Models / Techniques Applied
- No predictive model — purely analytical and visual exploration
- Tools used: `pandas` for data inspection, `matplotlib` & `seaborn` for visualization (histograms, pair plots, heatmaps, box plots)

### 📊 Key Results & Findings
- Dataset is **complete with no missing values** (150 non-null entries across all columns)
- **Petal length and petal width** are the most discriminative features — *setosa* is clearly separable from the other two species
- **Sepal width** shows the most overlap between species, making it the weakest standalone predictor
- Strong positive correlation exists between petal length and petal width
- The dataset is **perfectly balanced** with 50 samples per class

---

## Task 2 — Stock Price Prediction

### 🎯 Objective
Build and compare machine learning regression models to predict the **next-day closing price** of Amazon (AMZN) stock using historical OHLCV (Open, High, Low, Close, Volume) data as features.

### 📦 Dataset
| Property | Details |
|---|---|
| Ticker | Amazon (AMZN) |
| Source | Yahoo Finance via `yfinance` API |
| Size | 502 trading days (~Feb 2024 – Feb 2026) |
| Features | `Open`, `High`, `Low`, `Close`, `Volume` |
| Target | Next-day `Close` price |
| Train / Test Split | 400 / 101 samples |

### 🛠️ Models Applied
- **Linear Regression** — baseline model capturing linear trends
- **Random Forest Regressor** — ensemble model capturing non-linear patterns

### 📊 Key Results & Findings

| Metric | Linear Regression | Random Forest |
|---|---|---|
| MAE | **$3.43** | $4.77 |
| RMSE | **$4.70** | $6.72 |
| R² Score | **0.8651** | 0.7242 |

- **Linear Regression outperformed Random Forest** on this task, achieving an R² of **0.87**, indicating it captured ~87% of the variance in stock prices
- The models predicted a next-day closing price of **$207.81** (LR) and **$210.28** (RF), with an ensemble average of **$209.05** (vs. actual close of $210.00)
- Stock price data exhibited a strong linear trend over the short term, which explains why the simpler linear model performed better

---

## Task 3 — Heart Disease Prediction

### 🎯 Objective
Develop a binary classification system to predict the **presence or absence of heart disease** in a patient based on clinical measurements, and identify the most influential diagnostic features.

### 📦 Dataset
| Property | Details |
|---|---|
| Name | Cleveland Heart Disease Dataset |
| Source | UCI Machine Learning Repository |
| Size | 303 patients × 14 features |
| Key Features | `age`, `sex`, `chest pain type (cp)`, `resting BP`, `cholesterol`, `thalassemia (thal)`, `max heart rate`, `ST depression`, etc. |
| Target | Binary — `0` = No Disease, `1` = Disease |
| Train / Test Split | 242 / 61 patients |

### 🛠️ Models Applied
- **Logistic Regression** — probabilistic linear classifier
- **Decision Tree Classifier** — rule-based non-linear classifier

### 📊 Key Results & Findings

| Metric | Logistic Regression | Decision Tree |
|---|---|---|
| Accuracy | **86.89%** | 78.69% |
| AUC-ROC | **0.9524** | 0.8047 |
| F1-Score (Disease) | **0.87** | 0.79 |

- **Logistic Regression is the best model**, achieving **86.89% accuracy** and an outstanding AUC-ROC of **0.9524**
- Top 5 most important features for predicting heart disease (by Decision Tree importance):

  | Rank | Feature | Importance |
  |---|---|---|
  | 1 | `thal` (Thalassemia type) | 0.379 |
  | 2 | `cp` (Chest pain type) | 0.152 |
  | 3 | `ca` (Major vessels colored by fluoroscopy) | 0.117 |
  | 4 | `age` | 0.093 |
  | 5 | `chol` (Cholesterol) | 0.082 |

- Logistic Regression achieved **93% precision** for healthy patients and **81% precision** for diseased patients
- Thalassemia type (`thal`) and chest pain type (`cp`) are by far the strongest clinical predictors of heart disease

---

## Task 6 — House Price Prediction

### 🎯 Objective
Predict **median house values** for California districts using demographic and geographic features, and identify the key factors that drive property prices.

### 📦 Dataset
| Property | Details |
|---|---|
| Name | California Housing Dataset |
| Source | Scikit-learn / StatLib Repository |
| Size | 20,640 districts × 10 features |
| Key Features | `longitude`, `latitude`, `housing_median_age`, `total_rooms`, `total_bedrooms`, `population`, `households`, `median_income`, `ocean_proximity` |
| Target | `median_house_value` (range: $14,999 – $500,001, avg: $206,856) |
| Train / Test Split | 16,512 / 4,128 samples |

### 🛠️ Models Applied
- **Linear Regression** — baseline linear model
- **Gradient Boosting Regressor** — powerful ensemble of decision trees
- **Feature Engineering:** Created 3 derived features — `rooms_per_household`, `bedrooms_per_room`, `population_per_household`
- **Preprocessing:** StandardScaler normalization + One-hot encoding of `ocean_proximity`

### 📊 Key Results & Findings

| Metric | Linear Regression | Gradient Boosting |
|---|---|---|
| MAE | $50,888.66 | **$32,556.53** |
| RMSE | $72,668.54 | **$49,085.66** |
| R² Score | 0.5970 | **0.8161** |

- 🏆 **Gradient Boosting is the best model**, achieving an R² of **0.8161** — explaining ~82% of house price variance
- Top drivers of house prices:

  | Rank | Feature | Importance |
  |---|---|---|
  | 1 | `median_income` | 0.530 |
  | 2 | `ocean_proximity_INLAND` | 0.150 |
  | 3 | `population_per_household` | 0.116 |
  | 4 | `longitude` | 0.065 |
  | 5 | `latitude` | 0.061 |

- **Median income** is overwhelmingly the single strongest predictor of house prices (53% importance)
- Houses near the ocean command significantly higher prices than inland properties
- Gradient Boosting reduced prediction error by **36%** over Linear Regression (MAE: $32K vs $50K)
---

> 📌 *All tasks were completed as part of the AI/ML Engineering Internship at **DevelopersHub Corporation**.*
