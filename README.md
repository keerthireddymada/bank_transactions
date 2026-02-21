Bank User Clustering – First Unsupervised Learning Project
==========================================================

Problem Statement
-----------------

The goal of this project was to cluster bank users based on their transaction behavior.Instead of predicting a target variable, I used unsupervised learning to identify different types of users from raw transaction data.

Dataset
-------

I used a bank transaction dataset containing 2,512 transactions across 495 accounts.

Each transaction includes:

*   AccountID
    
*   TransactionAmount
    
*   TransactionDate
    
*   TransactionType (Debit / Credit)
    
*   AccountBalance
    
*   MerchantID
    
*   Location
    
*   PreviousTransactionDate
    

Since clustering should be done at the user level, I grouped transactions by AccountID to create user-level features.

My Approach
-----------

### 1\. Data Preparation

*   Converted date columns into datetime format
    
*   Calculated the number of days between transactions
    
*   Created a debit indicator feature
    

### 2\. Feature Engineering

I aggregated transaction-level data into user-level behavioral features:

*   Total spend
    
*   Average transaction amount
    
*   Transaction count
    
*   Debit ratio
    
*   Average account balance
    
*   Average days between transactions
    

This allowed each user to be represented as a structured feature vector.

### 3\. Feature Scaling

Since the features had different scales (for example, total spend vs debit ratio), I applied StandardScaler to normalize them before clustering.

### 4\. PCA for Visualization

I used Principal Component Analysis (PCA) to reduce the feature space to 2 dimensions.This helped visualize how the users were distributed across clusters.

### 5\. Clustering

I applied KMeans clustering with k = 4 to segment users into four groups.The number of clusters was chosen heuristically to keep the segmentation interpretable.

Results
-------

The model segmented users into four distinct groups based on their spending and transaction patterns.

### Cluster 0 – Low Activity Users

*   Lower overall spending
    
*   Fewer transactions
    
*   Moderate account balances
    
*   Mostly debit transactions
    

These users appear to use the account occasionally and maintain relatively stable balances.

### Cluster 1 – Heavy Active Spenders

*   Highest total spending
    
*   Highest transaction frequency
    
*   Mostly debit-based transactions
    
*   Slightly lower average balances compared to others
    

This group represents highly active users who frequently transact and spend more aggressively.

### Cluster 2 – Balanced Users

*   Moderate spending
    
*   Mixed debit and credit usage
    
*   Stable balances
    
*   Moderate transaction frequency
    

These users show more balanced financial behavior compared to other clusters.

### Cluster 3 – Stable Medium Spenders

*   Medium-level spending
    
*   Lower transaction frequency
    
*   Relatively higher balances
    

This group appears financially stable with controlled spending patterns.

The PCA visualization showed that while the clusters are not perfectly separated, there is visible grouping in the reduced 2D space. Some overlap exists between clusters, which is expected since financial behavior in real life does not form perfectly distinct categories.

Overall, the clustering produced meaningful behavioral segments even with relatively simple feature engineering.
