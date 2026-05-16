# Biomedical Computational Imaging — StFX 2025

A morphological rule-based diagnostic framework for gastrointestinal disease detection 
using deep learning anomaly detection and interpretable machine learning.  
Developed as part of **CSCI 546** at St. Francis Xavier University.

---

## 👩‍🎓 Authors

**Gayathri Thirumoorthi** | x2024gpp@stfx.ca  
**Pradeep Reddy Lopinti** | x2024gqa@stfx.ca  
**Daniel Attah** | x2025ckz@stfx.ca  

Department of Computer Science, St. Francis Xavier University, Nova Scotia, Canada

---

## 📄 Project Title

**A Morphological Rule-Based Diagnostic Framework Using Spatial Anomaly Features  
for Gastrointestinal Disease Detection using the Kvasir Dataset**

---

## 🧠 Project Overview

This project develops an interpretable diagnostic pipeline for gastrointestinal disease 
detection using the **Kvasir endoscopy dataset**. An autoencoder is trained exclusively 
on healthy tissue images. When exposed to diseased images, it fails to reconstruct 
anomalous regions accurately — producing high reconstruction errors that act as 
disease indicators.

Spatial features are then extracted from these anomaly maps and used in simple, 
interpretable rule-based classifiers to distinguish healthy tissue from three 
gastrointestinal pathologies:

- 🔴 **Esophagitis** — diffuse mucosal inflammation
- 🟡 **Polyps** — localized tissue protrusions
- 🟠 **Ulcerative Colitis** — widespread mucosal inflammation

---

## 📂 Repository Structure
---

## 🔬 Methodology

### Phase 1 & 2 — Autoencoder Pipeline
- Autoencoder trained on **healthy images only** (70% train / 10% baseline / 20% test)
- Images resized to **224×224 pixels**
- Reconstruction error images and scaled subtraction anomaly maps generated
- Healthy baseline average subtracted to reduce background noise

### Phase 3 — Diagnostic Framework

**Task 1 — ROC Analysis**  
Each image is scored by summing all pixel values in its anomaly map.  
Thresholds selected using **Youden's J statistic** (J = TPR − FPR).

**Task 2 — Montage Visualization**  
Visual validation of the pipeline showing:  
`Original → Reconstructed → Reconstruction Error → Scaled Anomaly Map`

**Task 3 — Morphological Rule-Based Classification**  
Two spatial features extracted via **connected component analysis**:
- **S** — Size of the largest contiguous anomaly region
- **C** — Number of spatially separated anomaly regions

Three classifier rules evaluated:
- **Size-based rule** — flags if largest component exceeds threshold
- **Count-based rule** — flags if number of components exceeds threshold
- **Combined rule** — flags if either size OR count exceeds threshold

---

## 📊 Results

| Pathology | AUC | Accuracy | Sensitivity | Specificity |
|---|---|---|---|---|
| Polyps | 0.960 | 92.6% | High | High |
| Ulcerative Colitis | 0.968 | 93.3% | High | High |
| Esophagitis | 0.426 | 29.8% | Very Low | Very High |

**Key Finding:** The size-based rule performs excellently for polyps and ulcerative colitis 
(focal/large anomalies) but fails for esophagitis (diffuse, scattered anomalies) — 
demonstrating the importance of matching diagnostic features to disease morphology.

---

## 🛠️ Technologies & Tools

| Category | Tools / Libraries |
|---|---|
| Language | Python 3 |
| Deep Learning | Autoencoder (PyTorch / TensorFlow) |
| Image Processing | PIL, OpenCV, scikit-image |
| Analysis | scikit-learn, NumPy, Matplotlib |
| Evaluation | ROC Analysis, AUC, Youden's J Statistic |
| Dataset | [Kvasir Dataset](https://datasets.simula.no/kvasir/) |

---

## 📈 Key Concepts

- Unsupervised anomaly detection via autoencoders
- Connected component analysis for morphological feature extraction
- Interpretable / explainable AI (XAI) in medical imaging
- ROC curve analysis and threshold optimization
- Gastrointestinal endoscopy image classification

---

## 📬 Contact

For academic collaboration or questions about this project, feel free to reach out.

**GitHub:** [@GayathriThirumoorthi](https://github.com/)
