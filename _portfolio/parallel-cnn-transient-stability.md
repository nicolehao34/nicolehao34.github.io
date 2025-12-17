---
title: "Parallel CNN-Based Transient Stability Analysis"
excerpt: "Parallelized multi-channel CNN for power grid transient stability assessment (98.8% test accuracy)<br/><img src='/images/Projects/parallel-cnn-transient-stability.png'>"
collection: portfolio
date: 2023-11-01
---

## Overview

Parallel Convolutional Neural Network (CNN)-based **Transient Stability Assessment (TSA)** for power grids, implemented as a **multi-channel time-series classifier** with **data-parallel training** to reduce retraining time while preserving high accuracy (**98.8% test accuracy** on the NE 39-bus benchmark).

This work was developed as a CS 6230 project with Jerry Feng.

## Problem Context

Power networks can be modeled as a graph (generation, transmission, demand nodes) with dynamic features such as voltage, angles, rotor speed, and power flows.

**Transient stability** asks whether the system can return to equilibrium after disturbances (generator outages, load changes, short circuits). In operations, we want a prediction that is both **accurate** and **fast**, using **immediate (<1s) post-fault time-series features**, and a pipeline that can be **retrained frequently** as new disturbances/status conditions appear.

Motivating gaps highlighted in the project:

- PDE time-domain simulation is accurate but slow
- Some fast pattern-recognition classifiers (e.g., SVM) sacrifice accuracy
- Many prior works emphasize accuracy but do not benchmark training time, scaling, or provide end-to-end open-source implementations

## Data & Experimental Setup

**Benchmark system:** New England IEEE **39-bus** system

**Signals / channels:** 10 generators, each with **5 channels**

**Disturbances:** three-phase short-circuit faults (0.1–0.3s clearing times), with 80–120% generation/load profiles

**Dataset size & class balance:** 12,852 examples labeled stable/unstable (≈58% stable, 42% unstable)

## Solution

A CNN-based TSA pipeline that:

- Treats TSA as **multi-channel time-series classification** (stable vs. unstable)
- Uses **data-parallel training** to accelerate retraining and support rolling updates
- Targets strong benchmark accuracy while emphasizing training-time scalability

## Technical Approach

### Model & Training

- **Multi-channel CNN** for post-fault trajectories
- **Batch normalization** to improve training speed, performance, and stability
- **Lower data requirement** than some baselines: uses generator-bus channels (10 generator buses) rather than requiring signals from all 39 buses

### Parallelization Methods

- **Data-parallel batch splitting** with `tf.distribute.MirroredStrategy()` to shard each Keras batch across available GPUs
- **Logical batch scaling** (optionally scale batch size by `num_replicas_in_sync` to keep per-GPU batch constant)
- **Im2Col convolution optimization** via a custom `Im2ColConv2D` layer (extract patches → reshape → GEMM → reshape back) to leverage high-efficiency matrix multiplies on GPU
- **Gradient AllReduce** to average gradients across replicas without manual synchronization, maintaining consistent weight updates vs. single-device training

## Results

- **Test accuracy:** **98.8%** on the NE 39-bus system
- Reported as an improvement over older NN-based approaches and on par with multi-channel CNN methods in the literature (as summarized in the presentation)

## Scaling Tests

Below are scaling experiments showing how training time grows with training set size while accuracy remains strong.

### Scaling Test Results (Time vs. Train Size, Accuracy vs. Train Size)

<img src="/images/Projects/parallel-cnn-scaling-test-results.png" alt="Scaling Test Results: training time and accuracy vs train size" width="700"/>

### Baseline: MLP Scaling (Training Time & Accuracy)

<img src="/images/Projects/parallel-cnn-mlp-scaling.png" alt="MLP scaling: training time and accuracy vs train size" width="700"/>

> **Note:** Place the two images above in your site at:
> - `/images/Projects/parallel-cnn-scaling-test-results.png`
> - `/images/Projects/parallel-cnn-mlp-scaling.png`

## Applications

- Real-time grid stability monitoring
- Preventive / corrective control support
- Emergency response decision support
- Fast screening of contingencies under changing operating conditions

## Technical Stack

- **Framework:** TensorFlow / Keras (`tf.distribute.MirroredStrategy`)
- **Language:** Python (Jupyter Notebooks)
- **Compute:** Multi-GPU data parallelism + optimized convolution (Im2Col + GEMM)

## Limitations & Future Work

- Validate scaling with throughput metrics (e.g., images/sec) as GPUs increase; tune batch size and learning rate
- Evaluate on larger systems (e.g., Polish 2383-bus) to study overheads and scaling limits
- Extend beyond binary stability to multi-class (e.g., oscillatory vs. aperiodic instability modes)
- Explore alternative architectures: GNNs for topology-aware modeling; CNN+GAN hybrids reported to improve accuracy; and parallelization beyond data-parallelism

## Links

- [GitHub Repository](https://github.com/nicolehao34/Parallel-CNN-based-Transient-Stability-Analysis)
- Topics: TensorFlow, Parallel Computing, CNN, Power Systems, Transient Stability
