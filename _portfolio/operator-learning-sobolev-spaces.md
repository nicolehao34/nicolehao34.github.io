---
title: "Operator Learning in Sobolev Spaces"
excerpt: "Functional analysis of neural operators with quantitative error bounds<br/><img src='{{ base_path }}/images/Projects/operator-learning-sobolev-spaces.png'>"
collection: portfolio
date: 2025-06-01
---

## Overview

This project bridges functional analysis and operator learning to rigorously analyze how deep neural networks approximate nonlinear operators between Sobolev spaces. The research characterizes the interplay between neural network architecture, optimization dynamics, and approximation error in high-dimensional function spaces, with applications to learning solution operators of partial differential equations (PDEs).

## Research Motivation

In traditional machine learning, we learn mappings from inputs to outputs (e.g., predicting house prices from features). However, many scientific problems require learning operators that map entire functions to functions:

* **Climate Modeling**: Today's temperature field → Tomorrow's temperature field
* **Material Science**: Applied stress field → Material deformation field
* **Fluid Dynamics**: Initial velocity field → Time-evolved velocity field

This is **operator learning** – learning machines that transform whole functions rather than individual data points.

## What Are Sobolev Spaces?

Sobolev spaces (H^s) are function spaces that measure not just function values but also their derivatives. They provide the natural mathematical framework for:

* Quantifying smoothness of functions
* Analyzing PDE solutions
* Establishing approximation error bounds
* Characterizing neural network expressiveness

## Research Contributions

### 1. Theoretical Foundations

