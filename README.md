# Hybrid PCA-PINN Framework for Accurate and Transparent ECG Arrhythmia Detection

**Paper:** Hybrid PCA-PINN framework for accurate and transparent ECG arrhythmia detection
**Journal:** Applied Mathematics and Computation, Volume 519, 15 June 2026, Article 129935
**DOI:** https://doi.org/10.1016/j.amc.2025.129935
**Authors:** Fatemeh Moaven, Mostafa Abbaszadeh

## Citation

If you use this code, please cite:

Moaven, F., & Abbaszadeh, M. (2026). Hybrid PCA-PINN framework for accurate and transparent ECG arrhythmia detection. Applied Mathematics and Computation, 519, 129935.

BibTeX:
@article{Moaven2026,
  title = {Hybrid PCA-PINN framework for accurate and transparent ECG arrhythmia detection},
  author = {Moaven, Fatemeh and Abbaszadeh, Mostafa},
  journal = {Applied Mathematics and Computation},
  volume = {519},
  pages = {129935},
  year = {2026},
  doi = {10.1016/j.amc.2025.129935}
}

## Highlights

- First integration of PCA (50 statistical features) with PINN (2 interpretable parameters: c1 for propagation, c3 for damping) for ECG arrhythmia detection
- Achieves 95.43% accuracy with largest gains for challenging supraventricular arrhythmias
- PINN-derived parameters provide physiologically meaningful explanations, addressing the "black box" limitation of deep learning
- Compact 52-dimensional feature vector with lightweight MLP (128->64->32), offering orders-of-magnitude parameter reduction
- Processes raw ECG images (128x128), suitable for scanned/archival records
- Specifically improves discrimination between morphologically similar but clinically distinct arrhythmias (S ↔ V)

## Overview

This repository implements a hybrid physics-augmented pipeline for ECG arrhythmia detection that combines:

1. **PCA Features:** 50 statistical components from principal component analysis
2. **PINN Parameters:** 2 interpretable coefficients (c1, c3) estimated by minimizing a CLG-style PDE residual
3. **Lightweight MLP:** 128 -> 64 -> 32 layer classifier with ReLU and softmax

The resulting 52-dimensional feature vector provides both accuracy and physiological interpretability.

## Key Results

| Metric | PCA Only | PINN Only | Hybrid PCA-PINN |
|--------|----------|-----------|-----------------|
| Accuracy | 92.59% | 18.52% | 95.43% |
| Macro F1 | 93.00% | - | 95.00% |

### Per-Class F1 Improvements

| Class | PCA Only | Hybrid PCA-PINN |
|-------|----------|-----------------|
| S (Supraventricular) | 88% | 92% |
| V (Ventricular) | 90% | 93% |

### ROC-AUC Performance

- F, M, N, Q: ≈ 1.00 (near perfect)
- S, V: ≈ 0.99

## Interpretable PINN Parameters

| Parameter | Physical Meaning |
|-----------|------------------|
| c1 | Wave propagation / relaxation |
| c3 | Damping / cross-coupling |

