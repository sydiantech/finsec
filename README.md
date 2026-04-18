# 🛡️ PhishGuard KE

**Real-time M-PESA phishing detector powered by machine learning.**

Paste any M-PESA SMS and instantly know if it's a scam — with a confidence score, risk level, and explanation in both English and Swahili.

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square)
![Streamlit](https://img.shields.io/badge/Streamlit-1.32-red?style=flat-square)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.4-orange?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 🚨 The Problem

M-PESA fraud costs Kenyans billions every year. Scammers send fake SMS messages impersonating Safaricom — fake prize wins, fake account suspensions, fake paybill requests. Ordinary users have no quick way to tell what's real.

## ✅ The Solution

PhishGuard KE uses a trained ML model to analyse any SMS in under a second and tells you exactly *why* it looks suspicious — in language Kenyans actually use.

---

## 🧠 How It Works

```
SMS Input → Text Cleaning → TF-IDF Vectorizer → Naive Bayes Classifier → Verdict + Confidence Score
```

**TF-IDF (Term Frequency–Inverse Document Frequency)**
Converts raw SMS text into numerical features. Words like "umeshinda" and "tuma haraka" score high because they appear almost exclusively in phishing messages.

**Multinomial Naive Bayes**
Calculates the probability the message is phishing based on learned word patterns. Outputs a label (phishing/legit) and a confidence percentage.

**Secondary Keyword Layer**
A bilingual keyword list (English + Swahili/Sheng) runs alongside the model to highlight the exact words that triggered the detection — making the result explainable to the user.

---

## ✨ Features

- Instant phishing / legit verdict with confidence score
- 🔴 HIGH / 🟡 MEDIUM / 🟢 SAFE risk levels
- Suspicious keyword highlighting
- Bilingual detection — English + Swahili + Sheng
- What to do / what NOT to do guidance
- Session dashboard — tracks messages checked and fraud rate
- Color-coded scan history table
- Pre-loaded sample messages for instant demo
- Safaricom & DCI Cyber Crime hotlines built in

---

## 🗂️ Project Structure

```
phishguard-ke/
├── app.py                  # Streamlit web application
├── train_model.py          # Model training script
├── requirements.txt        # Python dependencies
├── assets/
│   └── logob.png           # App logo
├── model/
│   └── phishing_model.pkl  # Trained model
├── data/
│   └── messages.csv        # Labelled SMS dataset
└── .streamlit/
    └── config.toml         # Theme configuration
```

---

## 🚀 Run Locally

```bash
# 1. Clone the repo
git clone https://github.com/yourusername/phishguard-ke.git
cd phishguard-ke

# 2. Create and activate virtual environment
python -m venv venv
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows

# 3. Install dependencies
pip install -r requirements.txt

# 4. Train the model
python train_model.py

# 5. Launch the app
streamlit run app.py
```

App runs at `http://localhost:8501`

---

## 📊 Dataset

Hybrid dataset combining:
- **Custom M-PESA samples** — manually authored Kenyan phishing messages in English and Swahili/Sheng covering fake prizes, paybill scams, account suspension threats, OTP theft, and doubling scams

Labels: `0` = legit, `1` = phishing / spam

---

## 🛠️ Stack

| Tool | Purpose |
|------|---------|
| Python | Core language |
| scikit-learn | TF-IDF vectorizer + Naive Bayes |
| Streamlit | Interactive web interface |
| pandas | Data loading and handling |
| joblib | Model serialization |

---

## 🇰🇪 Bilingual Fraud Detection

Catches scam patterns in both English and Swahili/Sheng:

**English:** `won`, `claim`, `urgent`, `suspended`, `verify`, `processing fee`, `guaranteed`, `100%`

**Swahili/Sheng:** `umeshinda`, `tuma haraka`, `mwisho wa leo`, `dharura`, `chap chap`, `bahati yako`, `imefungwa`, `thibitisha`, `uko lucky`, `chukua hii chance`

---

## 👥 Built By
 Amora And Ian at FinSec Cybersecurity Hackathon 2026, Nairobi Kenya .

**Report M-PESA scams:**
- Safaricom: **0722 000 100**
- DCI Cyber Crime: **0800 722 724**

---

## 📄 License

MIT — free to use, modify, and distribute.
