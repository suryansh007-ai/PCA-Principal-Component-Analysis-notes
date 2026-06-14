# Principal Component Analysis (PCA) - Learning Notes & Implementations

## Overview

This repository contains my hands-on implementation and notes on **Principal Component Analysis (PCA)** using various datasets from Scikit-Learn.

The goal of this project is to understand:

* Why dimensionality reduction is needed
* The mathematics and intuition behind PCA
* Data preprocessing and standardization
* Explained Variance Ratio (EVR)
* Choosing the optimal number of principal components
* Visualization of high-dimensional datasets in 2D space

This repository is being updated continuously as I explore PCA on different datasets of increasing complexity.

---

## Workflow Followed

For every dataset, the following pipeline is used:

1. Load dataset
2. Convert to Pandas DataFrame
3. Perform Exploratory Data Analysis (EDA)

   * Shape
   * Data types
   * Descriptive statistics
   * Null value check
   * Duplicate value check
   * Correlation analysis
4. Standardize features using `StandardScaler`
5. Apply PCA
6. Analyze Explained Variance Ratio
7. Visualize transformed components
8. Determine the minimum number of components required to preserve ~90% variance

---

## Datasets Completed

### 1. Wine Dataset

**Dataset Information**

* Samples: 178
* Features: 13
* Classes: 3

### Steps Performed

* EDA and statistical analysis
* Correlation heatmap visualization
* Standardization using `StandardScaler`
* PCA with 2 principal components
* Scatter plot visualization of transformed data
* Explained Variance Ratio analysis

### Results

| Principal Component | Explained Variance |
| ------------------- | ------------------ |
| PC1                 | 36.20%             |
| PC2                 | 19.21%             |

Total variance retained using 2 components:

55.41%

### Finding Components for 90% Variance

Two approaches were explored:

#### Method 1: Iterative Search

Loop through different values of `n_components` and compute cumulative EVR.

Result:

* 8 components retain approximately 92.02% variance

#### Method 2: Direct PCA Optimization

```python
PCA(n_components=0.9)
```

Scikit-Learn automatically selects the minimum number of components required to retain at least 90% variance.

This resulted in:

* 8 principal components
* 92.02% cumulative explained variance

### Key Observation

A useful Scikit-Learn feature is that:

```python
PCA(n_components=0.9)
```

automatically chooses the minimum number of components needed to preserve 90% of the information, eliminating the need for manual loops.

---

### 2. Breast Cancer Dataset

**Dataset Information**

* Samples: 569
* Features: 30
* Classes: 2

### Steps Performed

* Data inspection
* Statistical analysis
* Null value verification
* Duplicate value verification
* Correlation heatmap generation
* Feature standardization
* PCA transformation
* Explained variance analysis
* 2D visualization using the first two principal components

### Results

Variance retained by the first components:

| Component | Explained Variance |
| --------- | ------------------ |
| PC1       | 44.27%             |
| PC2       | 18.97%             |
| PC3       | 9.39%              |
| PC4       | 6.60%              |
| PC5       | 5.50%              |
| PC6       | 4.02%              |
| PC7       | 2.25%              |

### 90% Variance Retention

Using:

```python
PCA(n_components=0.9)
```

The dataset required:

* 7 principal components
* 91.01% cumulative explained variance

### Key Observation

The Breast Cancer dataset contains a large number of highly correlated features, making PCA particularly effective at reducing dimensionality while preserving most of the information.

---

## Datasets Currently In Progress

* Digits Dataset
* Additional Intermediate-Level PCA Datasets

These implementations will include:

* Explained variance analysis
* Scree plots
* Component interpretation
* Visualization of dimensionality reduction effects
* Comparison of PCA performance across datasets

---

## Libraries Used

```python
pandas
numpy
matplotlib
seaborn
scikit-learn
```
## Learning Outcome

Through these implementations, I gained practical experience with:

* Feature scaling
* Correlation analysis
* Dimensionality reduction
* Explained Variance Ratio interpretation
* Selecting optimal principal components
* Data visualization in reduced dimensions

This repository serves as my personal PCA learning journal and will continue to grow as I explore more datasets and dimensionality reduction techniques.
