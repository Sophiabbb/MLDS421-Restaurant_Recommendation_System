
# 🍽️ Restaurant Recommendation System & Customer Segmentation

This project tackles the challenge of helping users choose a restaurant based on users' order history. By implementing customer segmentation and advanced recommendation systems, we deliver more personalized restaurant recommendations and marketing strategies.

## Overview

With a dataset of over 1 million rows from a food delivery app, we implemented two core systems:

1. **Customer Segmentation** using RFM and cuisine preference clustering
2. **Restaurant Recommendation System** using collaborative filtering and hybrid models

---

## Customer Segmentation

### Data Preprocessing
- Reduced from 1M+ rows to 129K clean records across 29 features
- Grouped 60+ vendor tags into 11 broad cuisine categories
- Removed age/gender due to missing data and bias concerns

### RFM Analysis (K-Means Clustering)
Clustered users based on Recency, Frequency, and Monetary value + Customer Lifetime Value (CLV)

| Segment      | Description          | Strategy                          |
|--------------|----------------------|-----------------------------------|
| Super Users  | High spend, frequent | Loyalty programs, upselling       |
| Regular Users| Moderate activity    | Personalized discounts            |
| Churn Users  | Low engagement       | Targeted re-engagement offers     |
| Lost Users   | Inactive             | Win-back campaigns                |

### Cuisine Preference Clustering
Applied K-Means, K-Modes, and Hierarchical clustering on vendor tags to find food preferences.

Clusters included:
- Asian, American/Italian, Arabic, Breakfast lovers
- Balanced or diverse eaters

---

## Recommendation System

### User-Item Matrix
- Built from order history (no ratings)
- Ratings derived from order frequency per user-vendor

### Collaborative Filtering

| Method         | RMSE    |
|----------------|---------|
| User-Based     | 2.8255  |
| Item-Based     | 2.8121  |
| SVD            | 2.5822  |
| NMF            | 2.6901  |
| SVD++          | 2.6056  |
| Deep Learning  | 3.0697  |

### Hybrid Models
- **Weighted Hybrid** (best RMSE: 2.5763)
- **Stacked Models** using Random Forest & Neural Networks (best RMSE: 2.4803)

---

## Contributors
- Fuqian Zou
- Glenys Lion
- Iris Lee
- Liana Bergman-Turnbull
