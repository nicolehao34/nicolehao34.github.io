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

Re-implementation of "Cold Diffusion: Inverting Arbitrary Image Transforms Without Noise" (NeurIPS 2022) by Bansal et al. This project explores an innovative approach to generative modeling by replacing Gaussian noise with deterministic image transforms.

## Motivation: Do We Really Need Gaussian Noise?

Traditional "hot" diffusion models rely on Gaussian noise, making them stochastic processes. This project investigates a fundamental question: **Can we generate high-quality images using deterministic transforms like blurring, masking, or pixelation instead of random noise?**

![Traditional Diffusion Process]({{ base_path }}/images/Projects/cold-diffusion/HotDiffusion.png)

The answer is yes! Cold diffusion demonstrates that the random noise component can be **completely removed** from the diffusion framework and replaced with arbitrary deterministic transforms.

## Key Innovation: Improved Sampling Algorithm

### The Problem with Naive Sampling

Traditional diffusion models use a straightforward sampling approach (Algorithm 1):

```
Input: A degraded sample x_t
for s = t, t-1, ..., 1 do
    x̂_0 ← R(x_s, s)
    x_{s-1} = D(x̂_0, s-1)
end for
Return: x_0
```

This approach **fails** for cold diffusion because it doesn't account for the iterative nature of deterministic transforms.

### Improved Sampling (Algorithm 2)

The breakthrough comes from a corrective sampling strategy:

```
Input: A degraded sample x_t
for s = t, t-1, ..., 1 do
    x̂_0 ← R(x_s, s)
    x_{s-1} = x_s - D(x̂_0, s) + D(x̂_0, s-1)
end for
Return: x_0
```

![Algorithm Comparison]({{ base_path }}/images/Projects/cold-diffusion/Algo_comparison.png)

**Why does this work?** For linear degradations of the form $$D(x, s) \approx x + s \cdot e$$, the improved algorithm is extremely tolerant of errors in the restoration operator:

$$
\begin{align}
x_{s-1} &= x_s - D(R(x_s, s), s) + D(R(x_s, s), s - 1) \\\\
&= D(x_0, s) - D(R(x_s, s), s) + D(R(x_s, s), s - 1) \\\\
&= x_0 + s \cdot e - R(x_s, s) - s \cdot e + R(x_s, s) + (s - 1) \cdot e \\\\
&= x_0 + (s - 1) \cdot e = D(x_0, s - 1)
\end{align}
$$

Regardless of which restoration operator we use, our estimate will approximately equal the true latent at each step.

### Experimental Validation

![Sampling Comparison]({{ base_path }}/images/Projects/cold-diffusion/experiment_image.png)

**Top row**: Algorithm 1 fails to generate meaningful images
**Bottom row**: Algorithm 2 successfully samples high-quality images without any noise

## Core Contribution: A New Family of Generative Models

![Various Transforms]({{ base_path }}/images/Projects/cold-diffusion/Screenshot 2024-04-29 at 5.30.41 PM.png)

Cold diffusion works with arbitrary image transforms:
- **Blur**: Gaussian kernel convolution
- **Animorph**: Gradual transformation between images
- **Mask**: Progressively revealing masked regions
- **Pixelate**: Reducing resolution then restoring
- **Snow**: Adding snow-like artifacts

## Implementation

### Forward Diffusion Process

Gaussian blur implementation:
- Constructed list of Gaussian kernels (27×27) over 20 time steps (paper uses 300)
- Applied same kernel across all time steps for computational efficiency
- Implemented iterative deblurring using Algorithm 2

![Gaussian Kernels]({{ base_path }}/images/Projects/cold-diffusion/GaussianKernel.png)

### Model Architecture: Attention U-Net

![Model Architecture]({{ base_path }}/images/Projects/cold-diffusion/model-architecture.png)

**Key Components:**

1. **Time-step Embedding**
   - Sinusoidal embedding of blurring intensity $$t$$
   - Provides temporal context to the network

2. **Down-sampling Path**
   - 2 ConvNet blocks with Layer Norm and GELU activation
   - Attention blocks for capturing long-range dependencies

3. **Middle Block**
   - ConvNet block → Attention layer → ConvNet block
   - Processes features at lowest resolution

4. **Up-sampling Path**
   - 2 ConvNet blocks per level
   - Skip connections from corresponding downsampling stages
   - Attention blocks for feature refinement

5. **Final Convolution**
   - Maps to output image space

### Training Configuration

- **Datasets**: MNIST handwritten digits, CIFAR-10
- **GPU**: T100 GPU
- **Training Time**: 
  - 1,000 epochs: ~1 hour (preliminary results)
  - 100,000 epochs: ~10 hours (optimal results)
