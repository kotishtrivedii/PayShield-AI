# 🛡️ PayShield AI

### Intelligent Payment Risk & Fraud Detection System

**Track:** Track 2 — AI Risk Manager

PayShield AI is an explainable payment-risk intelligence system designed to analyze transactions, identify suspicious behavioral patterns, calculate a **0–100 risk score**, explain the factors behind the decision, and recommend an appropriate action.

---

## 🚨 Problem Statement

Digital payments are increasing rapidly, but fraudulent and suspicious transactions remain a major challenge for payment platforms.

Traditional fraud detection systems often focus only on whether a transaction is fraudulent or legitimate. For a risk-management team, that is not enough.

A useful system should answer:

* How risky is this transaction?
* Why was it flagged?
* Which behavioral signals contributed to the risk?
* What action should be taken?

**PayShield AI** addresses these questions through behavioral risk analysis and explainable AI.

---

## 💡 Solution

PayShield AI analyzes multiple transaction signals, including:

* Transaction amount
* Customer's average transaction amount
* Failed payment attempts
* Transaction velocity
* Device changes
* Location changes
* Transaction time
* International transactions

These signals are combined into an intelligent risk engine that produces:

```text
Risk Score: 94/100

Risk Level: HIGH

Recommended Action:
MANUAL REVIEW / TEMPORARILY HOLD

Risk Factors:
• Transaction amount is significantly above normal
• New device detected
• Location anomaly detected
• Multiple failed attempts
• High transaction velocity
```

---

## 🎯 Key Features

### 🔢 Risk Scoring

Generates a risk score between **0 and 100**.

|  Score | Risk Level | Recommended Action             |
| -----: | ---------- | ------------------------------ |
|   0–39 | 🟢 Low     | Approve                        |
|  40–74 | 🟡 Medium  | Additional Verification        |
| 75–100 | 🔴 High    | Manual Review / Temporary Hold |

### 🔎 Behavioral Analysis

Analyzes transaction behavior rather than relying only on transaction amount.

### 📱 Device Risk

Detects whether the payment is coming from a new device.

### 📍 Location Anomaly

Identifies changes in the customer's usual transaction location.

### ⚡ Transaction Velocity

Detects unusually high numbers of transactions within a short period.

### 🔐 Failed Attempt Detection

Multiple failed payment attempts increase the transaction's risk score.

### 🌙 Time-Based Risk

Transactions during unusual hours can receive additional risk weight.

### 🤖 Explainable AI

Instead of simply returning:

> "Fraud detected."

PayShield AI explains **why the transaction is considered risky**.

---

## 🏗️ System Architecture

```text
                  ┌──────────────────────┐
                  │  Payment Transaction │
                  └──────────┬───────────┘
                             ↓
                  ┌──────────────────────┐
                  │ Transaction Signals  │
                  │                      │
                  │ Amount               │
                  │ Device               │
                  │ Location             │
                  │ Velocity             │
                  │ Failed Attempts      │
                  │ Time                 │
                  └──────────┬───────────┘
                             ↓
                  ┌──────────────────────┐
                  │ Behavioral Risk      │
                  │ Analysis             │
                  └──────────┬───────────┘
                             ↓
                  ┌──────────────────────┐
                  │    Risk Engine       │
                  │      0–100           │
                  └──────────┬───────────┘
                             ↓
             ┌───────────────┴───────────────┐
             ↓                               ↓
    ┌──────────────────┐            ┌──────────────────┐
    │ Risk Level       │            │ Risk Explanation │
    │                  │            │                  │
    │ LOW              │            │ Why flagged?     │
    │ MEDIUM           │            │ Risk factors     │
    │ HIGH             │            │ Behavior         │
    └────────┬─────────┘            └────────┬─────────┘
             └───────────────┬───────────────┘
                             ↓
                  ┌──────────────────────┐
                  │ Recommended Action   │
                  │                      │
                  │ APPROVE              │
                  │ VERIFY               │
                  │ REVIEW / HOLD        │
                  └──────────┬───────────┘
                             ↓
                  ┌──────────────────────┐
                  │ Streamlit Dashboard  │
                  └──────────────────────┘
```

---

## 🧠 Risk Engine

PayShield combines multiple behavioral signals.

### Transaction Amount

The current transaction is compared with the customer's normal transaction amount.

Example:

```text
Customer Average: ₹4,200
Current Transaction: ₹45,000

Amount Ratio: 10.7×
```

A large deviation increases the risk score.

### Failed Attempts

Repeated failed transactions can indicate suspicious activity.

```text
0–1 attempts  → Low impact
2–3 attempts  → Moderate impact
4+ attempts   → High impact
```

### Transaction Velocity

A sudden increase in transaction frequency can indicate abnormal activity.

```text
Normal:
1–2 transactions/hour

Suspicious:
7+ transactions/hour
```

### New Device

A transaction from a previously unseen device receives additional risk weight.

### Location Change

A transaction from an unusual location can increase the risk score.

### Unusual Transaction Time

Transactions during unusual hours receive additional risk weight.

---

## 🖥️ Streamlit Dashboard

The interactive dashboard allows a user to enter transaction information and immediately receive a risk assessment.

### Input Parameters

```text
Transaction Amount
Customer Average Amount
Failed Attempts
Transactions in Last Hour
Device
Location
Transaction Hour
International Transaction
```

### Output

```text
Risk Score
Risk Level
Recommended Action
Risk Factors
Transaction Summary
AI Risk Explanation
```

---

## 🧪 Example

### Input

