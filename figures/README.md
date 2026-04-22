# Figures

All output figures from the stance detection pipeline organized by notebook.

## Baseline Models (01-02)
| Figure | Description |
|--------|-------------|
| `01_baseline_comparison.png` | Baseline model comparison |
| `02_vanilla_vs_tuned.png` | Vanilla vs tuned classical models |

## RoBERTa Training (03)
| Figure | Description |
|--------|-------------|
| `03_training_history.png` | Training and validation loss curves |
| `03_confusion_matrices.png` | Confusion matrices for all models |
| `03_complete_comparison.png` | Complete model comparison |

## Annotation & Augmentation (05-06)
| Figure | Description |
|--------|-------------|
| `label_distribution.png` | Label distribution in annotated dataset |
| `05_unified_comparison.png` | Unified model performance comparison (used in paper) |
| `05_class_progression.png` | Class F1 progression across models |
| `05_augmentation_impact.png` | Impact of data augmentation on minority classes |
| `05_top_words.png` | Top words per stance category |
| `05_sentence_length.png` | Sentence length distribution by stance |
| `06_augmentation_distribution.png` | Augmented dataset distribution |

## Confusion Matrices
| Figure | Description |
|--------|-------------|
| `cm_logistic_regression_tf-idf.png` | Logistic Regression confusion matrix |
| `cm_naive_bayes_tf-idf.png` | Naive Bayes confusion matrix |
| `cm_svm_tf-idf.png` | SVM confusion matrix |
| `cm_random_forest_tf-idf.png` | Random Forest confusion matrix |
| `cm_tuned_svm.png` | Tuned SVM confusion matrix |
| `cm_tuned_naive_bayes.png` | Tuned Naive Bayes confusion matrix |
| `cm_tuned_logistic_regression.png` | Tuned Logistic Regression confusion matrix |
| `cm_zero-shot_bert.png` | Zero-Shot BERT confusion matrix |

## Large-Scale Wikipedia Analysis (07)
| Figure | Description |
|--------|-------------|
| `07_weighted_stance_distribution.png` | Wikipedia stance distribution (used in paper) |
| `07_validation_comparison.png` | Validation set comparison |
| `07_manual_vs_largescale.png` | Manual annotation vs large-scale pipeline comparison |

## GenAI Analysis (08)
| Figure | Description |
|--------|-------------|
| `08_wiki_vs_genai_comparison.png` | Wikipedia vs GenAI stance,central finding (used in paper) |
| `08_genai_discipline_breakdown.png` | GenAI stance by discipline (used in paper) |
| `08_policy_length_vs_stance.png` | Policy length vs stance (used in paper) |
| `08_conditional_analysis_fig.png` | Conditional stance analysis (used in paper) |
| `08_tool_cooccurrence.png` | Tool co-occurrence analysis (used in paper) |
| `08_confidence_by_discipline.png` | Model confidence by discipline |