* **Universal Approximation Theorems**: Prove that neural networks can approximate operators mapping between Sobolev spaces H^s(D) → H^t(D')
* **Quantitative Error Bounds**: Establish explicit scaling laws relating:
  - Network depth and width
  - Input/output function regularity
  - Approximation error in Sobolev norms

### 2. Numerical Validation

Experiments on the **1D Burgers' Equation** using Fourier Neural Operators (FNOs):

* Learn operators mapping initial conditions to PDE solutions
* Validate theoretical depth-width-error tradeoffs
* Analyze optimization dynamics and generalization

### 3. Architecture Analysis

* **Width vs. Depth Scaling**: Empirical characterization of parameter efficiency
* **Learning Curves**: Training dynamics across different architecture sizes
* **Error vs. Parameters**: Quantitative relationships validated on real PDEs

## Technical Implementation

### Neural Operator Architecture

**Fourier Neural Operator (FNO)** architecture:
* Spectral layer representations in Fourier space
* Global convolution kernels via FFT
* Parametric spectral transforms

### Experimental Setup

* **PDE**: 1D Burgers' equation with viscosity
* **Training Data**: Multiple initial conditions
* **Evaluation**: L² and H¹ Sobolev norms
* **Framework**: PyTorch with custom spectral layers

## Key Results

### Theoretical Advances

* Explicit approximation rates for operator learning
* Sobolev norm error bounds depending on network architecture
* Connection between functional analysis and deep learning theory

### Numerical Findings

* FNO architectures achieve strong empirical performance
* Width scaling offers better parameter efficiency than depth for operator learning
* Learning curves show characteristic double-descent behavior
* Best models achieve low relative error on held-out test data

## Repository Structure

```
├── theory/
│   └── results.pdf          # Proofs and theoretical background
├── numerics/
│   ├── train_fno.py        # Full training pipeline
│   ├── parameter_sweep.py   # Hyperparameter experiments
│   └── solver.py           # Spectral Burgers solver
├── *.pt                     # Trained model checkpoints
└── *.png                    # Visualization results
```

## Experimental Results & Analysis

### Training Dynamics and Convergence

Our experiments reveal complex optimization dynamics when training Fourier Neural Operators on the 1D Burgers' equation:

![Learning Curves by Architecture Size]({{ base_path }}/images/Projects/fno_learning_curves_by_size.png)

**Key Observations:**

The learning curves demonstrate distinct convergence patterns across different FNO architectures:

* **Small Models** (modes=8, width=32): Rapid initial convergence but plateau at higher error
* **Medium Models** (modes=12-16, width=48-64): Balanced convergence with moderate final error
* **Large Models** (modes=24, width=96): Slowest initial convergence but achieve lowest final error

All architectures exhibit smooth convergence on this problem, validating the stability of spectral-based operator learning.

### Long-Run Training Behavior

Extended training reveals periodic instabilities and recovery patterns:

![Long-Run Learning Curve]({{ base_path }}/images/Projects/big_fno_longrun_learning_curve.png)

**Critical Insights:**

1. **Periodic Spikes**: Sharp increases in $H^1$-loss occur at regular intervals (~200 epochs)
2. **Recovery Dynamics**: Model consistently recovers to lower error states after spikes
3. **Long-Term Trend**: Overall downward trajectory despite local instabilities
4. **Convergence Threshold**: Achieves $10^{-8}$ test error after ~1000 epochs

This behavior suggests the optimization landscape contains saddle points or local minima that the optimizer periodically escapes, ultimately finding better solutions.

### Scaling Laws: Theory Meets Practice

One of our central theoretical results establishes approximation error bounds scaling with network parameters. Empirical validation:

![Error vs. Parameters (Best Epoch)]({{ base_path }}/images/Projects/fno_best_epoch_error_vs_params.png)

**Theoretical Prediction:**

For operator $\mathcal{G}: H^s \to H^t$ with regularity $s, t \geq 0$, the FNO approximation error satisfies:

$$
\| \mathcal{G} - \mathcal{G}_\theta \|_{H^t} \lesssim CN^{-\alpha}
$$

where:
* $N$ is the number of parameters
* $\alpha > 0$ is the convergence rate
* $C$ depends on operator smoothness

**Empirical Findings:**

* **Power Law Fit**: $CN^{-1.11}$ closely matches theoretical predictions
* **Optimal Regime**: Around $5 \times 10^5$ parameters (modes=16, width=64)
* **Diminishing Returns**: Beyond $10^6$ parameters, error reduction slows
* **Double-Descent**: Slight error increase for very large models before final descent

The close agreement between theory ($\alpha \approx 1$) and experiment ($\alpha = 1.11$) validates our Sobolev approximation framework.

### Architecture Comparison: Width vs. Depth

![Learning Curves - Multiple Architectures]({{ base_path }}/images/Projects/fno_learning_curves_by_size_best_epoch_sweep.png)

Comparing architectures reveals fundamental insights about spectral operator learning:

| Architecture | Modes | Width | Parameters | Best $H^1$-Error |
|-------------|-------|-------|------------|------------------|
| Small | 8 | 32 | $\sim 50k$ | $3 \times 10^{-7}$ |
| Medium-S | 12 | 48 | $\sim 150k$ | $1.5 \times 10^{-7}$ |
| Medium-L | 16 | 64 | $\sim 400k$ | $5 \times 10^{-8}$ |
| Large | 24 | 96 | $\sim 1.5M$ | $1.5 \times 10^{-8}$ |

**Key Insights:**

* **Width Scaling**: Increasing width (spectral modes) has greater impact than increasing depth
* **Spectral Bias**: FNO benefits from more Fourier modes to capture solution complexity
* **Parameter Efficiency**: Medium models offer best error-to-parameter ratio
* **Convergence Speed**: Smaller models train faster but with lower final accuracy

### Model Size Ablation Study

![Error vs. Model Size]({{ base_path }}/images/Projects/fno_error_vs_params.png)

Systematic variation of model capacity reveals:

* **Absolute $H^1$-Error**: Decreases monotonically with parameters
* **Relative $H^1$-Error**: Remains remarkably stable (~0.3%) across all sizes
* **Generalization**: No overfitting observed even for largest models
* **Data Efficiency**: Small models achieve good relative performance with limited capacity

The flat relative error curve indicates the operator learning task has favorable generalization properties - models of all sizes learn the correct structure, with capacity determining precision.

### Solution Quality Visualization

![Burgers Equation Solution and Derivative]({{ base_path }}/images/Projects/figure_1.png)

**Left Panel - Solution at $t=1$:**
* Blue: Initial condition $u(x,0)$
* Orange: True solution $u(x,1)$ from spectral solver
* Green (dashed): FNO prediction

**Right Panel - Spatial Derivative at $t=1$:**
* Orange (solid): True $\partial_x u$
* Orange (dashed): FNO predicted $\partial_x u$

**Analysis:**

The FNO achieves remarkable accuracy:
* **$L^2$ Error**: $< 10^{-6}$ for solution values
* **$H^1$ Error**: $< 10^{-7}$ including derivatives
* **Shock Capture**: Accurately resolves steep gradients in Burgers' equation
* **Sobolev Regularity**: Maintains smoothness properties of true solution

This validates that neural operators learn not just function values but the entire operator structure, including derivative information.

### Long-Term Training Stability

![Extended Training - Multiple Checkpoints]({{ base_path }}/images/Projects/fno_longrun_learning_curves.png)

Comparing checkpoints at 100, 500, and 1000 epochs:

* **100 Epochs** (Blue): Early convergence, $H^1$-error $\sim 10^{-6}$
* **500 Epochs** (Orange): Intermediate refinement, sporadic spikes
* **1000 Epochs** (Green): Final convergence, stable $10^{-8}$ error

The progression demonstrates:
* Consistent improvement with extended training
* Periodic instabilities that lead to better local minima
* Eventual stabilization at near-machine-precision accuracy

### Theoretical Implications

These experimental results provide strong empirical support for our main theoretical contributions:

1. **Sobolev Approximation Bounds**: The observed $N^{-1.11}$ scaling validates our theoretical error bounds in $H^1$ norm

2. **Universal Approximation**: FNOs successfully approximate the Burgers solution operator across diverse initial conditions

3. **Spectral Efficiency**: Fourier-based parameterization naturally captures smooth operator structure

4. **Generalization**: Strong performance on held-out data confirms operators learn underlying PDE structure, not memorization

## Applications

This research framework applies to:

* **Climate Science**: Learning weather/climate operators
* **Engineering**: Material response operators
* **Computational Physics**: Fast PDE surrogate models
* **Inverse Problems**: Recovering parameters from observations
* **Control Theory**: Learning dynamical system operators

## Mathematical Background Required

* Functional Analysis (Sobolev spaces, operator theory)
* Partial Differential Equations
* Deep Learning (neural network architectures)
* Numerical Analysis (spectral methods)

## Recent Updates

* **December 2025**: Compiled training scripts, added trained model checkpoints
* **June 2025**: Initial numerical implementations and experiments
* **May 2025**: Established theoretical framework

## Future Directions

* Extension to higher-dimensional PDEs
* Multi-physics operator learning
* Incorporating physical constraints
* Uncertainty quantification for operator learning
* Real-world scientific applications

## Links

* [GitHub Repository](https://github.com/nicolehao34/Operator-Learning-in-Sobolev-Spaces)
* [Research Paper](https://www.researchgate.net/publication/398610085_Quantitative_Sobolev_Approximation_Bounds_for_Neural_Operators_with_Empirical_Validation_on_Burgers'_Equation)
* Topics: Applied Mathematics, Numerical Methods, Functional Analysis, Neural Operators, PDEs
