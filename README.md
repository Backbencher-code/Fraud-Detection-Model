# Fraud Detection Using Machine Learning

A machine learning project to detect fraudulent financial transactions using a Random Forest Classifier. Built on a real-world style dataset of mobile money transactions with over 1 million records.


---

## The problem

Fraud detection is fundamentally a class imbalance problem — less than 1% of transactions are fraudulent. A naive model that predicts "not fraud" for everything would still be 99% accurate but completely useless. The goal here was to build a model that actually catches fraud, which means optimizing for Recall rather than accuracy.

---

## Results

| Metric | Score |
|---|---|
| Fraud Recall | ~89% |
| ROC-AUC | ~0.99 |

The model correctly identifies approximately 89% of all fraudulent transactions while maintaining a strong ROC-AUC of 0.99.

---

## How it works

1. **EDA** — explored transaction types, amount distributions, and balance changes across fraud vs non-fraud cases
2. **Preprocessing** — dropped identifier columns (nameOrig, nameDest), label encoded transaction type
3. **Class imbalance** — handled using `class_weight='balanced'` in the classifier and `stratify=y` during train-test split
4. **Model** — Random Forest with 100 trees, max depth 10
5. **Evaluation** — confusion matrix, classification report, ROC-AUC score, and feature importance

---

## Key findings

The most important fraud predictors turned out to be:
- Sender's balance before and after the transaction
- Transaction type — fraud is almost exclusively in TRANSFER and CASH_OUT
- Transaction amount
- Transaction timing (step)

The built-in rule-based fraud flag (`isFlaggedFraud`) had near-zero importance, which shows that static threshold-based systems miss most fraud.

---

## Running the notebook

```bash
# Install dependencies
pip install numpy pandas matplotlib seaborn scikit-learn openpyxl

# Then open the notebook
jupyter notebook Fraud_detection_model.ipynb
```

Run all cells top to bottom. The notebook is fully commented so each step explains what is happening and why.

---

## Project structure

```
Fraud Detection/
├── Fraud_detection_model.ipynb   ← main notebook
├── Fraud.xlsx                    ← dataset (download separately from Kaggle)
└── README.md
```

---

## Tech stack

- Python, Pandas, NumPy
- Scikit-learn (RandomForestClassifier)
- Matplotlib, Seaborn
- Jupyter Notebook

---

## Author

Sahil Rohilla — [LinkedIn](https://linkedin.com/in/sahilrohilla) · [GitHub](https://github.com/Backbencher-code)
