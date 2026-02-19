<!-- Back to top link -->
<a name="readme-top"></a>

# Unsupervised Learning for Sea Ice and Lead Classification
## Project Overview
This project explores the use of **unsupervised learning methods** to classify **sea ice and leads** using Earth Observation data.
Two main datasets are analysed:
- Sentinel-2 optical imagery (RGB bands)
- Sentinel-3 altimetry waveforms

The objectives of this project are:
- Cluster sea ice and lead observations with:
  - **K-means**
  - **Gaussian Mixture Models (GMM)**
- Compute:
  - Mean echo shape per class
  - Standard deviation of waveforms
- Compare clustering results with ESA official classifications using a confusion matrix.

<!-- TABLE OF CONTENTS -->
<details>
  <summary><strong>Table of Contents</strong></summary>
  <ol>
    <li>
      <a href="#unsupervised-learning">Unsupervised Learning</a>
    </li>
    <li>
      <a href="#methods">Methods</a>
      <ul>
        <li><a href="#k-means-clustering">K-means Clustering</a></li>
        <li><a href="#gaussian-mixture-models-gmm">Gaussian Mixture Models (GMM)</a></li>
      </ul>
    </li>
    <li>
      <a href="#applications">Applications</a>
      <ul>
        <li><a href="#image-classification-sentinel-2">Image Classification (Sentinel-2)</a></li>
        <li><a href="#altimetry-classification-sentinel-3">Altimetry Classification (Sentinel-3)</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#installation">Installation</a></li>
        <li><a href="#data-requirements">Data Requirements</a></li>
      </ul>
    </li>
    <li><a href="#disclaimer">Disclaimer</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#references">References</a></li>
  </ol>
</details>


## Unsupervised Learning
In this task, we deliberately apply unsupervised methods even though ESA labels exist. The goal is to test whether the physical signal itself naturally separates into two classes.
## Methods

<p align="center">
  <img src="outputs/clusterings.png" width="700">
</p>

<p align="center">
  <em>Comparison of K-means and GMM clustering applied to Sentinel-2 RGB bands.</em>
</p>

## K-means Clustering
K-means is a widely used unsupervised algorithm that partitions data into k predefined clusters. The algorithm assigns each data point to the nearest centroid and iteratively updates the centroid locations to minimise within-cluster variation. MacQueen (1967)

### Why K-means?
- No prior knowledge of data structure is required.
- It is simple to implement.
- It scales efficiently to large datasets.

### Algorithm Overview
1. Choose the number of clusters (k).
2. Initialize cluster centroids.
3. Assign each point to the nearest centroid.
4. Recalculate centroids as the mean of assigned points.
5. Repeat until convergence.

K-means may converge to a local optimum depending on centroid initialization, it provides a strong and interpretable baseline for clustering sea ice and lead signals.

## Gaussian Mixture Models (GMM)
Gaussian Mixture Models are probabilistic clustering methods that assume the data is generated from a mixture of Gaussian distributions.

### Unlike K-means, GMM:
- Provides soft (probabilistic) assignments.
- Allows clusters to have different shapes and covariance structures.
- Can better represent non-spherical data distributions.

### How GMM works
GMM uses the **Expectation–Maximization (EM)** algorithm:
- **E-step**: Estimate the probability that each point belongs to each Gaussian component.
- **M-step**: Update the Gaussian parameters (mean, covariance, mixing weights) to maximise data likelihood.

This process repeats until convergence.

GMM is particularly suitable when clusters differ in spread or orientation — which is often the case in physical remote sensing signals.

## Applications
### Image Classification (Sentinel-2)
Unsupervised clustering is applied to Sentinel-2 optical imagery to separate sea ice and leads.

The process involves:
- Reading RGB bands
- Stacking them into a feature matrix
- Removing invalid pixels
- Applying K-means and GMM clustering

This allows us to evaluate whether optical reflectance alone can distinguish between the two surface types.

### Altimetry Classification (Sentinel-3)
Clustering is also to Sentinel-3 altimetry data.

Before clustering, waveform data are transformed into physically meaningful variables, including:
- Peakiness
- Stack Standard Deviation (SSD)
- Backscatter coefficient (sig₀)

These features provide a compact description of waveform shape and amplitude characteristics.

---

## Getting Started
All experiments were conducted using **Google Colab**, which provides a cloud-based Jupyter notebook environment.

This setup ensures reproducibility without requiring local hardware configuration. Users can run the notebook directly in the browser after mounting Google Drive and adjusting file paths to match their data location.

## Installation

The following additional packages are required in Google Colab:
```markdown
!pip install rasterio  
!pip install netCDF4  
   ```

Other libraries (NumPy, SciPy, scikit-learn, Matplotlib) are pre-installed in Colab.

## Data Requirements
This project uses colocated Sentinel-2 and Sentinel-3 datasets obtained from the Copernicus Data Space.

Due to file size limitations, the data folders are **not included in this repository**.

The specific datasets used in this project are:
- Sentinel-2 Optical Data: S2A_MSIL1C_20190301T235611_N0207_R116_T01WCU_20190302T014622.SAFE
- Sentinel-3 Altimetry Data: S3A_SR_2_LAN_SI_20190307T005808_20190307T012503_20230527T225016_1614_042_131______LN3_R_NT_005.SEN3

These datasets were downloaded and colocated following the procedures described in:
- Data Fetching
- Colocating Sentinel-3 and Sentinel-2 Data

Users will need to download the corresponding Sentinel-2 and Sentinel-3 products and update the file paths in the notebook to match their local directory structure.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

---

## 📜Disclaimer

This repository contains coursework developed as part of the module GEOL0069(AI4EO) in the UCL Earth Sciences Department.

The content represents my personal academic work and understanding. It is not an official course resource. Although care has been taken to ensure correctness, the material may not reflect future updates to course content.


## 📬Contact
James Ge - zcfbyge@ucl.ac.uk

## 📚 References

1. CPOM UCL GEOL0069 AI4EO: Unit 2 — Unsupervised Learning Methods.* Available at: https://cpomucl.github.io/GEOL0069-AI4EO/Unit_2_Unsupervised_Learning_Methods_updated.html (Accessed: 18 February 2026).
2. MacQueen, J. (1967). Some methods for classification and analysis of multivariate observations. Proceedings of the Fifth Berkeley Symposium on Mathematical Statistics and Probability, 1, 281–297.
