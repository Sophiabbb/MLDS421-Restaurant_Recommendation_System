
# 🍽️ Restaurant Recommendation System & Customer Segmentation

## Project Overview
This project tackles the challenge of helping users choose a restaurant based on users' order history. By implementing customer segmentation and advanced recommendation systems, we deliver more personalized restaurant recommendations and marketing strategies.

With a dataset of over 1 million rows from a food delivery app, we implemented two core systems:

1. **Customer Segmentation** using RFM and cuisine preference clustering
2. **Restaurant Recommendation System** using collaborative filtering and hybrid models

---

## Customer Segmentation Approach

### 1. Data Preprocessing
- Reduced from 1M+ rows to 129K clean records across 29 features
- Grouped 60+ vendor tags into 11 broad cuisine categories
- Removed age/gender due to missing data and bias concerns

### 2. RFM Clustering
Applied K-Means clustering to cluster users based on Recency, Frequency, and Monetary value + Customer Lifetime Value (CLV)

| Cluster | Segment        | Description          | Strategy                         | Avg. Recency | Avg. Frequency | Avg. Monetary | Avg. CLV | Proportion of Users |
|---------|----------------|----------------------|----------------------------------|----------------------|--------------------------|----------------|--------------------|--------------------------|
| 1       | Super Users    | High spend, frequent | Loyalty programs, upselling      | 17                   | 30                       | $493.57        | $70.76             | 6%                       |
| 2       | Regular Users  | Moderate activity    | Personalized discounts           | 37                   | 7                        | $114.70        | $31.21             | 34%                      |
| 3       | Churn Users    | Low engagement       | Targeted re-engagement offers    | 45                   | 2                        | $17.85         | $19.55             | 38%                      |
| 4       | Lost Users     | Inactive             | Win-back campaigns               | 189                  | 2                        | $26.71         | $12.56             | 22%                      |

### 3. Cuisine Preference Clustering
Applied K-Means, K-Modes, and Hierarchical clustering on vendor tags to find food preferences.

Clusters included:
- Asian, American/Italian, Arabic, Breakfast lovers
- Balanced or diverse eaters

---

## Restaurant Recommendation System Approach

### 1. User-Item Matrix
- Built from order history (no ratings)
- Ratings derived from order frequency per user-vendor

### 2. Collaborative Filtering

| Method         | RMSE    |
|----------------|---------|
| User-Based     | 2.8255  |
| Item-Based     | 2.8121  |
| SVD            | 2.5822  |
| NMF            | 2.6901  |
| SVD++          | 2.6056  |
| Deep Learning  | 3.0697  |

### 3. Hybrid Models
- **Weighted Hybrid** (best RMSE: 2.5763)
- **Stacked Models** using Random Forest & Neural Networks (best RMSE: 2.4803)

---

## Contributors
- Fuqian Zou
- Glenys Lion
- Iris Lee
- Liana Bergman-Turnbull
