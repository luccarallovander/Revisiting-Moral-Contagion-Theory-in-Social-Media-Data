# Revisiting-Moral-Contagion-Theory-in-Social-Media-Data

Yixiang Cheng, C., Rice, J., Rallo Vanderchmitt, L., Bozkurt, B. & Ratnam, R. (2025) **“Revisiting Moral Contagion Theory in Social Media Data”** (forthcoming).

# 🧠 Revisiting Moral Contagion Theory in Social Media Data

_This project revisits the robustness of **Moral Contagion Theory**, which posits that morally framed content spreads more widely online.  
Using multiple computational approaches — from dictionaries to large language models (LLMs) — we re-examine prior empirical findings on the relationship between moral content and virality across nine large Twitter (X) datasets._

---

## 🎯 Overview

### Research Context
The **digital transformation of communication** has reshaped how individuals engage with moral and political discourse.  
“Moral contagion” — the idea that morally charged content exhibits higher virality — has become a key framework for understanding online polarization, persuasion, and moral discourse (Brady et al., 2017).

However, recent work (Burton et al., 2021) has raised doubts about the **robustness and generalizability** of this effect, citing measurement biases and methodological inconsistencies in prior studies.

### Research Objective
This project systematically re-examines **moral contagion effects** across datasets, measurement methods, and time periods to assess:
1. How different **computational measurement approaches** (dictionary-based, ML, and LLM-based) influence estimated effects.  
2. Whether moral contagion holds under **longitudinal and causal** modeling frameworks.  
3. How **measurement error and methodological choices** affect theoretical conclusions in computational social science.

---

## 🧩 Study Design

The paper employs a **three-study framework**:

| Study | Focus | Approach |
|---|---|---|
| **Study I** | Measurement validity and bias | Compare dictionary-based, ML-based, and LLM-based detection of moral content |
| **Study II** | Temporal dynamics | Evaluate survival and decay of moral content virality over time |
| **Study III** | Causal inference | Apply double machine learning to identify causal effects of moral language on diffusion |

> This repository primarily documents **Study I**, submitted as an extended abstract to the Political Studies Association (PSA) Annual Conference 2026.

---

## ⚙️ Study I: Measurement Bias in Moral Foundations Analysis

### Research Questions
- **RQ1:** To what extent do machine learning– and LLM-based approaches differ from traditional dictionary-based methods in measuring moral foundations?  
- **RQ2:** How do these measurement differences affect the observed moral contagion effect?

### Methods
We evaluate four main measurement approaches:
1. **Dictionary-based methods** — e.g., Moral Foundations Dictionary (MFD1, MFD2).  
2. **Supervised ML models** — e.g., Moral-Strength (MoralStrength).  
3. **Fine-tuned transformer models** — e.g., MFormer.  
4. **Large language models (LLMs)** — e.g., GPT-4.1-nano.

These approaches were benchmarked against a **human-annotated ground truth corpus**, then applied to **nine politically salient datasets**:
> “Gun Control,” “Same-Sex Marriage,” “Climate Change,” “Women’s March,” “COVID-19,” “Mueller Report,” “MeToo,” “US Election,” and “Post-Brexit.”

The **dependent variable** is retweet count, modelled via **negative binomial regression** — following the literature (Brady et al., 2017).

---

## 📈 Results

### Binary Classification (Moral vs. Non-Moral Content)

| Method | Accuracy | F1 Score | Recall |
|---|---|---|---|
| MFormer | **0.76** | **0.76** | **0.76** |
| GPT-4.1-nano | 0.72 | 0.71 | 0.72 |
| MFD-2 | 0.70 | 0.69 | 0.70 |
| Moral-Strength | 0.69 | 0.69 | 0.69 |
| MFD-1 | 0.68 | 0.68 | 0.68 |

**Summary:**  
Fine-tuned transformer models (MFormer) outperform both dictionaries and supervised ML models in binary moral classification.

---

### Multi-Class Classification (Five Moral Foundations)

| Method | Accuracy | F1 Score | Recall |
|---|---|---|---|
| MFD-1 | **0.55** | **0.54** | **0.55** |
| MFormer | 0.54 | **0.55** | 0.53 |
| MFD-2 | 0.52 | 0.54 | 0.52 |
| Moral-Strength | 0.52 | 0.53 | 0.52 |
| GPT-4.1-nano | 0.46 | 0.49 | 0.46 |
| eMFD / MoralBERT | 0.26 | 0.19 | 0.26 |

**Summary:**  
In multi-class settings, dictionary-based approaches still perform competitively.  
However, **F1 scores** reveal that transformer models offer better **precision–recall balance**, highlighting trade-offs between interpretability and predictive performance.

---

### Replication of Moral Contagion Effects

- Moral contagion effects remain statistically significant in **7 of 9 datasets** using LLM-based measures.  
- Effect sizes are **substantially larger** under LLM measurement compared to dictionary-based approaches.  
- Results confirm that **measurement choice critically influences effect magnitude** and theoretical conclusions.

Example:  
> In the *COVID-19*, *Mueller Report*, and *MeToo* datasets, LLM-based metrics estimate contagion effects up to **40–60% larger** than dictionary-based models.

---

## 🧠 Interpretation

These findings suggest that previous skepticism toward moral contagion effects may stem from **measurement artifacts** rather than absence of genuine phenomena.  
LLM-based methods capture semantic nuances missed by bag-of-words approaches, improving the validity of moral foundation detection.

Overall, our results highlight the **importance of measurement validity** in computational social science and provide methodological guidance for future work in **moral psychology, online behavior, and political communication.**

---

## 🧰 Tech & Methods

| Category | Tools / Libraries |
|-----------|------------------|
| Languages | Python |
| NLP & ML | Transformers (HuggingFace), scikit-learn, PyTorch |
| Evaluation | Accuracy, F1, Recall, Negative Binomial Regression |
| Data Sources | Twitter/X datasets (Brady et al., 2017; Burton et al., 2021) |
| Reproducibility | `requirements.txt`, Jupyter Notebooks, Git version control |

---

## 🚀 Reproducibility

```bash
# Clone repository
git clone https://github.com/luccarallovander/Revisiting-Moral-Contagion-Theory-in-Social-Media-Data.git
cd Revisiting-Moral-Contagion-Theory-in-Social-Media-Data

# Install dependencies
pip install -r requirements.txt

# Run main experiment
python study_I_measurement_analysis.py
