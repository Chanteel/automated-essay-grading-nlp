#  Automated Grading and Feedback for Argumentative Essays Using NLP  

**Author:** Chanteel Kimathi  
**Institution:** USIU-Africa  

---

## 📘 Project Overview  

Manual essay grading is time-consuming and subjective, often leading to inconsistent evaluation.  
This project develops a **hybrid NLP-based Automated Essay Scoring (AES)** system that uses both **linguistic features** and **semantic embeddings (SBERT)** to predict scores for argumentative essays and generate structured feedback aligned with marking rubrics.  

The model aims to reach **human-level scoring agreement** (Quadratic Weighted Kappa ≥ 0.80) and provide **actionable, rubric-based feedback** on content, organization, and language use.  

---

## 📊 Dataset  

- **Source:** [Kaggle ASAP-AES Competition](https://www.kaggle.com/competitions/asap-aes)  
- **Essays Used:** Sets 2 and 6 (argumentative essays)  
- **Target Variable:** `domain1_score` (range 1–6)  
- **Sample Provided:**  
  A small demonstration file, `asap_argumentative_sample.csv`, containing **200 essays**, is included for testing and reproducibility.  
  *(The full dataset is too large to host on GitHub but is publicly available on Kaggle.)*

---

## ⚙️ Methodology  

### **1. Preprocessing**
- Lowercasing, punctuation & number removal  
- Tokenization, stopword removal, lemmatization (spaCy)  
- Feature extraction:  
  - **Linguistic features:** word count, sentence count, lexical diversity, average sentence length, and average token length.  
  - **Semantic features:** contextual embeddings from **Sentence-BERT (`all-mpnet-base-v2`)**

### **2. Modeling**
- **Baseline:** Random Forest Regressor using linguistic features  
- **Hybrid Model:** LightGBM Regressor using linguistic + SBERT features  
- **Evaluation Metrics:** Mean Squared Error (MSE), R² Score, Quadratic Weighted Kappa (QWK)

| Model | MSE | R² | QWK |
|--------|-----|----|-----|
| Baseline (Random Forest) | 0.42 | 0.61 | 0.60 |
| Hybrid (LightGBM + SBERT) | 0.28 | 0.75 | 0.78 |

---

## 💡 Key Insights  

1. **Semantic context** captured by SBERT embeddings is the strongest predictor of essay quality.  
2. **Lexical diversity** and **average sentence length** correlate positively with human-assigned scores.  
3. **Prompt-specific fine-tuning** may further enhance fairness and reduce bias across essay topics.  

---

## 🚀 Next Steps  

- Integrate a **template-based feedback generator** (GPT-based) for actionable, rubric-aligned comments.  
- Improve **fairness and explainability** using SHAP visualizations.  
- Deploy a **Gradio web demo** for real-time essay scoring and feedback delivery.  
- Conduct **peer evaluation** to assess feedback quality and usefulness.

---

## 🧾 Files in This Repository  

| File | Description |
|------|--------------|
| `automated_grading.ipynb` | Jupyter notebook containing data prep, modeling, and evaluation code. |
| `Preliminary_Results_Report.docx` | 5-page summary report for DSA 4900 submission. |
| `asap_argumentative_sample.csv` | 200-row sample dataset for demonstration. |
| `README.md` | This documentation file. |

---

## 🧩 Tools and Libraries  

- Python (Pandas, NumPy, Matplotlib, Seaborn)  
- NLP: spaCy, NLTK, Sentence-Transformers  
- Modeling: scikit-learn, LightGBM  
- Evaluation: Cohen’s Kappa (QWK), MSE, R²  
- Deployment: Gradio / Streamlit  

---

## 🏁 Results Summary  

The hybrid AES model achieved:
- **QWK = 0.78** → strong agreement with human raters  
- **R² = 0.75** → strong predictive power  
- **MSE = 0.28** → improved over baseline (0.42)  

These results confirm that combining linguistic structure with semantic embeddings yields more consistent and accurate essay scoring than using traditional surface features alone.  

---

