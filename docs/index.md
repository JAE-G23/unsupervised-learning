# Unsupervised Learning for Sea Ice and Lead Classification

**GEOL0069 (UCL Earth Sciences) — Week 4 Coursework**

This project applies **unsupervised learning** to classify **sea ice and leads** using Earth Observation data:
- **Sentinel-2** optical imagery (RGB bands)
- **Sentinel-3** altimetry waveforms

Clustering methods used:
- **K-means**
- **Gaussian Mixture Models (GMM)**

---

## Key Results


<p align="center">
  <img src="outputs/clusterings.png" width="850">
</p>

<p align="center">
  <em>Comparison of K-means and GMM clustering applied to Sentinel-2 RGB bands.</em>
</p>

### 1. Waveform Alignment

#### GMM – Cluster Alignment
<p align="center">
  <img src="outputs/GMM/gmm_crosscorrelation_alignment.png" width="700">
</p>

#### K-means – Cluster Alignment
<p align="center">
  <img src="outputs/K-means/kmeans_crosscorrelation_alignment.png" width="700">
</p>

---

### 2. Mean Echo Shape and Variability

#### GMM
<p align="center">
  <img src="outputs/GMM/gmm_mean_sd.png" width="700">
</p>

#### K-means
<p align="center">
  <img src="outputs/K-means/kmeans_mean_sd.png" width="700">
</p>

---

### 3. Quantitative Evaluation (Confusion Matrices)

#### GMM vs ESA
<p align="center">
  <img src="outputs/GMM/gmm_confusion_matrix.png" width="600">
</p>


#### K-means vs ESA
<p align="center">
  <img src="outputs/K-means/kmeans_confusion_matrix.png" width="600">
</p>


---

## Open the Notebook in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JAE-G23/unsupervised-learning/blob/main/notebooks/Week4_Unsupervised_Learning_Methods.ipynb)

---

## Repository

- [GitHub Repository](https://github.com/JAE-G23/unsupervised-learning)
- [Full documentation and methods (README)](../README.md)
