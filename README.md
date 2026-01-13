# Quantum–Classical Synergy in Medical AI

## A Dual-Phase Benchmark for Diagnostic Intelligence in Lung Cancer Classification

This repository contains the official implementation of research conducted at the Department of Robotics and Artificial Intelligence, School of Mechanical and Manufacturing Engineering (SMME), National University of Sciences and Technology (NUST). The work introduces a Hybrid Quantum–Classical (HQC) framework aimed at improving sensitivity, robustness, and generalization in pulmonary nodule classification from volumetric CT data.

## Overview

Conventional deep learning approaches for lung cancer diagnosis are constrained by representational saturation and severe class imbalance inherent in volumetric CT datasets. This work proposes a Hybrid Quantum–Classical architecture that integrates Variational Quantum Circuits (VQCs) to model higher-order feature correlations that are difficult to capture using purely classical methods.

### Key Contributions

* **Dual-Phase Evaluation Framework**
  A systematic comparison of Classical (CNN), Pure Quantum (QNN), and Hybrid (HQC) paradigms across low- and high-dimensional feature regimes.

* **CGAN-Based Class Balancing**
  Use of Conditional Generative Adversarial Networks to address class imbalance while preserving three-dimensional volumetric structure.

* **High-Dimensional Feature Integration**
  Validation of HQC performance using embeddings derived from a 3D Swin Transformer backbone.

* **Quantum Stability Auditing**
  Quantitative analysis using Mean Fidelity, Readout Variance, and Entanglement Entropy to assess quantum circuit stability.


## Methodology

### Phase 1: Modeling Paradigm Comparison

Phase 1 benchmarks the HQC model against state-of-the-art classical architectures, including EfficientNet, DenseNet121, and Inception V3, as well as pure Quantum Neural Networks. All models are evaluated using standardized low-dimensional feature representations.

### Phase 2: Generalization and Robustness Analysis

Phase 2 evaluates HQC robustness on high-dimensional feature embeddings (768 dimensions) extracted using a 3D Swin Transformer. Performance is compared against established machine learning classifiers, including Support Vector Machines, XGBoost, and CatBoost.

### Quantum Architecture

The quantum component is based on a Strongly Entangling Layer (SELL) ansatz:

* **Feature Encoding:** Angle embedding for numerical stability
* **Circuit Design:** Parameterized rotation layers with CNOT, SWAP, and Hadamard gates to ensure global entanglement
* **Optimization:** Parameter-shift rule for unbiased gradient estimation and mitigation of barren plateau effects


## Key Results

The Hybrid Quantum–Classical model consistently outperformed both classical and pure quantum baselines across all evaluation settings.

| Paradigm             | Architecture   | ROC-AUC | Recall (Sensitivity) |
| -------------------- | -------------- | ------- | -------------------- |
| Classical (Phase 1)  | EfficientNet   | —       | —                    |
| Pure Quantum         | QNN (SELL)     | —       | —                    |
| Hybrid (HQC)         | Proposed Model | ****    | ****                 |
| Swin + ML (Phase 2)  | SVM / XGBoost  | —       | —                    |
| Swin + HQC (Phase 2) | Proposed Model | ****    | ****                 |


## Technical Stack and Setup

### Core Dependencies

* **Quantum Simulation:** PennyLane with GPU-accelerated state-vector backend
* **Deep Learning:** PyTorch for CNN and 3D Swin Transformer pipelines
* **Optimization:** AdamW optimizer with Focal Loss for class imbalance handling
* **Compute Infrastructure:** High-performance GPUs for volumetric processing and quantum simulation


## Author and Citation

**Author:** Muhammad Bilal Khan
**Supervisor:** Dr. Saqib Nazir
**Institution:** National University of Sciences and Technology (NUST), Islamabad, Pakistan

If you use this code or associated research, please cite:

Khan, M. B. (2026). *Quantum–Classical Synergy in Medical AI: A Dual-Phase Benchmark for Diagnostic Intelligence in Lung Cancer Classification*. MS Thesis, National University of Sciences and Technology.
