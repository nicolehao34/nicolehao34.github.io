---
title: "Detecting and Classifying Solar Flares in High-Resolution Solar Spectra using Supervised Machine Learning"
collection: publications
category: manuscripts
permalink: /publication/2024-06-solar-flares
excerpt: 'This paper presents a novel, standardized procedure for classifying solar flares using supervised machine learning, with implications for both solar physics and exoplanet research.'
date: 2024-06-01
venue: 'The Astrophysical Journal'
paperurl: 'https://arxiv.org/abs/2406.15594'
citation: 'Nicole Hao, Laura Flagg, Ray Jayawardhana. (2024). &quot;Detecting and Classifying Solar Flares in High-Resolution Solar Spectra using Supervised Machine Learning.&quot; <i>The Astrophysical Journal</i>.'
---

This research developed a full data pipeline for classifying solar flares, including processing high-resolution HARPS-N spectra, implementing Principal Component Analysis (PCA) for dimensionality reduction, and using undersampling to correct for data imbalance. We trained and optimized a C-Support Vector Classification (SVC) model with an RBF kernel, performing a GridSearch for hyperparameter tuning and validating the results with confusion matrices, precision, and recall.

![Principal Component Analysis](/images/publications/combined_principal_components.png)

![Confusion Matrix for SVC Model](/images/publications/AvgMatrix_SVC_rbf.png)
