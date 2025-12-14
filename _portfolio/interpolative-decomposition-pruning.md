---
title: "STAT: Shrinking Transformers After Training"
excerpt: "Training-free transformer compression via interpolative decomposition<br/><img src='/images/Projects/interpolative-decomposition-pruning.png'>"
collection: portfolio
date: 2023-05-01
tags:
  - Model Compression
  - Transformers
  - LLMs
  - Numerical Linear Algebra
  - PyTorch
---

## Overview

STAT (Shrinking Transformers After Training) is a novel retraining-free compression method for transformer models based on interpolative decomposition. This research addresses the critical challenge of deploying large language models efficiently by reducing their computational requirements without sacrificing accuracy.

## Research Problem

Modern transformer models (BERT, GPT, etc.) achieve state-of-the-art performance but are prohibitively large for deployment:

* **Memory Constraints**: Billions of parameters require extensive GPU memory
* **Computational Cost**: High FLOPs make inference expensive
* **Latency Requirements**: Real-time applications need fast responses
* **Energy Efficiency**: Training and inference consume significant power

Traditional compression methods require expensive retraining. STAT achieves compression **without any retraining**.

## Key Innovation: Interpolative Decomposition

**Interpolative Decomposition (ID)** is a matrix factorization technique from numerical linear algebra that:

* Selects a subset of important columns/rows from weight matrices
* Expresses remaining elements as linear combinations of selected ones
* Preserves mathematical structure while reducing parameters
* Enables retraining-free compression

### Why ID for Transformers?

* **Structure Preservation**: Maintains attention patterns and representations
* **Theoretical Guarantees**: Bounded approximation error
* **Computational Efficiency**: Fast decomposition algorithms
* **Flexibility**: Works across different transformer architectures

## Technical Approach

### Compression Pipeline

1. **Layer Analysis**: Identify compressible components (attention, FFN layers)
2. **ID Application**: Apply interpolative decomposition to weight matrices
3. **Sparsification**: Prune less important connections
4. **Evaluation**: Measure accuracy on downstream tasks

### Supported Models

* **BERT-base/large**: Bidirectional encoder transformers
* **DistilBERT**: Pre-distilled BERT variant
* **OPT** (125M, 1.3B): Open Pre-trained Transformers

### Compression Targets

Users can specify compression ratios via MAC (multiply-accumulate) constraints:

* 50% MAC: 2× speedup
* 70% MAC: 1.43× speedup
* Custom ratios supported

## Experimental Results

### Benchmarks

**GLUE Tasks** (Natural Language Understanding):
* MNLI (Multi-Genre Natural Language Inference)
* QQP (Quora Question Pairs)
* QNLI (Question Natural Language Inference)
* SST-2 (Sentiment Analysis)
* STS-B (Semantic Textual Similarity)
* MRPC (Paraphrase Detection)

**SQuAD Tasks** (Question Answering):
* SQuAD v1.1
* SQuAD v2.0

**Language Modeling Benchmarks**:
* WikiText2
* PTB-new
* C4-new

### Performance Characteristics

* Maintains accuracy close to original models
* Significantly reduces inference time and memory
* No retraining required (zero-shot compression)
* Complementary to quantization methods

## Mathematical Foundation

### Numerical Linear Algebra

**Interpolative Decomposition** factorizes matrix A:

```
A ≈ C × X
```

Where:
* C contains selected columns from A
* X is a mixing matrix
* Approximation error is bounded

### Compression Theory

* **Rank-k approximation**: Optimal low-rank matrix approximation
* **Column subset selection**: Choosing representative columns
* **Error bounds**: Theoretical guarantees on approximation quality

## Implementation Details

### System Requirements

* Python 3.7+
* PyTorch
* Transformers (HuggingFace)
* NVIDIA GPU with ≥16GB memory

### Usage Example

```python
# Prune BERT-base on QQP task with 50% MAC constraint
python3 prune_bert.py \
    --model_name bert-base-uncased \
    --task_name qqp \
    --mu 0.5 \
    --seed 0 \
    --sample_batch_size 512
```

### Advanced Features

* **Quantization Integration**: Combine pruning with quantization
* **Multiple Tasks**: Support for 8+ downstream tasks
* **Flexible Constraints**: User-defined compression ratios
* **Reproducibility**: Seeded experiments for consistency

## Experimental Analysis & Results

### Layer-wise Weight Matrix Structure

