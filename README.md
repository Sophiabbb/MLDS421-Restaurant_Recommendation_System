
# Restaurant Recommendation System & Customer Segmentation

## Project Overview
This project tackles the challenge of helping users choose a restaurant based on users' order history. By implementing customer segmentation and advanced recommendation systems, we deliver more personalized restaurant recommendations and marketing strategies.

With the datasets from a food delivery app, we implemented two core systems:

1. **Customer Segmentation** using RFM and cuisine preference clustering to understand users' spending habits and identify user preferences for different types of cuisine.
2. **Restaurant Recommendation System** using collaborative filtering and hybrid models to suggest restaurants tailored to each user’s preferences and ordering behavior.

---

## Customer Segmentation Approach

### 1. Data Preprocessing
- Cleaned and merged four datasets (customer, order, vendor, and location) into a single dataset for analysis. The final dataset contains 135K order records and 33 features
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
Applied K-Means, K-Modes, and Hierarchical clustering on vendor tags to find cuisine preferences.

Clusters included:
- **K-Means**: Breakfast Lovers, Healthy & Beverage Lovers, Global Cuisine Lovers
- **K-Modes**: Global Taste Lovers, Breakfast & Dessert Lovers, Italian & Health Lovers, American Food Lovers, Comfort Food Lovers
- **Hierarchical Clustering**: Global Variety Lovers, Balanced Food Lovers, American Food Lovers

---

## Restaurant Recommendation System Approach

### 1. User-Item Matrix
- Built from order history
- Ratings derived from order frequency per user-vendor

### 2. Collaborative Filtering
- **Memory-Based CF**: User-Based, Item-Based
- **Model-Based CF**:
  - Matrix Factorization: SVD, NMF, SVD++
  - Deep Learning
  
- **Results**:

| Method         | RMSE    |
|----------------|---------|
| User-Based     | 2.8255  |
| Item-Based     | 2.8121  |
| SVD            | 2.6002  |
| NMF            | 2.6802  |
| SVD++          | 2.6054  |
| Deep Learning  | 3.0611  |

### 3. Hybrid Models
- **Weighted Hybrid**: SVD & SVD++, SVD++ & Item-Based, SVD++ & Deep Learning
- **Stacked Models**: Random Forest, Neural Networks
- **Results**:

| Method                | RMSE    |
|-----------------------|---------|
| SVD & SVD++           | 2.8255  |
| SVD++ & Item-Based    | 2.8121  |
| SVD++ & Deep Learning | 2.5822  |
| Random Forest         | 2.4803  |
| Neural Networks       | 2.4845  |

**Stacked model with random forest** performed the best among all the models.

---

## Files Description
```
├── AWS_Depployment_Presentation.pdf       # Presentation on AWS deployment architecture
├── Modeling_Presentation.pdf              # Presentation on modeling process/results
├── README.md                              # Project overview
├── backend/                               # Backend code and configurations
│   ├── pipeline.py                        # Main backend pipeline script
│   ├── requirements.txt                   # Python dependencies for backend
│   ├── config/                            # Backend configuration file
│   ├── dockerfiles/                       # Dockerfile for backend services
│   ├── log/                               # Log files directory
│   ├── src/                               # Core backend source code
│   └── tests/                             # Unit tests for backend
├── etl/                                   # ETL (Extract, Transform, Load) scripts
│   └── ETL_code.py                        # Script for data extraction, cleaning, and loading
├── frontend/                              # Frontend code and configurations
│   ├── Dockerfile                         # Dockerfile for frontend
│   ├── requirements.txt                   # Python dependencies for frontend
│   ├── webapp.py                          # Main web application script
│   └── config/                            # Frontend configuration file
└── notebooks/                             # Jupyter notebooks for data analysis and modeling
    ├── 1_Preprocessing_and_EDA.ipynb      # Data preprocessing and exploratory data analysis
    ├── 2_Customer_Segmentation.ipynb      # Customer segmentation analysis
    ├── 3_Recommendation_System.ipynb      # Recommendation system modeling
    └── environment.yml                    # Conda environment configuration
```

---

## Contributors
- Fuqian Zou
- Glenys Lion
- Iris Lee
- Liana Bergman-Turnbull
