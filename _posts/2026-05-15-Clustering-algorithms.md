---
layout: post
title: Notes on Clustering Algorithms and Evaluation Methods (WIP)
---

# Clustering algorithms: DBSCAN, HDBSCAN, and how to evaluate them

## TL;DR
Density-based clustering captures arbitrarily-shaped clusters and handles noise. DBSCAN is simpler, HDBSCAN builds a hierarchical density model and is more robust to variable densities. Evaluate with a mix of internal scores, external scores (when labels exist), stability/persistence, and domain-specific validation (visualization, cluster sizes, outliers).

---

## 1. Quick intuition

- DBSCAN: groups points where neighborhood density (eps, min_samples) is high. Points with too few neighbors are noise. Good when clusters have similar density and eps can be chosen.
- HDBSCAN: builds a hierarchy of density-connectivity across scales and extracts stable clusters. Fewer hard parameters; it can find clusters at variable densities and gives soft membership/outlier scores.

---

## 2. Parameters and practical tips

DBSCAN
- key params: eps (radius), min_samples (min points in eps neighborhood).
- choose min_samples >= D + 1 (D = number of features) often; 2*D is a conservative choice.
- choose eps via k-distance plot: plot distances to k = min_samples nearest neighbor, look for elbow.

HDBSCAN
- key params: min_cluster_size (minimum cluster you care about), min_samples (controls conservativeness; defaults to min_cluster_size if not set).
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
    - Silhouette score: cohesion vs separation, but can be misleading when many noise points or varying densities.
    - Davies–Bouldin index: lower is better.
    - Calinski–Harabasz: higher is better.
    - Caveat: internal scores assume cluster compactness; density-based clusters may violate these assumptions.

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

