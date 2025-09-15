# Mini Project 2: Breast Cancer Dataset Analysis

**Author:** Matthew Martin

## Overview

This project explores the breast cancer gene expression dataset **GSE45827** from the CuMiDa database, which contains **151 tissue samples** and **54,676 gene expression features** across **five breast cancer subtypes** and normal tissue.  

The analysis focuses on **dimensionality reduction** using Principal Component Analysis (PCA) and **unsupervised clustering** to identify patterns and relationships among gene expression profiles.

## Objectives

- Understand gene expression patterns that differentiate breast cancer subtypes.  
- Apply PCA to reduce high-dimensional data while preserving variance.  
- Explore sample clustering using K-means and hierarchical methods.  
- Investigate which genes contribute most to principal components.  
- Validate clustering results against known subtype labels.

## Dataset

- **Source:** CuMiDa (GSE45827)  
- **Samples:** 151  
- **Features:** 54,676 gene expression values  
- **Classes:** basal, HER, luminal_A, luminal_B, cell_line, normal  

### Sample Distribution

| Subtype       | Count |
|---------------|-------|
| basal         | 41    |
| HER           | 30    |
| luminal_B     | 30    |
| luminal_A     | 29    |
| cell_line     | 14    |
| normal        | 7     |

## Data Preprocessing

- Checked for **missing values**: none present.  
- Dropped **metadata columns** (`samples` and `type`) for unsupervised analysis.  
- **StandardScaler** applied to normalize gene expression values.  

## Exploratory Data Analysis (EDA)

- Boxplots and histograms were generated for **top-variance genes** to identify patterns and skew.  
- Correlation matrix revealed highly correlated genes, suggesting potential co-expression or shared regulation.  
- Top genes showing variance across subtypes: `206378_at`, `228241_at`, `205916_at`.

## PCA Analysis

- Applied PCA to reduce dimensionality from 54,676 features to **151 components**.  
- **90% variance explained** by **106 components**.  
- PCA highlights dominant patterns and prepares data for clustering.

## Clustering Analysis

### K-means

- Used first **20 PCA components** to mitigate curse of dimensionality.  
- **k = 6** (number of known labels)  
- Silhouette Score: **0.1941**  
- Adjusted Rand Index (ARI): **0.3914**  
- Normalized Mutual Information (NMI): **0.6005**  

### Hierarchical Clustering

- Ward’s linkage on first **20 PCA components**.  
- **k = 6**  
- Silhouette Score: **0.1913**  
- ARI: **0.4263**  
- NMI: **0.6332**  

### Hyperparameter Tuning

- Explored **k = 2 to 25** for hierarchical clustering.  
- **Best silhouette score:** 0.329 at **k = 2**, indicating strong separation between cancerous vs. noncancerous samples.  

## Results & Insights

- PCA effectively reduced dimensionality while preserving variance.  
- Clustering performance moderate; low silhouette scores indicate overlapping subtypes.  
- Hierarchical clustering aligns better with true labels (higher ARI/NMI) than K-means.  
- Top-variance genes identified may inform biomarker discovery.

## Discussion

- Clustering based solely on gene expression may not fully capture subtype complexity.  
- Peak performance at k=2 likely reflects separation of cancerous vs. normal tissue, not distinct subtypes.  
- K-means produces tighter clusters, but hierarchical clustering better matches known subtypes.

## Future Work

- Explore **t-SNE** or **UMAP** for non-linear dimensionality reduction.  
- Consider **ensemble clustering** or supervised classification for better subtype identification.  
- Integrate clinical or pathway data to improve clustering and subtype discovery.

