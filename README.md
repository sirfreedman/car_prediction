# Dual-Stage Hybrid Phishing Email Detection System 🛡️

A high-throughput, cascading machine learning pipeline designed to detect phishing emails efficiently by combining fast statistical filtering with deep semantic analysis.

## What is Phishing?
A **phishing email** is a cyber attack where malicious actors disguise themselves as trusted entities to steal sensitive credentials or data. Building automated systems to catch these threats instantly is a crucial first line of defense in cybersecurity.

---

## Project Overview
Running heavy deep learning models on every single incoming email wastes massive amounts of compute power. To solve this locally in VS Code, I engineered a high-throughput, cascading hybrid pipeline:

* **The Fast Filter (Stage 1):** Uses TF-IDF and Logistic Regression to instantly handle clear-cut, high-confidence traffic.
* **Deep Semantic Analysis (Stage 2):** Dynamically routes the most ambiguous emails to a local Sentence Transformer (`all-MiniLM-L6-v2`) for deep context inspection.

---

## Implementation Workflow

1. **Data Prep & Hygiene:** Processed raw text data from Kaggle, ensuring strict data hygiene by keeping validation splits clean to prevent data leakage.
2. **Confidence Thresholding:** Set an optimal **80% routing threshold** through trial and error. This routes 48% of straightforward emails instantly through the fast filter (preserving local resources), while sending the trickiest 52% to the transformer model.
3. **Smart Routing & Training:** Funneled tricky, low-confidence emails into the Sentence Transformer and trained a secondary linear model on a balanced 500/500 split for robust feature boundaries.
4. **Performance:** Achieved an overall accuracy of **93.5%** and a phenomenal **99.0% phishing recall**—proving you don't have to sacrifice speed for deep semantic precision.

---

## Dataset Instructions
Due to GitHub's file size limit (100MB), the raw dataset cannot be stored directly in this repository. 
* You can download the dataset directly from Kaggle here: https://www.kaggle.com/datasets/naserabdullahalam/phishing-email-dataset?select=phishing_email.csv
* Place the downloaded file into your local project directory before running the Jupyter Notebook.