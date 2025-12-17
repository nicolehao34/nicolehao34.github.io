---
title: "CS & Applied Math Papers"
excerpt: "Curated collection of ML/AI research papers with learning resources<br/><img src='/images/Projects/cs-applied-math-papers.png'>"
collection: portfolio
date: 2025-01-01
---

## Overview

Latest CS & math papers with a focus on ML/AI and some supplemental resources. Curated with a focus on:

1. **Building Foundational Knowledge**: Resources to understand the mathematical and conceptual foundations for the latest research topics
2. **Understanding Frontier Research**: Latest papers pushing the boundaries of each field
3. **Identifying Limitations & Directions**: Critical analysis of current challenges and future research opportunities

Created by Nicole Hao, 2025

---

## Neural Tangent Kernels (NTKs)

Start with the following:

- [Lilian Weng's Blog on Math Behind NTKs](https://lilianweng.github.io/posts/2022-09-08-ntk/)
- [Understanding the Neural Tangent Kernel](https://www.eigentales.com/NTK/)
- [Neural Tangent Kernel, Applied Probability Notes](https://appliedprobability.blog/2021/03/10/neural-tangent-kernel/)
- [Prior's for Infinite Networks](https://link.springer.com/chapter/10.1007/978-1-4612-0745-0_2)

If you're interested in the functional analysis foundations of NTKs:
- [Similarity of Neural Network Models: A Survey of Functional and Representational Measures](https://arxiv.org/pdf/2305.06329)

Now you should be ready for the NTK foundational papers:
- [Neural Tangent Kernel: Convergence and Generalization in Neural Networks](https://arxiv.org/abs/1806.07572), NeurIPS 2018
- [Deep Neural Networks as Gaussian Processes](https://arxiv.org/abs/1711.00165), ICLR 2018
- [On Lazy Training in Differentiable Programming](https://arxiv.org/abs/1812.07956)

---

## O(3)-Equivariant Deep Networks

O(3) is the group of all rotations and reflections in 3D space. It's a mathematical concept that describes how objects can be moved in 3D without changing their fundamental properties (like distances between points).

An equivariant neural network, on the other hand, is one where the output changes in a specific, predictable way when the input is transformed by a group operation (like rotation or reflection). In simpler terms, if you rotate the input, the output will also be rotated in a corresponding manner.

Why are O(3) equivariant networks important? This is because they can learn generalizable features from 3D data, even if the training data only contains examples in a limited number of orientations. This reduces the amount of training data needed. Also, for tasks involving 3D objects, like predicting molecular properties or simulating physical systems, O(3)-equivariance ensures that the model's predictions are consistent with the laws of physics and geometry. They are also better at generalizing to unseen orientations of the input data.

### Mathematical Foundation on 3D Rotation Groups (Group Theory, Linear Algebra, Rotation Matrices)

- [3D Rotation Group](https://en.wikipedia.org/wiki/3D_rotation_group) - a 3D rotation group is a type of orthogonal group
- [Orthogonal Group](https://en.wikipedia.org/wiki/Orthogonal_group)
- [3D Rotations](http://mesh.brown.edu/rotations/) - Gabriel Taubin

### Latest Papers

- [Unifying O(3) Equivariant Neural Networks Design with Tensor-Network Formalism](https://arxiv.org/abs/2211.07482)
- [An Efficient Sparse Kernel Generator for O(3)-Equivariant Deep Networks](https://arxiv.org/abs/2501.13986)

---

## Real-time Adaptation Laws for Neural Networks

### Mathematical Foundations

- A college course in Differential equations
- Intermediate ODEs textbook: [Arnold's Ordinary Differential Equations](https://loshijosdelagrange.wordpress.com/wp-content/uploads/2013/04/vladimir-i-arnold-vladimir-i-arnold-roger-cooke-ordinary-differential-equations-1992.pdf)
- Dynamical systems
- Nonlinear dynamics is helpful too. I recommend Prof. Strogatz's [Nonlinear Dynamics and Chaos](https://www.stevenstrogatz.com/books/nonlinear-dynamics-and-chaos-with-applications-to-physics-biology-chemistry-and-engineering)

### Concept Definitions More Pertinent to Understanding Latest Research

- [Lyapunov function](https://en.wikipedia.org/wiki/Lyapunov_function)
- [Lyapunov stability](https://en.wikipedia.org/wiki/Lyapunov_stability)

### Latest Papers

- [A Tutorial on a Lyapunov-Based Approach to the Analysis of Iterative Optimization Algorithms](https://arxiv.org/abs/2309.11377)
- [Lyapunov-Based Real-Time and Iterative Adjustment of Deep Neural Networks](https://ieeexplore.ieee.org/document/9337905), IEEE Control Systems Letters

---

## Model Compression Techniques Through Numerical Linear Algebra

### Mathematical Foundation

- Linear algebra
- [Numerical Analysis, Numerical Linear Algebra, Trefethen and Bau](https://www.stat.uchicago.edu/~lekheng/courses/309/books/Trefethen-Bau.pdf), Chapter I - V

### Latest Papers

- [Model Preserving Compression for Neural Networks](https://arxiv.org/abs/2108.00065), NeurIPS

---

## Graph Neural Networks (GNNs)

GNNs are a class of neural networks designed to process data represented as graphs. Unlike traditional neural networks that work on Euclidean data like images or sequences, GNNs can directly operate on irregular data structures by modeling relationships between nodes and edges. They leverage a **message-passing** framework where nodes update their feature representations by aggregating information from their neighbors. This process allows them to capture complex relational information and learn a continuous representation, or **embedding**, of the graph's structure.

### Foundational Knowledge

- [Graph Neural Network - Wikipedia](https://en.wikipedia.org/wiki/Graph_neural_network): Provides a great overview of the basic building blocks of GNNs, including permutation equivariant layers, local and global pooling, and a discussion on the expressive power of GNNs.
- [Graph Neural Networks in TensorFlow](https://research.google/blog/graph-neural-networks-in-tensorflow/): A resource from Google Research that explains how GNNs can be trained on large datasets using a stream of subgraphs. It also touches on both supervised and unsupervised training methods.
- [Graph Neural Networks: A New Frontier](https://www.numberanalytics.com/blog/graph-neural-networks-new-frontier-cognitive-science-computing): This blog post explains the core components of a GNN, such as node representation, message passing, and aggregation, and provides a useful comparison with traditional neural networks.

### Frontier Research

- [Graph Neural Networks: Foundation, Frontiers and Applications](https://scholars.duke.edu/individual/pub1550511): This is a tutorial that covers a broad range of topics in GNNs, including fundamental concepts, new research frontiers, and emerging applications in fields like recommender systems and computer vision.
- [Recent Research Progress of Graph Neural Networks in Computer Vision](https://www.mdpi.com/2079-9292/14/9/1742): A comprehensive review of GNN applications in computer vision, focusing on image processing, video analysis, and multimodal data fusion. It highlights how GNNs capture inter-region dependencies and spatiotemporal dynamics.

---

## Physics-informed Neural Networks (PINNs)

Physics-informed neural networks (PINNs) are a type of neural network that incorporates the laws of physics into their training process. They do this by embedding governing equations, like partial differential equations (PDEs), into the neural network's loss function. This allows PINNs to find solutions to physical problems while requiring less training data than traditional data-driven models. They are particularly useful for solving forward and inverse problems in computational science.

### Foundational Knowledge - Start with These

- [Physics-informed Neural Networks - Wikipedia](https://en.wikipedia.org/wiki/Physics-informed_neural_networks): A great starting point that defines PINNs, explains their function approximation capabilities, and covers different types of problems they can solve, such as data-driven solution and discovery of PDEs.
- [Physics-Informed Neural Networks for Inverse PDE Problems](https://towardsdatascience.com/physics-informed-neural-networks-for-inverse-pde-problems/): This article provides an intuitive explanation of PINNs as a "cheat sheet" for a regular neural network, outlining how they use automatic differentiation and a physics-based loss function to achieve better results with less data.
- [Adaptive Physics-informed Neural Networks](https://arxiv.org/html/2503.18181v1): A review paper that discusses how advanced ML techniques, like transfer learning and meta-learning, can be integrated into PINNs to improve model adaptivity and address convergence challenges.

### Frontier Research

- [Physics-Informed Neural Networks: A Review of Methodological Evolution, Theoretical Foundations, and Interdisciplinary Frontiers Toward Next-Generation Scientific Computing](https://www.mdpi.com/2076-3417/15/14/8092): A comprehensive review paper that establishes a framework for understanding PINNs, covering methodological innovations, theoretical breakthroughs, and cross-disciplinary applications. It also proposes a roadmap for "PINN 2.0" including neuro-symbolic integration and quantum-accelerated optimization.
- [Physics-Informed Neural Networks with Hard Constraints for Inverse Design](https://epubs.siam.org/doi/10.1137/21M1397908): This paper introduces a method for solving topology optimization problems using PINNs with hard constraints, which is a significant advancement for engineering design.

### Notes & Limitations

- Training PINNs can be computationally expensive, especially for complex or multi-physics problems.
- Optimizing PINNs can be difficult, and their convergence properties are not as well understood as traditional methods.
- PINNs can struggle to solve high-frequency or multiscale problems and to incorporate noisy, sparse real-world data effectively.
- A key area of future research is improving PINN performance by integrating them with other methods, such as domain decomposition techniques (e.g., XPINNs), and exploring novel optimization strategies. The "PINN 2.0" vision focuses on neuro-symbolic integration, federated physics learning, and quantum-accelerated optimization.

---

## AI4Health

AI4Health (AI for Health) is an interdisciplinary field that applies machine learning and artificial intelligence to various aspects of healthcare. This includes tasks like medical image analysis, personalized treatment planning, drug discovery, and disease prediction. The field aims to improve the accuracy of diagnoses, enhance patient outcomes, and streamline clinical workflows.

### Foundational Knowledge

- [Artificial Intelligence In Health And Health Care: Priorities For Action](https://www.healthaffairs.org/doi/10.1377/hlthaff.2024.01003): This paper provides a historical context for AI in healthcare and identifies key policy-related domains. It discusses the evolution from early symbolic representations to modern deep neural networks for tasks like digital imaging and diagnostic reasoning.
- [(PDF) "Impact of Artificial Intelligence on Healthcare: A Review of Current Applications and Future Possibilities"](https://www.researchgate.net/publication/372960293_Impact_of_Artificial_Intelligence_on_Healthcare_A_Review_of_Current_Applications_and_Future_Possibilities): A review that clarifies the role of machine learning and natural language processing in healthcare. It covers applications in image analysis, diagnosis, and treatment planning, and discusses future possibilities like personalized medicine.

### Frontier Research

- [Evolution of Artificial Intelligence in Healthcare: a 30-year Bibliometric Study](https://www.frontiersin.org/journals/medicine/articles/10.3389/fmed.2024.1505692/full): A longitudinal study of AI publications in healthcare over three decades. It highlights the sustained growth in the field and the rise of new topics like COVID-19 analysis and new drug discovery.
- [Frontiers on Healthcare Research](https://frontiersonhealthcare.org/): This is a journal that focuses on bridging the gap between healthcare research and clinical applications. It's a good source for the latest peer-reviewed findings and strategies for improving patient care.

### Limitations & Directions

- **Data Dependency**: AI models are often trained on specific datasets from a single hospital or clinic, which can lead to poor performance when applied to data from different institutions. A key challenge is developing models that are more robust and can generalize to diverse populations.
- **Bias and Ethical Concerns**: AI models can be biased due to the data they're trained on, which can exacerbate healthcare disparities. The "black box" nature of many deep learning models makes it difficult to understand their decision-making process, leading to a lack of trust from both patients and clinicians.
- **Clinical Integration**: Many AI technologies show promise in research but have not been evaluated in clinical settings. Successful implementation requires seamless integration into existing workflows and proper training for healthcare professionals.
- **Human-in-the-loop Systems**: Currently, AI in healthcare should assist, not replace, doctors. Future research focuses on creating explainable AI (XAI) models that are transparent and trustworthy, and on developing systems where the final decision remains with a human clinician.

---

## Target Audience

* Graduate students in ML/AI
* Researchers entering new subfields
* Practitioners seeking deeper mathematical understanding

## Links

* [GitHub Repository](https://github.com/nicolehao34/cs-applied-math-papers)
* Topics: Machine Learning, Deep Learning, Applied Mathematics, Research Papers
