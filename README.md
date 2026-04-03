# DriftTermIR (CIKM26 Short Paper Demo Repository)

This repository provides a **minimal, review-stage demo** for our CIKM 2026 short track submission:

**“Spectral Drift Monitoring of Contextual Embeddings for Multi-Sense Semantic Change”**

> **Review-stage note.**  
> To support an *open-science* signal during the anonymous review period, we release a lightweight demo that reflects the **overall pipeline and code structure**.  
> A **full, cleaned, and fully reproducible release** (complete configs/scripts, end-to-end runs, and documentation) will be provided **after acceptance**.

---

## 🧠 Overview

Detecting how word meanings shift over time is essential to understanding language, technology, and society.  
Our work introduces an **unsupervised semantic drift monitor** for contextual embeddings (e.g., BERT-family models) with an emphasis on **multi-sense** change and **interpretability**.

At a high level, the approach:
- adopts a distributional view of contextual representations (projected-Gaussian perspective),
- monitors drift using a **covariance-spectrum (spectral) signal**,
- supports interpretation via **multi-sense clustering** and **representative instance extraction**.

---

## ✅ What This Demo Provides

- A compact reference implementation of the main components (structure-level faithful to the paper):
  - embedding IO and slice handling,
  - spectral drift scoring utilities,
  - optional clustering hooks for multi-sense analysis,
  - qualitative inspection utilities (representative usages).

### Not included (yet)
- End-to-end reproduction scripts and exact hyperparameter/config files
- Preprocessed datasets and embedding caches
- Full ablation, logging, and figure/table generation pipeline

These will be released in the post-acceptance version.

---

## 📁 Repository Structure

<pre>
├── code/
│   ├── detect_semantic_change.py         # Drift monitor demo (reference pipeline)
│   ├── util.py                           # Utility functions for data loading, clustering, etc.
│   ├── visualize_change_target_word.py   # Clustering + PCA projection for interpretability
│   ├── extract_typical_instance.py       # Highlighting representative shifted usages
│   └── patent_preprocess.py              # Tools for cleaning and processing USPTO patent texts
│
├── data/
│   ├── data_description.pdf              # Overview of benchmark & domain datasets
│   └── additional_resources/             # Custom stopword lists, Greek symbols, and filters for USPTO
│       ├── greek.txt
│       ├── stopwords.txt
│       └── symbols.txt
</pre>


---

## 📊 Datasets

### 🔬 SemEval-2020 Task 1 
- Multilingual benchmark with human-labeled semantic shifts (EN, DE, LA, SV).
- Evaluated using mBERT contextual embeddings.

### 🏛️ USPTO Patent Corpus
- 7.6M granted patents (1960–2022), segmented into 5-year windows.
- Tracks how technical terms evolve in meaning and domain usage.
- Demonstrates real-world scalability and interpretability.
