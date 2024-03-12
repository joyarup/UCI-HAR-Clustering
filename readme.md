# Analysis of Sensor Data Using Clustering Techniques

## Abstract

This study explores the application of clustering techniques, specifically KMeans and DBSCAN, on a sensor dataset comprising multiple dimensions. The primary aim is to identify inherent groupings within the data that could unveil patterns or similarities among the observations. This report details the process from data preprocessing, including scaling and dimensionality reduction, to the application of clustering algorithms and the interpretation of their results.

## 1. Introduction

Clustering algorithms are essential tools in machine learning for uncovering natural groupings within datasets. This study focuses on a sensor dataset, presenting a complex, multidimensional challenge. KMeans and DBSCAN are selected for their distinct approaches to clustering: KMeans for its simplicity and efficacy in forming spherical clusters, and DBSCAN for its ability to handle noise and identify clusters of arbitrary shapes. The study aims to compare these methods' effectiveness in revealing insightful patterns within the sensor data.

## 2. Methodology

### 2.1 Data Acquisition and Preprocessing

The dataset consists of sensor readings with 561 features, spanning over 7352 observations. Preprocessing involved several steps to prepare the data for clustering:

- **Scaling**: The StandardScaler from scikit-learn was applied to normalize the feature scales, ensuring that no single feature would dominate the distance calculations used in clustering.
- **Feature Selection**: A VarianceThreshold was applied to remove features with low variance, which are unlikely to contribute to the clustering process. This step reduced the dimensionality from 561 to 524 features, enhancing computational efficiency and focusing analysis on the most informative features.
- **Dimensionality Reduction**: Principal Component Analysis (PCA) was utilized to further reduce dimensionality while preserving the variance in the dataset. The number of components was chosen based on the cumulative explained variance ratio, aiming for a concise representation that still captures the majority of the information in the dataset.

### 2.2 Clustering Algorithms

#### 2.2.1 KMeans

The elbow method was used to determine the optimal number of clusters, with inertia (within-cluster sum of squares) plotted against a range of cluster counts. The chosen number of clusters was where the rate of decrease in inertia began to plateau, indicating a suitable balance between cluster compactness and quantity.

#### 2.2.2 DBSCAN

The DBSCAN algorithm requires the selection of `eps` and `min_samples`. The nearest neighbor technique was employed to estimate a suitable `eps` value by analyzing the distance to the nearest points. The selection of `min_samples` was informed by the dataset's density and the desired minimum cluster size.

## 3. Results

### 3.1 Preprocessing Outcomes

- **Feature Selection and Scaling**: The dataset was successfully reduced to 524 features, with all features scaled to have zero mean and unit variance.
- **PCA Analysis**: PCA further reduced the dimensionality, focusing on retaining significant variance. The selection of components was based on a target cumulative explained variance, which led to the retention of 59 components capturing over 90% of the variance.

### 3.2 Clustering Analysis

- **KMeans Clustering**: Visualizations of KMeans clustering on PCA-reduced data highlighted the formation of distinct clusters, with the optimal number of clusters determined to be 2 based on the elbow method.
- **DBSCAN Clustering**: DBSCAN applied to both PCA and t-SNE reduced datasets revealed clusters, focusing on the method's ability to handle noise and identify more naturally formed groupings. The analysis yielded varying numbers of clusters depending on the parameters and dimensionality reduction technique used, illustrating DBSCAN's sensitivity to parameter settings.

### 3.3 Validation

The KMeans clustering algorithm demonstrated superior performance and was subsequently applied to the "y_train" dataset to assess its clustering efficacy. The clustering outcomes, as determined by the algorithm, were categorized according to their respective label indices, providing insight into the algorithm's accuracy in mirroring the inherent groupings of the "y_train" component.

## 4. Discussion

The study highlighted the strengths and limitations of KMeans and DBSCAN in clustering multidimensional sensor data. KMeans provided clear and distinct cluster assignments but required a predetermined number of clusters. DBSCAN, conversely, did not require specifying the number of clusters upfront and was adept at handling outliers but required careful tuning of its parameters. Dimensionality reduction played a crucial role in visualizing and interpreting the clusters.

## 5. Conclusion

This report presented a comprehensive analysis of sensor data using KMeans and DBSCAN clustering algorithms. Through meticulous preprocessing and the application of dimensionality reduction techniques, the study provided insights into the inherent groupings within the sensor dataset. The comparison between KMeans and DBSCAN revealed their respective advantages and challenges, contributing to our understanding of clustering methodologies' application in analyzing complex datasets.
