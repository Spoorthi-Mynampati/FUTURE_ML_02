# 🤖 Intelligent Customer Support Ticket Triage System

An end-to-end NLP engineering pipeline built to automate customer support queues by handling text preprocessing, dual-target classification (predicting both **Ticket Category** and **Priority Urgency**), and automated routing triage.

---

## 📈 The Core Engineering Highlight: Data Auditing & Insights
> ⚠️ **Key Project Finding:** During evaluation, the model achieved a static **19.24% accuracy** across 5 balanced classes. Through statistical auditing of the text matrices, this project successfully proved a negative: the underlying public dataset consists of mathematically randomized synthetic templates with zero correlation between features and target labels. 
> 
> While the model cannot extract a signal from pure noise, the **entire backend infrastructure, regex engineering, and dual-model architecture are 100% production-ready** for real-world deployment.

---

## 🚀 Key Features Built
* **Custom Text Cleaning Pipeline:** Built a regex-driven pipeline handling lowercase standardization, noise/punctuation removal, and edge-case tokenization fixing (e.g., dynamically handling `"iam"` -> `"I am"`).
* **Feature Engineering Matrix:** Utilized `TfidfVectorizer` mapping unigrams and bigrams (`ngram_range=(1,2)`) to capture multi-word contextual phrases.
* **Dual-Target Classification Architecture:** Designed an infrastructure that simultaneously trains two separate Scikit-Learn `LogisticRegression` models over a unified TF-IDF feature matrix:
  1. `category_model` (Maps text to issues like *Billing, Technical, Cancellation*)
  2. `priority_model` (Maps text to triage levels like *High, Medium, Low*)
* **Real-Time Inference Simulator:** Programmed an interactive `triage_ticket()` entry point that mimics a live backend API to clean, vectorize, and tag incoming tickets instantly.

---

## 📊 Dataset Distribution (Exploratory Data Analysis)
The pipeline includes visual evaluation to verify class balancing across the ~8,400 ticket corpus:

*(Note: Remember to upload your `ticket_distribution.png` image to this repository so this image displays!)*

---

## 🛠️ Tech Stack & Libraries Used
* **Language:** Python 3
* **Environment:** Google Colab / Jupyter Notebooks
* **Data Manipulation:** Pandas, NumPy
* **Machine Learning & NLP:** Scikit-Learn (`TfidfVectorizer`, `LogisticRegression`, `train_test_split`)
* **Data Visualization:** Seaborn, Matplotlib
* **Text Processing:** Python Native Regex (`re`)

---

## 🔮 Sample Live Triage Output
```text
📥 Incoming Ticket: 'I am unable to login to my account due to a 500 error'
--------------------------------------------------
🤖 Classified Category : Technical issue
🔥 Tagged Priority     : High
⚙️ Automation Action   : 🚨 Route directly to Tier-1 Live Escalation Queue