- **Metrics**: FID (Fréchet Inception Distance), SSIM (Structural Similarity Index)

![MNIST Examples]({{ base_path }}/images/Projects/cold-diffusion/MNIST_example.png) ![CIFAR-10 Examples]({{ base_path }}/images/Projects/cold-diffusion/CIFAR10.png)

## Results

### Deblurring Performance

![Deblurring Results]({{ base_path }}/images/Projects/cold-diffusion/Screenshot 2024-04-29 at 5.23.16 PM.png)

Comparison across MNIST, CIFAR-10, and CelebA datasets:
- **Left**: Degraded inputs $$D(x_0, T)$$
- **Middle-left**: Direct reconstruction $$R(D(x_0, T))$$
- **Middle-right**: Sampled reconstruction with Algorithm 2
- **Right**: Original images

### Training Progress: 1,000 Epochs

<table>
  <tr>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-xt-10.png" alt="Degraded"><br><b>Degraded</b></td>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-direct_recons-10.png" alt="Direct"><br><b>Direct</b></td>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-recon-10.png" alt="Algorithm 2"><br><b>Algorithm 2</b></td>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-og-10.png" alt="Original"><br><b>Original</b></td>
  </tr>
</table>

At 1,000 epochs, the model begins to capture digit structures but lacks fine detail.

### Training Progress: 100,000 Epochs

<table>
  <tr>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-xt-95.png" alt="Degraded"><br><b>Degraded</b></td>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-direct_recons-95.png" alt="Direct"><br><b>Direct</b></td>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-recon-95.png" alt="Algorithm 2"><br><b>Algorithm 2</b></td>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-og-95.png" alt="Original"><br><b>Original</b></td>
  </tr>
</table>

After extended training, reconstructions show significant improvement in quality and fidelity.

### Reconstruction Progression

![Progression 1]({{ base_path }}/images/Projects/cold-diffusion/all_1_90.png)
![Progression 2]({{ base_path }}/images/Projects/cold-diffusion/all_2_95.png)
![Progression 3]({{ base_path }}/images/Projects/cold-diffusion/all_1_195.png)
![Progression 4]({{ base_path }}/images/Projects/cold-diffusion/all_2_1127.png)

The progressive deblurring shows how the model iteratively refines images from completely degraded states back to sharp originals.

## Challenges and Observations

### High Fidelity, Low Diversity

The model demonstrates an interesting trade-off:
- Generates high-quality images for certain digit classes (0, 3, 6, 8)
- Shows bias toward specific digit types
- Some generated samples remain indecipherable

<table>
  <tr>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-og-99.png" alt="Original"></td>
    <td><img src="{{ base_path }}/images/Projects/cold-diffusion/sample-recon-99.png" alt="Reconstruction"></td>
  </tr>
</table>

### Unconditional Generation

- Implemented using Gaussian Mixture Model (GMM) for sampling channel-wise means
- More challenging than conditional reconstruction

### Blur vs. Noise

Our experiments suggest that **blur distortion is harder to recover from than Gaussian noise**, requiring more careful architecture design and longer training.

## Applications

Cold diffusion opens new possibilities for:

- **Image Restoration**: Forensic analysis, recovering damaged photos
- **Medical Imaging**: Deblurring MRI/CT scans without introducing noise artifacts
- **Super-Resolution**: Upscaling images through depixelation
- **Inpainting**: Filling masked regions deterministically
- **General Image Enhancement**: Quality improvement while preserving authentic details

## Lessons Learned

1. **Question Assumptions**: The requirement for Gaussian noise in diffusion models was not as fundamental as previously thought
2. **Architecture Matters**: Attention mechanisms and skip connections are crucial for long-range spatial dependencies
3. **Sampling Algorithms**: The choice of sampling algorithm dramatically affects generation quality
4. **Training Requirements**: 100,000 epochs may still not be sufficient for perfect generation across all classes
5. **Engineering Hygiene**: Well-designed helper functions and modular code are essential for complex deep learning projects

## Future Work

- Extended training beyond 100,000 epochs
- Systematic comparison between blur and Gaussian noise degradation
- Exploration of hybrid models combining multiple transform types
- Conditional generation with class labels
- Application to higher-resolution datasets (ImageNet, etc.)
- Performance optimization and inference speedup

## Links

* [GitHub Repository](https://github.com/nicolehao34/Cold-Diffusion)
* [Original Paper](https://arxiv.org/abs/2208.09392) (NeurIPS 2022)
* Topics: Deep Learning, Diffusion Models, Generative AI, Image Restoration
