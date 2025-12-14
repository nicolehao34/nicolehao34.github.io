---
title: "Cold Diffusion"
excerpt: "Re-implementation of cold diffusion model for image restoration<br/><img src='/images/Projects/cold-diffusion.png'>"
collection: portfolio
date: 2023-12-01
tags:
  - Deep Learning
  - Diffusion Models
  - Generative AI
  - PyTorch
---

## Overview

Re-implementation of the Cold Diffusion method from the NeurIPS 2022 paper "Cold Diffusion: Inverting Arbitrary Image Transforms Without Noise". This project explores an innovative approach to reversing image transformations without intermediate noise addition.

## Research Context

Traditional image restoration techniques often add noise to images and apply denoising processes, which can lead to detail loss. Cold Diffusion achieves inversion directly without the noise addition step, potentially preserving more image details.

## Core Contribution

The Cold Diffusion method provides a new way to reverse image transformations:

* **Direct Inversion**: Reverses transformations without noise addition
* **Arbitrary Transforms**: Works with various image distortions including blur
* **Quality Preservation**: Maintains image details better than noise-based methods

## Implementation

### Model Architecture

* **UNet Architecture**: Series of down-samples and up-samples with attention blocks
* **Residual Connections**: Maintain information flow throughout the network
* **Gaussian Diffusion**: Uses blur operator coupled with Gaussian kernels

### Training Details

* **Dataset**: MNIST handwritten digits
* **GPU Requirements**: T100 GPU recommended
* **Training Time**: 10,000 epochs (~1 hour), optimal results at ~100,000 epochs (~10 hours)

## Results & Analysis

* Model demonstrates ability to capture key aspects of digits even with limited training
* Shows potential of diffusion-like methods with minimal computational resources
* Some challenges with completely black or smudged generations
* Demonstrates that blur distortion can be harder to recover than Gaussian noise

## Applications

Potential applications in:

* Image restoration in forensic analysis
* Medical imaging (MRI, CT scans)
* General image quality enhancement without detail loss

## Future Work

* Extended training for improved performance
* Comparison with purely Gaussian noise distortion
* Exploration of other transformation types
* Performance optimization

## Links

* [GitHub Repository](https://github.com/nicolehao34/Cold-Diffusion)
* Topics: Deep Learning, Diffusion Models, Generative AI
