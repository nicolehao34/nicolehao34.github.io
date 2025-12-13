---
title: "Parallel CNN-Based Transient Stability Analysis"
excerpt: "Parallelized CNN for power grid stability assessment<br/><img src='/images/Projects/parallel-cnn-transient-stability.png'>"
collection: portfolio
date: 2023-11-01
---

## Overview

A parallel CNN-based transient stability assessment algorithm achieving >98% accuracy on real-world power grid datasets. The system uses parallelized training to significantly reduce training time while maintaining state-of-the-art performance.

## Problem Context

Transient stability analysis is critical for power grid reliability. It assesses whether a power system can return to equilibrium after a disturbance (like a fault or sudden load change). Traditional methods are computationally expensive, making real-time assessment challenging.

## Solution

This project implements a CNN-based approach that:

* Analyzes power grid data to predict stability
* Uses parallel computing to accelerate training
* Achieves comparable accuracy to existing state-of-the-art methods
* Enables faster real-time stability assessment

## Technical Approach

### Model Architecture

* **Convolutional Neural Network**: Designed for time-series power grid data
* **Parallel Training**: Distributed training across multiple GPUs
* **Optimization**: TensorFlow-based implementation with custom training loops

### Dataset

* **New England 39-bus system**: Real-world power grid test case
* **Features**: Voltage angles, frequencies, active/reactive power
* **Labels**: Stable/unstable classification

## Performance Metrics

* **Accuracy**: >98% on test set
* **Speed**: Significant training time reduction through parallelization
* **Scalability**: Tested on various system sizes

## Applications

* Real-time power grid monitoring
* Preventive control systems
* Grid stability prediction
* Emergency response systems

## Technical Stack

* **Framework**: TensorFlow
* **Computing**: Parallel GPU training
* **Language**: Python (Jupyter Notebooks)

## Research Collaboration

Collaborative project demonstrating the application of parallel computing and deep learning to power systems engineering.

## Future Work

* Parameter tuning optimization
* Extended scaling tests
* Application to larger grid systems
* Integration with real-time monitoring systems

## Links

* [GitHub Repository](https://github.com/nicolehao34/Parallel-CNN-based-Transient-Stability-Analysis)
* Topics: TensorFlow, Parallel Computing, CNN, Transient Analysis
