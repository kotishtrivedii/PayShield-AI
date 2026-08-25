# 🛡️ PayShield AI — Intelligent Payment Risk & Fraud Detection System

An explainable payment-risk intelligence system that combines a supervised fraud
classifier (Random Forest), an unsupervised anomaly detector (Isolation Forest),
rule-based behavioral scoring, and SHAP-based explainability into a single 0–100
risk score with an action recommendation.

## Files

| File | Purpose |
|---|---|
| `PayShield_AI.ipynb` | Full pipeline — open in Google Colab and run top to bottom. Generates a realistic synthetic dataset, trains both models, builds the risk engine, runs SHAP, and includes a manual transaction simulator. |
| `app.py` | Streamlit dashboard — loads the models saved by the notebook and lets you analyze transactions interactively. |
| `requirements.txt` | Python dependencies. |

## How to run

### 1. Notebook (Google Colab)
1. Upload `PayShield_AI.ipynb` to [Google Colab](https://colab.research.google.com/).
2. Run all cells (**Runtime → Run all**). No setup needed — the dataset is generated in Section 2.
3. Section 13 saves the trained models (`.pkl` files) and a scored dataset (`.csv`) to the Colab file system. Download them (or mount Google Drive) before your Colab session ends.

### 2. Dashboard (local)
```bash
pip install -r requirements.txt
# Place the .pkl files and payshield_scored_transactions.csv from step 1 next to app.py
streamlit run app.py
```

## Using a real dataset instead of synthetic data

Section 2 of the notebook explains exactly which columns are required. Replace the
data-generation cell with:
```python
df = pd.read_csv("/content/your_file.csv")
```
Every other cell (feature engineering, models, risk engine, SHAP, simulator) works
unchanged as long as the required columns are present. Good public sources: Kaggle's
"Credit Card Fraud Detection" dataset or the IEEE-CIS Fraud Detection dataset.

## Risk engine

```
Combined Risk Score = 0.45 × (Random Forest fraud probability)
                     + 0.30 × (Isolation Forest anomaly score)
                     + 0.25 × (rule-based behavioral score)

0–30   → LOW      → APPROVE
31–70  → MEDIUM   → ADDITIONAL VERIFICATION
71–100 → HIGH     → MANUAL REVIEW (or TEMPORARILY BLOCK if score ≥ 95)
```

## Suggested repo structure for GitHub

```text
payshield-ai/
├── README.md
├── notebooks/
│   └── PayShield_AI.ipynb
├── app.py
├── requirements.txt
└── .gitignore
```
