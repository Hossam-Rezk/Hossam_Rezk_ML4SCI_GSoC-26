# DeepLense — GSoC 2026 Evaluation Tasks

**Applicant:** Hossam Rezk · Ain Shams University, Cairo, Egypt  
**Project:** LSST Data Processing Pipeline for DeepLense Workflows · ML4SCI

---

## Results Summary

| Task | Accuracy | AUC |
|------|----------|-----|
| Common Test I — Multi-Class Lens Classification | 95.20% | 0.9940 (mean) |
| Specific Test V — Gravitational Lens Finding | 97.24% | 0.9898 |

---

## Repository Structure
```
├── Test_I_Classification.ipynb   # Multi-class gravitational lens classification
├── Test_V_Lens_Finding.ipynb     # Binary gravitational lens finding
└── README.md
```

---

## Test I — Multi-Class Gravitational Lens Classification

Three-class classification: **No Substructure**, **Subhalo (Sphere)**, and **Vortex**. Fine-tuned ResNet18 with Dropout(0.4), weight decay, and augmentation on single-channel `.npy` lensing images.

**Key decisions:** Full fine-tuning (frozen layers gave 33% accuracy) · One-vs-Rest ROC strategy · Early stopping across 15 epochs.

| Class | AUC |
|-------|-----|
| No Substructure | 0.9947 |
| Subhalo (Sphere) | 0.9911 |
| Vortex | 0.9962 |
| **Mean** | **0.9940** |

---

## Test V — Gravitational Lens Finding

Binary classification on three-filter (g, r, i) images with a 16.6× class imbalance (28,675 non-lenses vs 1,730 lenses). Fine-tuned ResNet18 with a three-layer imbalance strategy: weighted sampler + `pos_weight` in loss + augmentation. AUC used as early-stopping criterion.

**188 out of 195 real lenses correctly identified — 96.4% lens recall.**

---

## Contact

- **Email:** hossam.a.rezk@gmail.com  
- **GSoC Project:** ML4SCI · DeepLense · LSST Data Processing Pipeline
