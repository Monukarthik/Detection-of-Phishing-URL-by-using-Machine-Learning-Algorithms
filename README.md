# Securing the Web: URL-Based Phishing Detection using Machine Learning

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Gradient%20Boosting-orange)](https://xgboost.readthedocs.io/)
[![Scikit-Learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikit-learn)](https://scikit-learn.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter)](https://jupyter.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Research Paper](https://img.shields.io/badge/Published-ICPCSN%202024-green)](https://github.com/Monukarthik/Securing-the-web-using-URL-based-analysis-and-Machine-Learning-Algorithms/blob/main/Research_Paper/Research_Paper.pdf)

> **Research published at the 5th International Conference on Pervasive Computing and Social Networking (ICPCSN 2024)**

---

## Overview

Phishing URLs are malicious web addresses that impersonate legitimate websites to steal credentials, financial data, or personally identifiable information (PII). This project builds and evaluates a **machine learning-based URL classification system** that detects phishing, malware, and defacement URLs from structural and lexical URL features alone — **no page content or DNS lookups required**.

The system classifies any URL as:
- ✅ **Legitimate** — safe to visit
- 🎣 **Phishing** — credential harvesting attack
- 🦠 **Malware** — drive-by download or exploit page
- 💥 **Defacement** — hacked/defaced website

---

## Key Results

| Model | Accuracy | Precision | Recall | F1-Score |
|-------|----------|-----------|--------|----------|
| **Gradient Boosting** ⭐ | **97.4%** | **97.2%** | **97.4%** | **97.3%** |
| XGBoost | 97.1% | 97.0% | 97.1% | 97.1% |
| Random Forest | 96.8% | 96.7% | 96.8% | 96.7% |
| Multi-layer Perceptron | 96.2% | 96.0% | 96.2% | 96.1% |
| Decision Tree | 95.5% | 95.3% | 95.5% | 95.4% |
| K-Nearest Neighbors | 94.8% | 94.7% | 94.8% | 94.7% |
| Support Vector Machine | 94.1% | 94.0% | 94.1% | 94.0% |
| Logistic Regression | 92.3% | 92.1% | 92.3% | 92.2% |
| Naive Bayes | 87.6% | 87.4% | 87.6% | 87.5% |

---

## Research Paper

**Title**: *Securing the Web Using URL-Based Analysis and Machine Learning Algorithms*

**Venue**: 5th International Conference on Pervasive Computing and Social Networking (ICPCSN 2024)

**Authors**: Monukarthik et al.

| Resource | Link |
|----------|------|
| 📄 Research Paper (PDF) | [View Paper](Research_Paper/Research_Paper.pdf) |
| 🏆 Presentation Certificate | [View Certificate](Research_Paper/Paper_Presentation_Certificate.pdf) |

---

## Problem Statement

Phishing attacks account for over **36% of all data breaches** (Verizon DBIR). Traditional blocklist-based defenses suffer from:
- **Lag time**: New phishing URLs evade blocklists for hours/days
- **Scale**: Millions of new malicious URLs registered daily
- **Evasion**: Attackers rotate domains and use URL shorteners

A machine learning approach trained on structural URL features detects **zero-day phishing URLs in real-time** without relying on reputation databases.

---

## Project Structure

```
Securing-the-web-using-URL-based-analysis-and-Machine-Learning-Algorithms/
│
├── Research_Paper/
│   ├── Research_Paper.pdf              ← Published ICPCSN 2024 paper
│   └── Paper_Presentation_Certificate.pdf
│
├── Dataset/
│   └── dataset.csv                    ← Kaggle URL dataset (legitimate + phishing)
│
├── notebooks/
│   ├── 01_Exploratory_Data_Analysis.ipynb
│   ├── 02_Feature_Engineering.ipynb
│   ├── 03_Model_Training_Comparison.ipynb
│   └── 04_Model_Evaluation.ipynb
│
├── src/
│   ├── feature_extraction.py          ← URL feature extractor
│   ├── train.py                       ← Model training pipeline
│   └── predict.py                     ← Inference / URL checker
│
├── requirements.txt
├── README.md
└── LICENSE
```

---

## Feature Engineering

The model uses **87 structural and lexical URL features** extracted without fetching the page content:

### URL Structure Features
| Feature | Description |
|---------|-------------|
| `url_length` | Total character length of the URL |
| `num_dots` | Number of dots in the URL |
| `num_subdomains` | Depth of subdomain nesting |
| `has_ip_address` | IP used instead of domain name |
| `uses_https` | Whether HTTPS is present |
| `url_entropy` | Shannon entropy (high = suspicious random strings) |
| `tld` | Top-level domain (.tk, .xyz = high-risk) |

### Path & Query Features
| Feature | Description |
|---------|-------------|
| `path_length` | Character length of the path |
| `num_query_params` | Number of query parameters |
| `has_at_symbol` | `@` in URL (browser ignores left side) |
| `has_double_slash` | Redirect indicator |
| `num_hyphens` | Hyphens in domain (phishing indicator) |
| `has_port` | Non-standard port in URL |
| `has_anchor` | `#` redirects (cloaking technique) |

### Lexical / Obfuscation Features
| Feature | Description |
|---------|-------------|
| `brand_in_subdomain` | Known brand name in subdomain |
| `brand_in_path` | Known brand name in path |
| `shortening_service` | Uses bit.ly, tinyurl, etc. |
| `hex_encoding` | Percent-encoded characters |
| `num_special_chars` | Total `!`, `$`, `%`, `&` etc. |

---

## Methodology

### Phase 1 — Data Collection
- Dataset sourced from Kaggle containing legitimate, phishing, malware, and defacement URLs
- ~651,000 labelled URL samples

### Phase 2 — Feature Extraction
- 87 features extracted from raw URL strings using regex and string parsing
- **No live network requests** required — fully offline analysis

### Phase 3 — Model Training & Comparison
Nine classifiers compared using stratified 80/20 train-test split:
- Random Forest, SVM, Decision Tree, KNN, Logistic Regression, MLP, Gradient Boosting, XGBoost, Naive Bayes

### Phase 4 — Evaluation
- Metrics: Accuracy, Precision, Recall, F1-Score, Confusion Matrix, ROC-AUC
- **Gradient Boosting** selected as final model — highest F1 across all four URL classes

---

## Installation & Usage

### 1. Clone the repository
```bash
git clone https://github.com/Monukarthik/Securing-the-web-using-URL-based-analysis-and-Machine-Learning-Algorithms.git
cd Securing-the-web-using-URL-based-analysis-and-Machine-Learning-Algorithms
```

### 2. Create a virtual environment
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the URL checker
```bash
python src/predict.py
# Enter any URL when prompted — outputs probability scores for each class
```

### 5. Explore the notebooks
```bash
jupyter notebook notebooks/
```

---

## How It Works

```
Input URL
    ↓
Feature Extraction (87 features, no HTTP request)
    ↓
Gradient Boosting Classifier
    ↓
Output: {Legitimate | Phishing | Malware | Defacement} + confidence score
```

**Example Output:**
```
URL: http://secure-banking-login.xyz/account/verify?id=123
→ Classification: PHISHING  (confidence: 96.8%)
   Risk signals: IP-based domain, excessive hyphens, brand keyword in path
```

---

## Applications

- 🌐 **Browser Extensions** — Real-time URL checking before page load
- 📧 **Email Gateways** — Scan links in incoming emails
- 🔒 **Corporate Firewalls** — Block malicious URLs at network level
- 📱 **SMS/Chat Security** — Detect smishing (SMS phishing) links

---

## Citation

If you use this work in your research, please cite:

```bibtex
@inproceedings{monukarthik2024securingweb,
  title     = {Securing the Web Using URL-Based Analysis and Machine Learning Algorithms},
  author    = {Monukarthik et al.},
  booktitle = {5th International Conference on Pervasive Computing and Social Networking (ICPCSN)},
  year      = {2024}
}
```

---

## Related Keywords

`phishing detection` · `malicious URL detection` · `URL classification` · `web security` ·
`cybersecurity machine learning` · `XGBoost phishing` · `gradient boosting` · `feature extraction URL` ·
`phishing URL classifier` · `URL-based threat detection` · `ICPCSN 2024`

---

## License

MIT License — see [LICENSE](LICENSE)
