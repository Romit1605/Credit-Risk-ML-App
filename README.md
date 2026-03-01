<div align="center">

# 💳 Credit Risk ML App

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-RandomForest-orange?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![License](https://img.shields.io/badge/License-Educational-green)](LICENSE)
[![CLI](https://img.shields.io/badge/Interface-CLI-lightgrey?logo=gnometerminal)]()

> **Predict loan default risk from the command line — fast, modular, and production-ready in structure.**

</div>

---

## 📌 What This Project Does

This is a **CLI-driven machine learning pipeline** that classifies loan applicants as *default* or *non-default* using a tuned Random Forest Classifier trained on real-world financial data. It is designed with a clean, modular architecture to make extending or deploying the model straightforward.

---

## ✨ Key Features

| Feature | Details |
|---|---|
| **CLI Interface** | Train and predict entirely from the terminal |
| **Preprocessing** | Median imputation for missing values, robust to outliers |
| **Class Imbalance Handling** | Balanced class weights — model focuses on catching defaulters |
| **Cross-Validation** | K-Fold CV for reliable model evaluation |
| **Hyperparameter Tuning** | Grid/Random search support via `tune.py` |
| **Artifact Management** | Trained model, scaler, and feature list persisted to disk |
| **Configurable** | All key settings managed via `config/config.yaml` |
| **Logging** | Structured logs at every pipeline stage |

---

## 🗂️ Project Structure

```
Credit-Risk-ML-App/
│
├── src/
│   ├── main.py                    # CLI entry point (--train / --predict)
│   ├── config/
│   │   └── config.yaml            # Central configuration file
│   ├── data/
│   │   ├── load_data.py           # Dataset ingestion
│   │   └── preprocess.py          # Feature engineering & imputation
│   ├── models/
│   │   ├── pipeline.py            # sklearn pipeline construction
│   │   ├── train.py               # Model training logic
│   │   ├── evaluate.py            # Metrics computation
│   │   ├── cross_validation.py    # K-Fold CV runner
│   │   └── tune.py                # Hyperparameter search
│   ├── pipeline/
│   │   ├── training_pipeline.py   # End-to-end training orchestration
│   │   └── prediction_pipeline.py # End-to-end inference orchestration
│   └── utils/
│       ├── logger.py              # Logging setup
│       └── save_artifacts.py      # Model & artifact persistence
│
├── data/
│   ├── exploration.ipynb          # EDA notebook
│   └── sample_input.csv           # Sample prediction input
├── artifacts/
│   └── metrics/
│       └── metrics.json           # Saved evaluation results
├── tests/
│   ├── test_data.py
│   └── test_train.py
├── requirements.txt
└── run_training.sh                # One-shot: run tests + train
```

---

## 🚀 Getting Started

### Prerequisites

- Python **3.8** or higher
- `pip`

### 1 — Clone & Install

```bash
git clone https://github.com/Romit1605/Credit-Risk-ML-App.git
cd Credit-Risk-ML-App

python -m venv venv
# Windows
venv\Scripts\activate
# macOS / Linux
source venv/bin/activate

pip install -r requirements.txt
```

### 2 — Get the Dataset

Download the [Kaggle Credit Risk Dataset](https://www.kaggle.com/datasets/laotse/credit-risk-dataset) and place the file:

```
data/credit_risk_dataset.csv
```

---

## 🖥️ Usage

### Train the model
```bash
python -m src.main --train
```

### Predict on new data
```bash
python -m src.main --predict data/sample_input.csv
```

### Run tests then train (recommended first run)
```bash
bash run_training.sh
```

---

## 📊 Model Performance

| Metric | Score |
|---|---|
| **Accuracy** | 88.4% |
| **Precision** (default class) | 72.0% |
| **Recall** (default class) | 77.2% |
| **F1 Score** (default class) | 74.5% |

> Metrics saved automatically to `artifacts/metrics/metrics.json` after every training run.

---

## 🔧 Technical Highlights

- **Median imputation** — robust to the heavy-tailed distributions common in loan data
- **Balanced class weights** — prevents the model from ignoring the minority (default) class
- **Identical transformations** — the trained scaler and feature list are persisted so prediction always mirrors training transforms exactly
- **Modular codebase** — data, models, and pipeline stages are fully decoupled for easy testing and extension

---

## 👤 Author

**Romit Patel**  
[GitHub](https://github.com/Romit1605)

---

## 📄 License

This project is intended for educational and portfolio demonstration purposes.