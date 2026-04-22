# Syllabus Stance Detection: Wikipedia vs Generative AI

**From Caution to Embrace: Stance Shifts in University Syllabus Policies 
Toward Wikipedia and Generative AI**

*Charitha Battini, Alireza Javadian Sabet, Morgan R. Frank*  
*University of Pittsburgh — Department of Informatics and Networked Systems*

---

## Overview

This repository contains the full pipeline for detecting stance in university 
syllabus policy sentences and applying it comparatively to Wikipedia and 
Generative AI (GenAI) policies.

We fine-tune a RoBERTa-base model on 354 manually annotated syllabus sentences 
across three stance categories **discouraging**, **conditional**, and 
**encouraging** achieving a Macro F1 of 0.682. Applied at scale, we find 
that 72.7% of Wikipedia policy sentences are discouraging while 57.1% of 
GenAI policy sentences are encouraging a near-complete reversal of academic 
stance.

---

## Repository Structure

| Notebook | Description |
|----------|-------------|
| `00_data_preparation.ipynb` | Data loading, cleaning, and filtering of Wikipedia syllabus sentences |
| `01_baseline_models.ipynb` | Logistic Regression, SVM, and Zero-Shot BERT baselines |
| `02_hyperparameter_tuning.ipynb` | Grid search and cross-validation for classical models |
| `03_scibert_finetuning_clean.ipynb` | RoBERTa and SciBERT fine-tuning with class weighting and balanced sampling |
| `04_inter_annotator_agreement.ipynb` | Annotation validation and label consistency review |
| `05_error_analysis.ipynb` | Error analysis and model comparison across all approaches |
| `06_data_augmentation.ipynb` | Synthetic data generation using Llama-3 via Groq API |
| `07_large_scale_classification.ipynb` | Large-scale inference on 26,600 Wikipedia sentences (CRC pipeline) |
| `08_genai_analysis.ipynb` | GenAI policy analysis : sentence extraction, classification, and comparative analysis |

---

## Key Findings

- **Wikipedia**: 72.7% discouraging, 18.5% conditional, 8.9% encouraging (n=9,686, weighted)
- **GenAI**: 57.1% encouraging, 27.4% discouraging, 15.5% conditional (n=2,076)
- Encouraging GenAI policies are ~2x longer than discouraging ones (median 317 vs 141 words)
- Citation is the most common condition attached to GenAI permission (18.7%)
- Naming a specific AI tool (ChatGPT, Gemini etc.) correlates with encouraging stance

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
| `wiki_unique_sentences.csv` | 26,600 Wikipedia-mentioning syllabus sentences (Open Syllabus Project) |
| Manually annotated set | 354 sentences (discouraging=292, conditional=34, encouraging=28) |
| Augmented training set | 483 sentences (real + Llama-3 synthetic) |
| GenAI corpus | 2,076 AI-mentioning sentences from 208 syllabi |

---

## Infrastructure

- **Local**: MacBook, Python 3.9, Jupyter
- **GPU Training**: Google Colab (T4 GPU)
- **Large-Scale Inference**: University of Pittsburgh CRC (`htc-n86.crc.pitt.edu`)
- **Augmentation**: Groq API (Llama-3, free tier)

---

## Dependencies

```bash
pip install transformers torch scikit-learn pandas numpy matplotlib 
            seaborn spacy openpyxl
python -m spacy download en_core_web_sm
```

---

## Citation

If you use this work please cite:

```bibtex
@article{battini2026stance,
  title={From Caution to Embrace: Stance Shifts in University Syllabus 
         Policies Toward Wikipedia and Generative AI},
  author={Battini, Charitha and Javadian Sabet, Alireza and Frank, Morgan R.},
  year={2026}
}
```

---

## Acknowledgments

This work was conducted as an independent study at the University of Pittsburgh 
under the supervision of Morgan R. Frank. The project was conceived and guided 
by Alireza Javadian Sabet. We thank the contributors to the 
[Syllabi Policies for Generative AI Repository](https://osf.io/) and the 
[Open Syllabus Project](https://opensyllabus.org) for making their data 
publicly available. Computing resources were provided by the University of 
Pittsburgh Center for Research Computing (CRC).
