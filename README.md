# CineLogic-Movie-Success-Classification-via-Inductive-Logic-Programming
---

## 🧠 Project Overview

**CineLogic** applies **Inductive Logic Programming (ILP)** to predict movie success using relational MovieLens data.  
Unlike black-box models, this project focuses on **interpretable rule induction**, enabling transparent reasoning about why a movie is classified as a *hit* or *non-hit*.

This work was developed as part of the **Machine Learning & Data Mining (MLDM)** coursework at the University of Surrey.

---

## 🔍 Learning Paradigm Comparison

| Paradigm | Focus | Interpretability |
|--------|------|------------------|
| Supervised ML | Statistical correlations | Low–Medium |
| Decision Trees | Hierarchical rules | Medium |
| **Inductive Logic Programming** | Relational, symbolic rules | **High** |

ILP complements statistical models by revealing **explicit logical patterns** rather than implicit correlations.

---

## 📂 Dataset

**MovieLens Relational Dataset**
- 3,646 movies
- Binary target: **Hit vs Non-Hit**
- Attributes include:
  - genres
  - audience ratings
  - popularity
  - director & actor quality
  - temporal metadata

The dataset is **nearly balanced**, enabling reliable evaluation using accuracy and F1-score.

---

## 🔧 Data Preparation for ILP

To support first-order logic reasoning:

- Continuous attributes were **discretised** into qualitative intervals (e.g. *low/high*, *few/many*)
- Categorical variables were encoded as **Prolog-style predicates**
- Separate files were created for:
  - background knowledge
  - positive examples
  - negative examples

This transformation improves **rule generalisation** and **human interpretability**.

---

## ⚙️ ILP Configuration

| Component | Setting |
|--------|--------|
| ILP Engine | PyGol |
| Logic Backend | SWI-Prolog (Janus interface) |
| Train/Test Split | 50 / 50 |
| `max_literals` | 2 |
| `min_pos` | 2 |
| `max_neg` | 170 |

Constraints were deliberately chosen to balance **expressiveness**, **interpretability**, and **overfitting control**.

---

## 📊 Results

| Metric | Score |
|------|------|
| Test Accuracy | **90.7%** |
| Test F1-Score | **90.6%** |
| Generalisation Gap | Low |

In addition to strong predictive performance, ILP generated **human-readable rules** capturing:

- genre-driven success patterns
- team-driven success (multiple directors)
- conditional temporal effects
- popularity–rating interactions

---

## 🧩 Example Learned Rule (Illustrative)

```prolog
hit(Movie) :-
    genre(Movie, adventure),
    high_rating(Movie),
    many_votes(Movie).
```
---

## ✨ Key Takeaways

- ILP achieves competitive accuracy while remaining fully interpretable
- Multiple success strategies emerge instead of a single dominant factor
- Symbolic learning is a powerful complement to statistical ML approaches

---

## 🛠️ Tech Stack

- Python
- PyGol
- SWI-Prolog
- Janus Interface
- MovieLens Relational Dataset

---

## 👤 Author

Aaditya Singh
MSc Data Science — University of Surrey

This repository contains the Inductive Logic Programming (ILP) component of a broader MLDM coursework project.
