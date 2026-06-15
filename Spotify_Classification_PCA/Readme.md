# Spotify Genre Analysis using PCA, Logistic Regression, and K-Means Clustering

## Overview

In this notebook, I explored a Spotify dataset containing **114,000 songs across 114 genres**. The objective was to understand how **Principal Component Analysis (PCA)** affects high-dimensional data, how it impacts classification performance, and whether songs can be naturally grouped using clustering.

---

## What I Did

### 1. Exploratory Data Analysis (EDA)

* Checked dataset shape and data types.
* Found only **1 missing value** each in:

  * artists
  * album_name
  * track_name
* Found **0 duplicate rows**.
* Visualized the most common genres.
* Generated a correlation heatmap.

### Interesting Correlations

Some relationships I noticed:

* **Energy ↔ Loudness** (strong positive correlation)
* **Danceability ↔ Valence**
* **Speechiness ↔ Explicit**
* **Danceability ↔ Loudness**

These correlations suggested that some features may contain overlapping information, making PCA worth trying.

---

### 2. Feature Selection

Dropped:

```python
track_name
artists
album_name
```

because they were not useful for numerical analysis.

Before PCA, I also removed:

```python
track_id
track_genre
```

since one is an identifier and the other is the target label.

---

## Principal Component Analysis (PCA)

### Standardization First

A key thing I learned:

> PCA should be performed after feature scaling.

So I used:

```python
StandardScaler()
```

before applying PCA.

---

### Retaining 90% Variance

Instead of manually checking different component values, I used:

```python
PCA(n_components=0.9)
```

I found this to be a very useful shortcut because PCA automatically selects the minimum number of components needed to preserve at least 90% of the variance.

### Observation

Even after PCA:

```text
15 numerical features → 12 principal components
```

My reaction in the notebook:

> "21 to 12 for 0.9 EVR hmmm...."

This showed that the audio features contain a lot of unique information and are not highly redundant.

---

### PCA Visualization

I reduced the dataset to:

```python
PCA(n_components=3)
```

for 3D visualization.

Results:

```text
PC1 = 18.75%
PC2 = 9.75%
PC3 = 8.65%
```

Total variance explained:

```text
37.15%
```

This helped me understand that visualizing data in only 2 or 3 dimensions often loses a large amount of information.

---

## Logistic Regression

I trained a Logistic Regression model to predict song genres.

### Without PCA

```text
Accuracy: 49.07%
Training Time: ~78.7 seconds
```

### With PCA (90% Variance)

```text
Accuracy: 47.31%
Training Time: ~73.9 seconds
```

### What I Learned

PCA reduced training time slightly, but accuracy dropped.

Important lesson:

> PCA preserves variance, not necessarily the information that helps separate classes.

Reducing dimensions can make models faster, but it does not always improve performance.

---

## K-Means Clustering

After classification, I wanted to ignore genre labels and see whether songs naturally form groups based on audio characteristics.

### Elbow Method

I used the elbow method and found:

```text
K = 2
```

to be the optimal number of clusters.

---

### Cluster Interpretation

#### Cluster 0

Contained genres such as:

* EDM
* House
* Hardstyle
* Trance
* Reggaeton

Characteristics:

* Higher energy
* Higher loudness
* More danceable

#### Cluster 1

Contained genres such as:

* Classical
* Ambient
* Sleep
* Opera
* New Age

Characteristics:

* Higher acousticness
* Lower energy
* More instrumental

### Most Interesting Finding

Even without using genre labels, K-Means grouped songs in a meaningful way.

My takeaway:

> We were kind of able to classify genres based on energy, loudness and other audio features using K-Means clustering.

---

## Key Things I Learned

* PCA should be applied after standardization.
* `PCA(n_components=0.9)` is an easy way to retain 90% variance.
* High-dimensional data often cannot be represented well using only 2-3 components.
* PCA can reduce training time but may reduce classification accuracy.
* Logistic Regression achieved nearly 49% accuracy on a difficult 114-class genre problem.
* K-Means can discover natural groupings in music without being given genre labels.
* Features such as energy, loudness, acousticness, and danceability capture meaningful musical patterns.

---

## Libraries Used

```python
pandas
numpy
matplotlib
seaborn
plotly
scikit-learn
```

This notebook was primarily a learning exercise to understand PCA, dimensionality reduction, visualization, classification, and clustering on a real-world high-dimensional dataset.
