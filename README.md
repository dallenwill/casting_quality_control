# Casting Quality Control

Automated defect detection for metal casting products using deep learning and computer vision.

---

## Overview

In manufacturing, casting defects such as blowholes, pinholes, burrs, shrinkage defects, mold material defects, and metallurgical defects can compromise product quality and lead to costly batch rejections. Traditional manual inspection is time-intensive and prone to human error.

This project builds a CNN-based image classification system to automatically identify **defective** vs. **non-defective** submersible pump impellers, reducing inspection time while improving detection accuracy and reliability.

---

## Dataset

- **Source:** [Kaggle - Real-life Industrial Dataset of Casting Product](https://www.kaggle.com/datasets/ravirajsinh45/real-life-industrial-dataset-of-casting-product)
- **Total Images:** 7,348 grayscale top-view images of submersible pump impellers (300x300 px)
- **Non-Augmented Set:** 1,300 images (519 non-defective, 781 defective) resized from 512x512 to 300x300

| Split | Images | Defective % |
|-------|--------|-------------|
| Training | 6,633 | 56.66% |
| Validation | 1,005 | — |
| Testing | 1,000 | 63.36% |

---

## Results

Three CNN architectures were developed and compared:

### Model 1 — Baseline CNN
| Metric | Value |
|--------|-------|
| Training Accuracy | 99.43% |
| Validation Accuracy | 94.70% |
| Test Accuracy | 84.80% |
| Test Loss | 1.8783 |

### Model 2 — CNN with Dropout + L2 Regularization ✅ **(Final Model)**
| Metric | Value |
|--------|-------|
| Best Epoch | 23 |
| Validation Accuracy | 92.54% |
| Test Accuracy | 80.30% |
| Test Loss | 0.6520 |

### Model 3 — CNN with Batch Normalization
| Metric | Value |
|--------|-------|
| Best Epoch | 9 |
| Validation Accuracy | 92.24% |
| Test Accuracy | 81.70% |
| Test Loss | 1.4000 |

**Model 2 was selected** as the final model due to its lowest test loss (0.6520), indicating the best generalization to unseen data. The model was saved as `CQC_4_Final_Model`.

---

## Project Structure

```
casting_quality_control/
│
├── notebooks/
│   ├── cqc_2_data_wrangling_eda.ipynb        # Data loading, cleaning, and EDA
│   └── cqc_3_data_processing_training.ipynb  # Preprocessing and model training
│
├── CQC_4_Final_Model/                         # Saved final model
│
├── reports/
│   ├── cqc_1_problem_statement.pdf
│   ├── cqc_5_presentation.pdf / .pptx
│   └── cqc_6_project_report.pdf / .docx
```

---

## Technologies

- Python
- TensorFlow / Keras
- NumPy, Pandas
- Matplotlib, Seaborn
- Scikit-learn
- Jupyter Notebook

---

## Getting Started

```bash
git clone https://github.com/dallenwill/casting_quality_control.git
cd casting_quality_control
pip install tensorflow numpy pandas matplotlib seaborn scikit-learn jupyter
jupyter notebook
```

Run notebooks in order:
1. `notebooks/cqc_2_data_wrangling_eda.ipynb`
2. `notebooks/cqc_3_data_processing_training.ipynb`

---

## Future Work

- Retrain periodically with new production data to maintain accuracy
- Expand the dataset to improve model generalization
- Deploy the model into a live quality control pipeline

---

## Author

**Dallen Huang**  
[GitHub](https://github.com/dallenwill)
