---
title: "Knowledge Distillation: Effects of Alpha"
excerpt: "Research on optimal alpha parameter for knowledge distillation<br/><img src='/images/Projects/knowledge-distillation-alpha.png'>"
collection: portfolio
date: 2023-08-01
---

## Overview

Research project exploring how the alpha parameter in knowledge distillation affects student model performance. Investigates the optimal balance between learning from ground-truth labels and teacher model predictions.

## Research Question

**How does varying the parameter alpha in knowledge distillation affect the accuracy of a student model compared to training it from scratch or purely from teacher predictions?**

## Hypothesis

There exists an optimal range of alpha values that yields higher accuracy than training with hard labels alone, by leveraging the additional structure provided by the teacher's soft predictions.

## Knowledge Distillation Concepts

### Core Components

* **Teacher Model**: Large, high-performing CNN trained to ~99% accuracy on MNIST
* **Student Model**: Lightweight CNN (16 and 32 filters)
* **Alpha (α)**: Scalar in [0,1] that interpolates between:
  - Student loss (ground-truth labels)
  - Distillation loss (soft teacher labels)

### Loss Functions

* **Distillation Loss**: Cross-entropy between softened student and teacher logits
* **Student Loss**: Cross-entropy between student predictions and hard labels
* **Combined Loss**: α × student_loss + (1-α) × distillation_loss

## Implementation

### Framework
* **TensorFlow/Keras**: Primary ML framework
* **Custom Distiller Class**: Subclass of `keras.Model` for custom loss computation
* **Temperature**: Tunable softening parameter (default = 3.0)

### Model Architecture

**Teacher Model**:
* 2-layer CNN with 256 and 512 filters
* Trained for 1000 epochs
* Achieved ~98.8% test accuracy

**Student Model**:
* Lightweight 2-layer CNN with 16 and 32 filters
* Trained for 100 epochs
* Various alpha values tested

## Experimental Results

### Key Findings

* **α = 1.0** (hard labels only): ~93.1% accuracy
* **α = 0.5** (balanced): Slightly better or comparable performance
* **Teacher Model**: ~98.8% accuracy baseline
* **Conclusion**: Knowledge distillation can enhance generalization with proper α tuning

### Performance Analysis

Models trained with intermediate alpha values demonstrated:
* Better generalization to test data
* Improved performance over pure hard-label training
* Benefits of combining teacher knowledge with ground truth

## Dataset

* **MNIST**: Handwritten digits (28×28 grayscale)
* **Training**: 60,000 samples
* **Testing**: 10,000 samples
* **Preprocessing**: Label perturbation for noise analysis

## Research Supervision

Independent research project conducted under the guidance of **Prof. Yunan Yang** (August 2023).

## Future Work

1. Explore different teacher model qualities and architectures
2. Test on more complex datasets (Fashion-MNIST, CIFAR-10)
3. Evaluate with additional metrics (precision, recall, F1)
4. Study denoising effects under increasing noise levels
5. Theoretical analysis using synthetic datasets

## Links

* [GitHub Repository](https://github.com/nicolehao34/Knowledge-Distillation-Effects-Of-Alpha)
* [Final Report PDF](https://github.com/nicolehao34/Knowledge-Distillation-Effects-Of-Alpha/blob/main/Knowledge_Distillation_Final_Report.pdf)
* Topics: Deep Learning, Knowledge Distillation, Model Compression
