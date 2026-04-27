# Food Safety Risk Prediction Using RASFF Data

## 📘 Overview
This project explores whether machine learning can be used to **predict food safety risk** using real-world data from the EU’s Rapid Alert System for Food and Feed (RASFF).  
The final result is a **binary classification model** (high risk vs. not high risk) achieving **~87% accuracy**, along with a demo **Streamlit application**.

---


## 📁 Dataset
- **~27,000 RASFF cases** (2020–2025)  
- **13 features** (numeric + categorical)  
- **Target variable**: 6-level risk decision (“no risk” → “serious risk”)

**Key challenges:**
- Long, unstructured text fields  
- Very diverse categorical variables  
- Significant class imbalance  

---

## 🧪 Hazard Classification
The “subject” text field was classified into **9 hazard types** using an LLM.

**Insights:**
- **Chemical hazards** were the most common overall  
- In serious cases:
  - **Salmonella**: ~31%  
  - **Aflatoxins**: ~28%  
  - Remaining: mix of chemical + microbiological hazards  

---

## 🌍 Origin & Product Insights
Most frequently reported origins:
- **Turkey**
- **Poland**
- **India**
- **China**

Most affected product categories:
- **Fruits & vegetables**
- **Nuts & seeds**

---

## 🔍 Feature Selection
Used **Cramer's V** to evaluate feature–risk relationships.

Most informative features:
- Hazard-related attributes  
- Origin information  

Ultimately selected **7 important features** for the baseline model.
-Category, subject, origin, notifying country, hazard, hazard type, classification


---

## 🛠️ Feature Engineering
This was one of the most challenging parts of the project.

Methods used:
- **Sentence Transformer embeddings** for the "subject" text  
- **One-hot encoding** for low-cardinality features  
- **Target encoding** for high-cardinality features (hazard, origin, notifying country)  
- Tested both embeddings and one-hot for product categories  

---

## ⚖️ Handling Data Imbalance
The dataset is heavily skewed toward the **“serious” risk** class.

Results:
- **6-class model** → ~75% accuracy, very high recall for serious cases  
- Reducing to **3 classes** or **2 classes** increased accuracy but lowered sensitivity to high-risk cases  

Trade-off: accuracy vs. preserving high-risk detection.

---

## 🤖 Model Comparison
Tried several models with progressively added features.

Best performing models (3-class setup):
- **XGBoost**
- **LightGBM**

Both handled high-dimensional encoded features well.

---

## 🏆 Final Model
Final configuration:
- **Binary classification** (high risk vs. not high risk)  
- **7 features**  
- **XGBoost**, tuned via randomized search  

**Final accuracy:**  
➡️ **~87%**

---

## 🖥️ Streamlit Demo App
A simplified interactive demo was created.

User inputs:
- **Subject**
- **Hazard type**
- **Origin**

Outputs:
- **High risk** or **Moderate/low risk** prediction  
- Probability score  

---

## 🧩 Conclusion
The project demonstrates the potential of machine learning for supporting **food safety risk assessment**.

**Key achievements:**
- Built a model with strong performance (~87% accuracy)  
- Developed a functional Streamlit demo  
- Explored methods for handling high-cardinality and imbalanced data  

**Future improvements:**
- Improved encoding for high-cardinality features  
- Fine-tuned language models  
- More robust Streamlit integration  
- Enhanced treatment of class imbalance  

---

## 🚀 Tech Stack
- Python  
- XGBoost / LightGBM  
- Sentence Transformers  
- Pandas / NumPy / Scikit-learn  
- Streamlit  

---

## 📁 Project Files

```
📄 AI meets food safety_presentation.pdf  → Summary presentation
📓 20 experimentation notebook (will be cleaned up later)
📄 cleanedDataset.csv    → cleaned dataset
📄 RASFF_originaldataset.csv    → origina dataset
```
