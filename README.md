# DriftTermIR (CIKM 2026 Short Paper — Anonymous Demo)

This repository provides a **minimal, review-stage demo** for our anonymous CIKM 2026 short paper submission:

**“Spectral Drift Monitoring of Contextual Embeddings for Multi-Sense Semantic Change”**

> **Review-stage note (anonymity + open science).**  
> During anonymous review, we release a lightweight demo that reflects the **core pipeline and code structure**.  
> A **fully reproducible release** (complete configs/scripts, end-to-end runs, and documentation) will be provided **upon acceptance**.

---

## Why this matters for IR / IS

Dynamic collections (news, patents, scientific literature) exhibit **term drift**: the meaning and neighborhood of a term changes over time.  
This can cause **temporal vocabulary mismatch** and degrade downstream workflows such as:

- **Query rewriting / expansion** for cross-temporal search
- **Drift-aware monitoring & alerting** (e.g., emerging-technology tracking)
- **Collection analytics** (neighborhood turnover, technology recombination signals)

Our method is designed as a **lightweight, alignment-free drift monitor** that can **rank and alert** drifting terms and provide **interpretable** broadening vs. specialization signals.

---

## Overview of the approach

At a high level, the approach:

- adopts a distributional view of contextual token embeddings (a **projected-Gaussian interpretation**),
- measures drift using a **centered covariance-spectrum** statistic (spectral anisotropy / eigengap),
- handles polysemy via **slice-local clustering** and **cluster-weighted aggregation**,
- supports interpretation via **representative usage extraction** and visualization.

This makes the monitor suitable as a **plug-in module** in IR pipelines: detect drift → trigger rewriting/alerts → support analysis.

---

## What this demo provides

- A compact reference implementation of the main components (structure-level faithful to the paper):
  - slice handling (time/domain windows),
  - spectral drift scoring utilities,
  - optional multi-sense clustering hooks,
  - qualitative inspection utilities (representative usages + visualization).

### Not included (yet)
- End-to-end reproduction scripts and exact hyperparameter/config files
- Preprocessed datasets and embedding caches
- Full ablation/logging + figure/table generation pipeline

These will be included in the post-acceptance release.

---

## Repository structure

<pre>
├── code/
│   ├── detect_semantic_change.py         # Drift monitor demo (reference pipeline)
│   ├── util.py                           # Utilities: loading, clustering hooks, scoring
│   ├── visualize_change_target_word.py   # Clustering + PCA projection for interpretability
│   ├── extract_typical_instance.py       # Representative usage extraction
│   └── patent_preprocess.py              # USPTO text preprocessing helpers
│
├── data/
│   ├── data_description.pdf              # Dataset overview (benchmark & USPTO)
│   └── additional_resources/             # Stopwords / symbols filters for USPTO
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
