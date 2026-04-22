# Syllabus Stance Detection: Wikipedia vs Generative AI

**From Caution to Embrace: Stance Shifts in University Syllabus Policies Toward Wikipedia and Generative AI**

*Charitha Battini, Alireza Javadian Sabet, Morgan R. Frank*

*University of Pittsburgh , Department of Informatics and Networked Systems*

---

## Overview

This repository contains the full pipeline for detecting stance in university syllabus policy sentences and applying it comparatively to Wikipedia and Generative AI (GenAI) policies.

We fine-tune a RoBERTa-base model on 354 manually annotated syllabus sentences across three stance categories : **discouraging**, **conditional**, and **encouraging** ,achieving a Macro F1 of 0.682. Applied at scale, we find that 72.7% of Wikipedia policy sentences are discouraging while 57.1% of GenAI policy sentences are encouraging a near-complete reversal of academic stance.

---

## Repository Structure

```
syllabus-stance-detection/
│
├── notebooks/                          
│   ├── 00_data_preparation.ipynb
│   ├── 01_baseline_models.ipynb
│   ├── 02_hyperparameter_tuning.ipynb
│   ├── 03_scibert_finetuning_clean.ipynb
│   ├── 04_inter_annotator_agreement.ipynb
│   ├── 05_error_analysis.ipynb
│   ├── 06_data_augmentation.ipynb
│   ├── 07_large_scale_classification.ipynb
│   └── 08_genai_analysis.ipynb
│
├── data/                               
│   ├── raw/                            
│   ├── annotation/                     
│   ├── processed/                      
│   └── interim/                        
│
├── results/                            
│
└── figures/                            
```

---

## Notebook Descriptions

| Notebook | Description |
|----------|-------------|
| `00_data_preparation.ipynb` | Data loading, cleaning, and filtering of Wikipedia syllabus sentences |
| `01_baseline_models.ipynb` | Logistic Regression, SVM, and Zero-Shot BERT baselines |
| `02_hyperparameter_tuning.ipynb` | Grid search and cross-validation for classical models |
| `03_scibert_finetuning_clean.ipynb` | RoBERTa and SciBERT fine-tuning with class weighting and balanced sampling |
| `04_inter_annotator_agreement.ipynb` | Annotation validation and label consistency review |
| `05_error_analysis.ipynb` | Error analysis and model comparison across all approaches |
| `06_data_augmentation.ipynb` | Synthetic data generation using Llama-3 via Groq API |
| `07_large_scale_classification.ipynb` | Two-stage pipeline: policy relevance filtering (CRC) + stance classification (Colab) |
| `08_genai_analysis.ipynb` | GenAI policy analysis — sentence extraction, classification, and comparative analysis |

---

## Key Findings

- **Wikipedia**: 72.7% discouraging, 18.5% conditional, 8.9% encouraging (n=9,686, weighted)
- **GenAI**: 57.1% encouraging, 27.4% discouraging, 15.5% conditional (n=2,076)
- Encouraging GenAI policies are ~2x longer than discouraging ones (median 317 vs 141 words)
- Citation is the most common condition attached to GenAI permission (18.7%)
- Naming a specific AI tool (ChatGPT, Gemini etc.) correlates with encouraging stance
- Languages and Information Studies show strongest resistance to GenAI
- STEM and applied fields are most permissive

---

## Model Performance

| Model | Macro F1 |
|-------|----------|
| Logistic Regression | 0.412 |
| SVM (tuned) | 0.467 |
| Zero-Shot BERT | 0.646 |
| SciBERT (fine-tuned) | 0.302 |
| RoBERTa (no augmentation) | 0.623 |
| **RoBERTa (+ augmentation)** | **0.682** |

---

## Data

| Dataset | Description |
|---------|-------------|
| `data/raw/` | Raw GenAI syllabus corpus (208 policies, 263KB) |
| `data/annotation/` | 354 manually annotated sentences across 3 stance categories |
| `data/processed/` | Augmented training set (483 sentences, real + synthetic) |
| `data/interim/` | Intermediate annotation and sampling files |
| `results/` | Large-scale classified datasets (9,686 Wikipedia + 2,076 GenAI sentences) |

> **Note**: The raw Wikipedia corpus (26,600 sentences, 30.4MB) is not included due to file size constraints. It is available via the [Open Syllabus Project](https://opensyllabus.org).

---

## Trained Model

The fine-tuned RoBERTa model is not included in this repository due to file size constraints (~500MB). It is available on request.

Contact: CHB299@pitt.edu

---

## Infrastructure

- **Local**: MacBook, Python 3.9, Jupyter
- **GPU Training**: Google Colab (T4 GPU)
- **Large-Scale Inference**: University of Pittsburgh CRC (`htc-n86.crc.pitt.edu`)
- **Augmentation**: Groq API (Llama-3, free tier)

---

## Dependencies

```bash
pip install transformers torch scikit-learn pandas numpy matplotlib seaborn spacy openpyxl groq
python -m spacy download en_core_web_sm
```

---

## Citation

```bibtex
@article{battini2026stance,
  title={From Caution to Embrace: Stance Shifts in University Syllabus Policies Toward Wikipedia and Generative AI},
  author={Battini, Charitha and Javadian Sabet, Alireza and Frank, Morgan R.},
  year={2026}
}
```

---

## Acknowledgments

This work was conducted as an independent study at the University of Pittsburgh under the supervision of Morgan R. Frank. The project was conceived and guided by Alireza Javadian Sabet. We thank the contributors to the [Syllabi Policies for Generative AI Repository](https://osf.io/) and the [Open Syllabus Project](https://opensyllabus.org) for making their data publicly available. Computing resources were provided by the University of Pittsburgh Center for Research Computing (CRC).
