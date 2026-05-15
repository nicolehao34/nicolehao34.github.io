---
layout: post
title: Notes on Clustering Algorithms and Evaluation Methods (WIP)
---

TL;DR: 
Density-based clustering captures arbitrarily-shaped clusters and handles noise. This blog post covers how they work and their practical evaluation methods.

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) is a relatively simple density-based clustering algorithm, while HDBSCAN (Hierarchical Density-Based Spatial Clustering of Applications with Noise) builds a hierarchical density model and is more robust when clusters have varying densities.

These algorithms are commonly used for “grouping” features in modern applications, and they are becoming even more relevant as AI agents increasingly rely on long-context summarization and semantic organization. 

For developers, it is important to know how to evaluate clustering quality across multiple dimensions, including coherence, cluster distinctiveness, semantic consistency, stability, persistence, and domain-specific usefulness. 

Evaluation often combines internal metrics, external metrics when labels are available, and practical validation methods such as visualization, cluster size analysis, and outlier inspection.

---

## 1. Quick intuition

- DBSCAN: groups points where neighborhood density (eps, min_samples) is high (I'll explain the hyperparameters later). Points with too few neighbors are noise. 
- HDBSCAN: builds a hierarchy of density-connectivity across scales and extracts stable clusters. Fewer hard parameters; it can find clusters at variable densities and gives soft membership/outlier scores.

---

## 2. Parameters and practical tips

DBSCAN
- key params: 
    - eps (radius), 
    - min_samples (min points in eps neighborhood)
- choose min_samples >= D + 1 (D = number of features) often; 2*D is a conservative choice.
- choose eps via k-distance plot: plot distances to k = min_samples nearest neighbor, look for elbow.

HDBSCAN
- key params: 
    - eps
    - min_cluster_size (minimum cluster you care about), 
    - min_samples (controls conservativeness; defaults to min_cluster_size if not set).
- better for variable density; returns cluster_persistence (stability) and soft cluster membership (probabilities) plus outlier scores.

Preprocessing
- scale features (StandardScaler/RobustScaler).
- reduce dimensionality for very high-D data (PCA, UMAP) before density clustering; density estimation suffers in high dims.
- choose distance metric appropriate to data.

Complexity
- Both require neighborhood queries: with a KD-tree / ball-tree or approximate neighbors; worst-case O(n^2) but typically near O(n log n) with indexing.

---

## 3. Evaluation strategies

1. Internal metrics (no ground truth)
    - Silhouette score
        - For a sample $$i$$: $$a(i)$$ = mean intra‑cluster distance, $$b(i)$$ = min mean distance to points in any other cluster.
        - $$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}$$. The overall silhouette = $$\text{mean}_i s(i) \in [-1, 1]$$, higher is better.
    - Davies–Bouldin index (DB)
        - For $$k$$ clusters, let $$S_i$$ = average distance of points in cluster $$i$$ to its centroid $$\mu_i$$, and $$M_{ij} = \text{distance}(\mu_i, \mu_j)$$.
        - $$\text{DB} = \frac{1}{k} \sum_{i=1}^{k} \max_{j \neq i} \frac{S_i + S_j}{M_{ij}}$$. Lower is better.
    - Calinski–Harabasz index (CH)
        - Let $$n$$ be total samples, $$k$$ clusters, $$\mu$$ the global mean, $$\mu_i$$ the $$i$$-th cluster mean, and $$n_i$$ cluster sizes.
        - Between‑cluster dispersion: $$B = \sum_{i=1}^{k} n_i \|\mu_i - \mu\|^2$$.
        - Within‑cluster dispersion: $$W = \sum_{i=1}^{k} \sum_{x \in C_i} \|x - \mu_i\|^2$$.
        - $$\text{CH} = \frac{B / (k - 1)}{W / (n - k)}$$. Higher is better.
    - Caveat: these internal scores assume compact, globular clusters and can be misleading for density‑based or varying‑density cluster shapes and when many noise points exist. Consider combining them with density‑aware measures and visual checks.

2. External metrics (with labels)
    - Adjusted Rand Index (ARI), Adjusted Mutual Information (AMI): robust comparisons accounting for chance.
    - Use these when true labels exist for objective evaluation.

3. Density-aware / stability measures
    - For HDBSCAN use cluster_persistence (stability) to rank clusters.
    - Look at soft membership / outlier scores: high outlier score → treat as noise.
    - Subsample stability: repeat clustering on bootstrapped samples and measure cluster similarity (ARI between runs).

4. Practical / visual checks
    - Inspect cluster sizes (avoid tiny clusters unless meaningful).
    - Visualize with 2D embedding (UMAP / t-SNE) colored by cluster and outlier scores.
    - Domain-specific validation (e.g., time patterns, known labels, manual inspection).

---

## 4. Example workflow (Python)

```python
# pip install scikit-learn hdbscan umap-learn
import numpy as np
from sklearn.preprocessing import StandardScaler
from sklearn.neighbors import NearestNeighbors
from sklearn.cluster import DBSCAN
from sklearn.metrics import silhouette_score, adjusted_rand_score, adjusted_mutual_info_score
import hdbscan

# X: (n_samples, n_features) numpy array
X_scaled = StandardScaler().fit_transform(X)

# k-distance plot for DBSCAN (k = min_samples)
k = 5
nbrs = NearestNeighbors(n_neighbors=k).fit(X_scaled)
distances, _ = nbrs.kneighbors(X_scaled)
k_distances = np.sort(distances[:, -1])
# plot k_distances and pick eps at elbow

# DBSCAN
db = DBSCAN(eps=0.5, min_samples=k, metric='euclidean').fit(X_scaled)
labels_db = db.labels_  # -1 = noise

# HDBSCAN
hdb = hdbscan.HDBSCAN(min_cluster_size=10, min_samples=5, metric='euclidean')
hdb.fit(X_scaled)
labels_hdb = hdb.labels_
probabilities = hdb.probabilities_  # soft membership
outlier_scores = hdb.outlier_scores_
persistence = hdb.cluster_persistence_
```

Metrics (example)
```python
# internal
sil_db = silhouette_score(X_scaled[labels_db != -1], labels_db[labels_db != -1])

# external (if y_true exists)
ari_hdb = adjusted_rand_score(y_true, labels_hdb)
ami_hdb = adjusted_mutual_info_score(y_true, labels_hdb)
```

---

## 5. Practical checklist before production
- Scale data and consider dimensionality reduction.
- Use k-distance plot to choose DBSCAN eps; prefer HDBSCAN when densities vary.
- Inspect number of noise points and cluster sizes.
- Use bootstrapping/subsampling to test stability.
- Combine automated metrics (ARI/AMI if available) with visual & domain checks.
- If runtime is large, use approximate neighbors or sample data to tune params.