```text
Transaction Amount: ₹45,000
Customer Average: ₹4,200
Failed Attempts: 4
Transactions in Last Hour: 7
Device: New Device
Location: New Location
Transaction Hour: 02:00
International: No
```

### Output

```text
🚨 HIGH RISK

Risk Score: 100/100

Recommended Action:
MANUAL REVIEW / TEMPORARILY HOLD

Risk Factors:
✓ Transaction amount significantly above average
✓ Multiple failed attempts
✓ High transaction velocity
✓ New device detected
✓ Location anomaly detected
✓ Unusual transaction hour
```

---

## 🛠️ Technology Stack

| Component            | Technology                       |
| -------------------- | -------------------------------- |
| Programming Language | Python                           |
| Development          | Google Colab                     |
| Data Processing      | Pandas, NumPy                    |
| Machine Learning     | Scikit-learn                     |
| Classification       | Random Forest                    |
| Anomaly Detection    | Isolation Forest                 |
| Explainability       | SHAP                             |
| Visualization        | Plotly, Matplotlib               |
| Frontend             | Streamlit                        |
| Backend              | FastAPI                          |
| Database             | SQLite / PostgreSQL              |
| Model Storage        | Joblib                           |
| Version Control      | Git + GitHub                     |
| Deployment           | ngrok / Streamlit Cloud / Render |

---

## 📁 Project Structure

```text
payshield-ai/
│
├── README.md
│
├── app.py
│
├── notebooks/
│   └── PayShield_AI.ipynb
│
├── models/
│   ├── payshield_model.pkl
│   └── scaler.pkl
│
├── src/
│   ├── preprocessing.py
│   ├── features.py
│   ├── risk_engine.py
│   └── explainability.py
│
├── data/
│   └── README.md
│
├── requirements.txt
│
└── .gitignore
```

---

## 🚀 Running the Project

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/payshield-ai.git
cd payshield-ai
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run Streamlit

```bash
streamlit run app.py
```

The application will be available locally at:

```text
http://localhost:8501
```

---

## ☁️ Google Colab + ngrok

The prototype can also be run directly from Google Colab.

Install dependencies:

```python
!pip install streamlit pyngrok
```

Then start Streamlit and expose port `8501` through ngrok.

> **Security:** Never commit your ngrok authentication token to GitHub or expose it in a public notebook.

---

## 📊 Machine Learning Approach

The planned ML architecture contains two complementary approaches.

### Supervised Detection

**Random Forest Classifier**

Used to learn patterns from historical transactions labeled as legitimate or fraudulent.

```text
Historical Transactions
          ↓
Feature Engineering
          ↓
Random Forest
          ↓
Fraud Probability
```

### Unsupervised Detection

**Isolation Forest**

Used to identify unusual transactions that differ significantly from normal behavior.

```text
Transaction Features
          ↓
Isolation Forest
          ↓
Anomaly Score
```

### Combined Risk Engine

```text
Fraud Probability
        +
Anomaly Score
        +
Behavioral Signals
        ↓
Final Risk Score
```

---

## 🔍 Explainability

A major objective of PayShield AI is **explainable risk detection**.

The system should not only identify suspicious transactions but also provide understandable reasons.

Example:

```text
Risk Score: 91/100

Top Risk Factors:

1. Transaction amount is unusually high
2. New device detected
3. Multiple failed attempts
4. Unusual location
5. High transaction velocity
```

SHAP can later be integrated with the trained ML model to provide model-level feature contributions.

---

## 🎯 Recommended Actions

PayShield AI converts the risk assessment into an operational recommendation.

### 🟢 Low Risk

```text
Risk Score: 18

Action:
APPROVE
```

### 🟡 Medium Risk

```text
Risk Score: 58

Action:
ADDITIONAL VERIFICATION
```

### 🔴 High Risk

```text
Risk Score: 91

Action:
MANUAL REVIEW / TEMPORARILY HOLD
```

---

## 🔐 Security Considerations

PayShield AI is a prototype for educational and demonstration purposes.

For a production deployment:

* Never expose API keys or authentication tokens.
* Use environment variables for secrets.
* Encrypt sensitive transaction information.
* Implement authentication and authorization.
* Maintain audit logs.
* Apply rate limiting.
* Validate all transaction inputs.
* Follow applicable financial-data and privacy regulations.
* Do not automatically block legitimate customers solely based on an ML prediction.

---

## ⚠️ Disclaimer

PayShield AI is a **prototype risk-analysis system** and is not intended to make autonomous real-world financial decisions.

The risk score and recommendations are demonstrations of an AI-assisted risk-management workflow and should be validated extensively before any production use.

---

## 🌟 Future Improvements

* Real-time transaction streaming
* PostgreSQL integration
* FastAPI backend
* Real fraud datasets
* Advanced feature engineering
* SHAP-based explanations
* XGBoost comparison
* Real-time anomaly monitoring
* Risk analyst dashboard
* Transaction history
* Alert management
* Human-in-the-loop review
* Model monitoring and drift detection
* Authentication and role-based access
* Production cloud deployment

---

## 🏆 Project Objective

PayShield AI aims to demonstrate how **machine learning, behavioral analytics, anomaly detection, and explainable AI** can work together to support payment-risk teams.

The core workflow is:

```text
Transaction
     ↓
Behavior Analysis
     ↓
ML + Anomaly Detection
     ↓
Risk Score
     ↓
Explainability
     ↓
Recommended Action
     ↓
Human Review
```

---

## 👨‍💻 Author

**Kotish Trivedi**

B.Tech Computer Science Engineering — Data Science

---

## 📜 License

This project is intended for educational, experimental, and hackathon purposes.

Add an appropriate open-source license before distributing the project publicly.
