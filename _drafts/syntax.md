---
layout: post
title: Syntax
---

Learning is about generalization. Language learning is about generalization to sentences not seen before. 
One aspect of this is **syntacic generalization**, 

## Papers:
- **R**epresentations of Syntax [MASK] Useful: Effects of Constituency and Dependency Structure in Recursive LSTMs
- **O**verestimation of Syntactic Representation in Neural Language Models
- **S**yntactic Data Augmentation Increases Robustness to Inference Heuristics
- **A** Systematic Assessment of Syntactic Generalization in Neural Language Models
- **D**oes Syntax Need to Grow on Trees? Sources of Hierarchical Inductive Bias in Sequence-to-Sequence Networks

| **Paper** | **Task** | **Metric** | **Models** | **Findings** |
|-|-|-|-|-|
| R | verb-object agreement | accuracy | sequence & tree LSTMs | Tree structure & augmentation help |
| O | syntactic priming | perplexity change | sequence LSTM, n-gram | Task too easy for baselines  |
| S | entailment inference | accuracy | BERT | Augmentation helps |
| A | 6 tasks | accuracy | GPTs, sequence RNNs, n-gram... | GPTs > RNNs, model > data |
| D | question formulation | accuracy (first word) | sequence & tree RNNs | Tree structure helps, not augmentation* |
