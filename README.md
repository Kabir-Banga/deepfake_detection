# Deepfake Image Detection using Transfer Learning and Fuzzy Logic

## Project Overview

Deepfake technology has advanced rapidly with the development of Generative Adversarial Networks (GANs), making manipulated images increasingly difficult to distinguish from authentic ones. This project presents a hybrid deepfake detection framework that combines Deep Learning and Fuzzy Logic to improve both prediction accuracy and interpretability.

Unlike traditional deep learning models that only provide binary predictions, this system introduces a trust-scoring mechanism that evaluates prediction confidence and uncertainty, helping users better understand model decisions.

---

## Problem Statement

Most deepfake detection systems rely solely on convolutional neural networks (CNNs) and provide only a "Real" or "Fake" prediction. These predictions often lack transparency and can be overconfident when handling uncertain cases.

This project addresses these limitations by integrating:

- Transfer Learning
- Confidence Margin Analysis
- Entropy-Based Uncertainty Measurement
- Fuzzy Inference Trust Scoring

The result is a more interpretable and reliable deepfake detection system.

---

## Dataset

The model was trained using the Kaggle Real vs Fake Face Dataset.

### Dataset Statistics

| Category | Images |
|-----------|---------|
| Real Images | 6,000 |
| Fake Images | 6,000 |
| Total Images | 12,000 |

### Data Split

- Training Set: 70%
- Validation Set: 15%
- Test Set: 15%

---

## Model Architecture

### Base Model

- MobileNetV2 (Pre-trained on ImageNet)

### Classification Head

```text
GlobalAveragePooling2D
        ↓
Dense (256, ReLU)
        ↓
Dropout (0.5)
        ↓
Dense (128, ReLU)
        ↓
Dropout (0.3)
        ↓
Dense (2, Softmax)
```

### Input Shape

```text
224 × 224 × 3
```

---

## Data Augmentation

To improve model generalization, the following augmentation techniques were applied:

- Rotation
- Horizontal Flip
- Zoom
- Width Shift
- Height Shift

---

## Confidence Feature Extraction

The system extracts additional confidence-related information from model predictions.

### Softmax Probabilities

```text
P(real)
P(fake)
```

### Confidence Margin

```text
CM = |P(real) - P(fake)|
```

Higher values indicate stronger prediction confidence.

### Entropy-Based Uncertainty

Entropy is used to quantify uncertainty in predictions.

```text
H(X) = - Σ p(x) log p(x)
```

Lower entropy indicates higher confidence, while higher entropy suggests uncertainty.

---

## Fuzzy Inference System

A Mamdani Fuzzy Inference System converts confidence metrics into an interpretable trust score.

### Inputs

- Confidence Margin
- Entropy

### Output

- Trust Score (0–100)

### Example Rules

- IF Confidence Margin is High AND Entropy is Low → Trust Score is Very High
- IF Confidence Margin is Medium AND Entropy is High → Trust Score is Low
- IF Confidence Margin is Low AND Entropy is High → Trust Score is Very Low

---

## Final Decision Framework

| Trust Score | Classification |
|-------------|---------------|
| 80 – 100 | Authentic |
| 40 – 79 | Suspicious |
| 0 – 39 | Likely Deepfake |

This three-level classification system helps identify uncertain predictions instead of forcing binary decisions.

---

## Results

### Model Performance

| Metric | Score |
|----------|----------|
| Accuracy | 77.17% |
| Precision | 0.7724 |
| Recall | 0.7717 |
| F1 Score | 0.7715 |

The model achieved balanced performance while improving interpretability through fuzzy trust scoring.

---

## Key Features

- Deepfake Image Classification
- Transfer Learning using MobileNetV2
- Entropy-Based Uncertainty Estimation
- Confidence Margin Analysis
- Fuzzy Logic Trust Scoring
- Explainable AI Approach
- Three-Level Risk Assessment
- Human-Readable Predictions

---

## Technologies Used

- Python
- TensorFlow / Keras
- MobileNetV2
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Scikit-Fuzzy
- Jupyter Notebook

---

## Future Improvements

- Video Deepfake Detection
- Vision Transformer (ViT) Integration
- EfficientNet-Based Models
- Real-Time Deployment
- Grad-CAM Explainability
- Cross-Dataset Validation
- Improved Confidence Calibration

---

## Repository Structure

```text
Deepfake-Detection-Project/
│
├── deepfake_detection.ipynb
├── Deepfake_Detection_Report.docx
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Author

Kabir Singh Banga

Bachelor's in Data Science & Data Analytics

---

## Project Highlights

This project demonstrates practical applications of:

- Deep Learning
- Computer Vision
- Transfer Learning
- Explainable AI (XAI)
- Fuzzy Logic
- Uncertainty Quantification
- Machine Learning Research

The combination of neural networks and fuzzy reasoning enables more transparent and trustworthy deepfake detection decisions.