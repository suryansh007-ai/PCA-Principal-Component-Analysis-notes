# Customer Feedback Clustering using NLP & Unsupervised Machine Learning

## Overview

Companies receive thousands of customer feedback messages, reviews, and complaint tickets every day. Reading and categorizing each one manually is time-consuming and inefficient.

This project automatically groups similar customer feedback into meaningful clusters using **Natural Language Processing (NLP)** and **K-Means Clustering**. The goal is to help businesses identify common issues, understand customer concerns, and improve support efficiency without manually labeling every complaint.

---

## Problem Statement

Given a collection of customer feedback or complaint tickets, automatically identify and group similar complaints together without any predefined labels.

Example clusters:

- Billing Issues
- Shipping Delays
- Login Problems
- Refund Requests
- Technical Issues

---

## Features

- Text preprocessing using NLP
- TF-IDF Vectorization
- K-Means Clustering
- Hyperparameter tuning for optimal number of clusters
- PCA-based cluster visualization
- Top keywords extraction for every cluster
- Interactive dashboard for analysis

## Project Workflow

```
Customer Feedback
        │
        ▼
Data Cleaning
(Remove Null Values & Duplicates)
        │
        ▼
NLP Preprocessing
• Lowercase Conversion
• Remove Punctuation
• Tokenization
• Stopword Removal
• Lemmatization
        │
        ▼
TF-IDF Vectorization
(Text → Numerical Features)
        │
        ▼
K-Means Clustering
        │
        ▼
Hyperparameter Tuning
(Elbow Method & Silhouette Score)
        │
        ▼
PCA Visualization
        │
        ▼
Cluster Analysis Dashboard
```

---

## Machine Learning Concepts Covered

- Natural Language Processing (NLP)
- Text Preprocessing
- TF-IDF Vectorization
- Unsupervised Learning
- K-Means Clustering
- Hyperparameter Tuning
- Principal Component Analysis (PCA)
- Cluster Evaluation
- Data Visualization

## Future Improvements

- Sentence Transformers (BERT/SBERT) instead of TF-IDF
- HDBSCAN for density-based clustering
- Automatic cluster naming using LLMs
- Sentiment Analysis
- Complaint Priority Prediction
- Automatic Complaint Routing
- AI-generated summaries for each cluster
