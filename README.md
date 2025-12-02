# 🧬 Machine Learning Classification of Structural Protein Sequences for Drug Discovery

**Authors:**  
**Paul London**, **Ernest Bonat, Ph.D.**

---

## 📘 Overview

This repository accompanies the project **“Machine Learning Classification of Structural Protein Sequences for Drug Discovery.”**  
The project investigates how modern machine learning (ML) and language-modeling techniques can classify proteins based solely on their amino acid sequences.

By treating protein sequences as *biological text*, we apply natural language processing (NLP), recurrent neural networks (LSTMs), and pre-trained large language models (LLMs, e.g., ESM-2) to analyze patterns within primary structure and predict each protein’s functional class.

The project emphasizes:

- Lightweight, GPU-friendly workflows  
- Methods balancing computational efficiency with biological relevance  
- Comparisons between NLP, LSTM, and LLM-based approaches  
- Exploratory data analysis (EDA) of protein sequences from the Protein Data Bank (PDB)

---

## 📂 Repository Structure

- Notebook.ipynb
- .gitignore
- README.md
- requirements.txt

---

## 📦 Dataset

Data originate from:

- **Kaggle – Protein Data Set**  
  (originally sourced from the RCSB Protein Data Bank)

Two files are required:

- `metadata.csv` — experimental and structural metadata  
- `sequences.csv` — amino acid sequences for all chains  

### 🔍 Key preprocessing steps

1. Merge metadata and sequences on `structureId`  
2. Filter for **proteins only**  
3. Remove missing sequences/labels  
4. Clean sequences to the **20 standard amino acids**  
5. Keep sequence lengths **20–1024 residues**  
6. Concatenate multi-chain sequences  
7. Select the **top 20 protein classes**  
8. Train/validation/test split (70/15/15)

---

## 🚀 Project Pipelines

### **🧵 Pipeline 1 — NLP + Tree-Based Models**

- 3-mer tokenization  
- CountVectorizer  
- SMOTE for imbalance  
- Dimensionality reduction (SVD)  
- LazyClassifier baseline  
- Optuna hyperparameter tuning  

**Best model:** Tuned Random Forest  
**Accuracy:** ~69.7%

---

### **🔁 Pipeline 2 — LSTM Sequence Model (Keras)**

- Tokenized + padded sequences  
- Bidirectional LSTM  
- Class weighting  
- Trained 50–100 epochs  

**Best validation accuracy:** ~78.2%

---

### **🧠 Pipeline 3 — LLM Embeddings (ESM-2)**

- Pre-trained model: `esm2_t6_8M_UR50D`  
- Extract embeddings per sequence  
- Train shallow neural nets & tree models  
- UMAP visualization of protein structure space  

**Status:** Embedding-based model comparison in progress

---

## 📊 Exploratory Data Analysis

Includes:

- Sequence length distributions  
- Protein class counts  
- Amino acid composition & grouping  
- PCA and UMAP  
- Secondary-structure motif logos (Logomaker)

---

## 🛠️ Installation

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
pip install -r requirements.txt