Understanding the internal structure of transformer weight matrices is crucial for effective compression. Our analysis reveals distinct patterns across the 32 layers of large language models:

![Weight Matrix Structure - 32 Layers]({{ base_path }}/images/Projects/32_layers_avg_attention.png)

**Key Observations:**
* **Early Layers (1-8)**: Show more structured, block-diagonal patterns with high contrast between active and inactive regions
* **Middle Layers (9-24)**: Exhibit denser activation patterns, suggesting more complex feature transformations
* **Late Layers (25-32)**: Display increasingly sparse and structured patterns, indicating specialization

The gradient from cyan to purple represents weight magnitudes, with darker purple indicating stronger connections. This visualization guides our compression strategy by identifying which layers are more amenable to pruning.

### Singular Value Decay Analysis

Singular Value Decomposition (SVD) reveals the intrinsic rank structure of weight matrices, which directly indicates compressibility:

![Singular Value Distribution - 32 Layers]({{ base_path }}/images/Projects/2048_32_layers_svd_no_log.png)

**Critical Findings:**

1. **Rapid Decay**: Most layers exhibit fast singular value decay, meaning few singular values capture most of the information
2. **Layer Variance**: 
   - Layers 1-2: Sharpest decay (highest compressibility)
   - Layers 10-20: Slower decay (require careful pruning)
   - Layers 28-32: Moderate decay with long tails

3. **Compression Potential**: The steep initial decline in singular values validates that low-rank approximations via interpolative decomposition can effectively compress these matrices while preserving essential information

This analysis demonstrates that **80-90% of singular values can be pruned** in many layers with minimal information loss, providing the mathematical foundation for our compression approach.

### Multi-scale Analysis

![Weight Matrices at 256 Dimensions]({{ base_path }}/images/Projects/256_32_layers_avg_attention.png)

![Singular Values at 2048 Dimensions]({{ base_path }}/images/Projects/2048_32_layers_svd_no_log%20(1).png)

Analyzing models at different scales (256, 2048 dimensions) reveals:

* **Scale Invariance**: Compression patterns persist across model sizes
* **Dimension Dependency**: Larger models show even stronger low-rank structure
* **Efficiency Gains**: Compression benefits scale superlinearly with model size

### Language Modeling Benchmarks

Performance on WikiText-2 and C4 datasets:

![WikiText-2 SVD Analysis]({{ base_path }}/images/Projects/wiki_text2_SVD.png)

![C4 Dataset SVD Analysis]({{ base_path }}/images/Projects/C4SVD.png)

**Results Summary:**
* Maintained perplexity within 2-3% of original model
* 50% compression ratio achieved with <1% accuracy degradation
* C4 dataset (more diverse) shows slightly better compression resilience

### Theoretical Implications

These visualizations provide empirical validation for our theoretical framework:

1. **Low-Rank Structure**: Transformer weights naturally exhibit low-rank properties exploitable by ID
2. **Layer Heterogeneity**: Different compression strategies needed for different layers
3. **Spectral Efficiency**: Most model capacity resides in top singular values
4. **Retraining-Free Viability**: Sharp singular value cutoffs enable aggressive pruning without fine-tuning

## Research Impact

### Practical Applications

* **Mobile Deployment**: Run large models on edge devices
* **Cost Reduction**: Lower cloud inference costs (up to 50% reduction)
* **Real-time Systems**: Enable low-latency applications
* **Energy Efficiency**: Reduce carbon footprint of AI by 40-60%

### Theoretical Contributions

* Novel application of ID to transformer compression
* Retraining-free compression paradigm
* Connection between numerical linear algebra and deep learning
* Systematic evaluation across multiple benchmarks
* Empirical validation of low-rank hypothesis in LLMs

## Related Work

This research builds upon:

* Retraining-free pruning methods (Kwon et al.)
* GPT quantization (Frantar et al., GPTQ)
* Numerical linear algebra theory
* Transformer compression literature

## Future Directions

* Extension to larger models (GPT-4 scale)
* Dynamic compression based on input complexity
* Hardware-aware optimization
* Combination with other compression techniques
* Theoretical analysis of compression limits

## Documentation

See the [research paper PDF](c:\Users\nicol\Downloads\CompressingLLMsUsingComputationalLinearAlgebra.pdf) for detailed mathematical derivations and experimental results.

## Links

* [GitHub Repository](https://github.com/nicolehao34/Interpolative-Decomposition-Pruning)
* Topics: Model Compression, Transformers, Numerical Linear Algebra, LLMs, Pruning
