# Drug-Classification

## Project Overview

- **The Dataset:** https://www.kaggle.com/datasets/prathamtripathi/drug-classification/data
- This project applies machine learning techniques to classify drugs based on various patient metrics. It utilizes Support Vector Machine (SVM) algorithms, along with comparative analyses using Nearest Neighbor (KNN) and Nearest Class Centroid (NCC) classifiers. The project aims to evaluate the effectiveness of these models in predicting drug types based on patient characteristics.

### Features

- Implementation of SVM with linear kernel.
- Cross-validation strategy to evaluate SVM performance.
- PCA (Principal Component Analysis) for dimensionality reduction.
- Comparative analysis with KNN and NCC classifiers.

# Methodology

### Preprocessing Steps

1. **Encoding Categorical Values**:
   - **Binary Encoding**: Applied to the 'Sex' and 'Cholesterol' columns.
   - **One-Hot Encoding**: Used for the 'BP' (Blood Pressure) column.

2. **Feature Scaling**:
   - **StandardScaler**: Standardizes features by removing the mean and scaling to unit variance.

### Parameter Selection and Model Tuning Methods

1. **Support Vector Machine (SVM)**:
   - **Kernel**: Linear
   - **Random State**: 0

2. **K-Nearest Neighbors (KNN)**:
   - **Number of Neighbors (n_neighbors)**: 5
   - **Distance Metric**: Minkowski with \( p = 2 \) (Euclidean distance)

3. **Nearest Class Centroid (NCC)**:
   - **Metric**: Euclidean distance

### Cross-Validation Strategy

- **K-Fold Cross-Validation**: Different values of `n_splits` (2, 10, 15, 25) are experimented with.
- **Shuffle**: Ensuring data is shuffled before splitting into batches.

### Additional Points

- **Principal Component Analysis (PCA)**: Used to reduce dimensionality.
- **Model Comparison**: Comparing SVM with KNN and NCC models.


# Algorithm Explanation

### Support Vector Machine (SVM)

- **Fundamentals**: SVM is a supervised learning algorithm used for classification and regression. It works by finding the hyperplane that best separates the classes in the feature space.
- **Maximizing Margin**: The algorithm focuses on maximizing the margin between the data points of different classes, aiming to increase the model's generalization ability.
- **Support Vectors**: Data points closest to the hyperplane, called support vectors, are critical in defining the hyperplane and the margin.

### Nearest Neighbor (KNN)

- **Basic Concept**: Classifies a data point based on how its neighbors are classified. 
- **Distance Metrics**: Often uses Euclidean distance but can use other metrics.
- **Choosing 'K'**: The number of neighbors (K) is a crucial parameter, with a larger K smoothing the decision boundaries.

### Nearest Class Centroid (NCC)

- **Principle**: Assigns a class based on the closest class centroid.
- **Centroid Calculation**: The centroid of a class is the average of all points in that class.
- **Suitability**: Effective when classes are compact and well-separated.


# Results

- **Simple Support Vector Machine (SVM)**: accuracy is `0.9375`
- **Simple Support Vector Machine (SVM) with cross validation:** accuracy varies from `0.9901098` to `0.985` based on the number of splits
- **Simple Support Vector Machine (SVM) with PCA Applayied:** accuracy varies based on the number of PCA  components with the highest `0.5`
- **Comparative analysis with Nearest Neighbor and Nearest Class Centroid classifiers:** For NC accuracy is `0.7625` and for KNN `0.7`
 
Since I didn't initialize a random state, results might slightly vary from time to time.

# Discussion

The results indicate a strong performance of the Simple Support Vector Machine (SVM) model, achieving an accuracy of `0.9375`. This high accuracy underscores SVM's effectiveness in handling the dataset's linear separability. Notably, the application of cross-validation to SVM further enhanced its robustness, with accuracy reaching as high as `0.9901098`, depending on the number of splits. This variability in accuracy with different splits highlights the importance of cross-validation in evaluating model performance more comprehensively. However, the introduction of PCA (Principal Component Analysis) to SVM led to a significant decrease in accuracy, with the highest being only `0.5`. This suggests that dimensionality reduction via PCA might be removing critical information necessary for accurate classification in this specific dataset. In comparison, Nearest Neighbor (KNN) and Nearest Class Centroid (NCC) classifiers demonstrated lower accuracy, with NCC achieving 0.7625 and KNN 0.7. This disparity in performance could be attributed to SVM's superior ability to manage the feature space and its boundaries, as opposed to the distance-based classification approach used by KNN and the centroid-based approach of NCC. 
