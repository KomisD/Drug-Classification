# Drug-Classification

## Project Overview

- **The Dataset:** [Drug Classification Dataset on Kaggle](https://www.kaggle.com/datasets/prathamtripathi/drug-classification/data)
- This repository contains two projects applying machine learning techniques for drug classification based on various patient metrics. 

## Projects

- **Project2_NNs.ipynb**: Utilizes Support Vector Machine (SVM) algorithms, along with comparative analyses using Nearest Neighbor (KNN) and Nearest Class Centroid (NCC) classifiers.
- **Project3_NNs.ipynb**: Focuses on Radial Basis Function Neural Network (RBFN) implementation **from scratch**, along with comparative analyses using KNN and NCC classifiers.

### Features Across Projects

- **SVM and RBFN Implementations**: Linear kernel SVM and RBFN for drug classification.
- **PCA (Principal Component Analysis)**: For dimensionality reduction in SVM.
- **Cross-validation**: Strategy to evaluate model performances.
- **Comparative Analysis**: With KNN and NCC classifiers in both projects.

# Methodology

## Preprocessing Steps (Common for Both Projects)

1. **Encoding Categorical Values**:
   - **Binary Encoding**: Applied to the 'Sex' and 'Cholesterol' columns.
   - **One-Hot Encoding**: Used for the 'BP' (Blood Pressure) column.

2. **Feature Scaling**:
   - **StandardScaler**: Standardizes features by removing the mean and scaling to unit variance.

## Parameter Selection and Model Tuning Methods

### Project2_NNs.ipynb (SVM, KNN, NCC)

1. **Support Vector Machine (SVM)**:
   - **Kernel**: Linear
   - **Random State**: 0

2. **K-Nearest Neighbors (KNN)** and **Nearest Class Centroid (NCC)**:
   - Similar parameters as detailed below.

### Project3_NNs.ipynb (RBFN, KNN, NCC)

1. **Radial Basis Function (RBFN)**:
   - Neuron Count: Varied (e.g., 20, 30, 50).
   - Gamma Value: Calculated from data variance or constant values.
   - Prototype Initialization: Random or using KMeans clustering.

2. **K-Nearest Neighbors (KNN)** and **Nearest Class Centroid (NCC)**:
   - **Number of Neighbors (n_neighbors)**: 5 (KNN)
   - **Distance Metric**: Minkowski with \( p = 2 \) (Euclidean distance)
   - **Metric for NCC**: Euclidean distance

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

### Radial Basis Function (RBFN):
   - **Neuron Count**: Experimented with different numbers of neurons in the hidden layer (e.g., 20, 30, 50). This parameter affects the capacity of the model to capture complex patterns.
   - **Gamma Value**: Calculated based on data variance to determine the spread of the RBF or some constant values ranging from 0.5 to 2.
   - **Prototype Initialization**: In some models, prototypes were initialized using KMeans clustering, which provides a more informed starting point for these centers and in others randomly select prototypes from the training data.

# Results

## Project2_NNs.ipynb (SVM, KNN, NCC)
- **Simple Support Vector Machine (SVM)**: accuracy is `0.9375`
- **Simple Support Vector Machine (SVM) with cross validation:** accuracy varies from `0.9901098` to `0.985` based on the number of splits
- **Simple Support Vector Machine (SVM) with PCA Applayied:** accuracy varies based on the number of PCA  components with the highest `0.5`
- **Comparative analysis with Nearest Neighbor and Nearest Class Centroid classifiers:** For NC accuracy is `0.7625` and for KNN `0.7`
 
Since I didn't initialize a random state, results might slightly vary from time to time.

## Project3_NNs.ipynb (RBFN, KNN, NCC)

- **RBFN Performance**: Best at 88.75% accuracy for 50 neurons.
- **Prototype Initialization**: No improvement using KMeans.
- **Comparative analysis**: NC accuracy is `0.7625` and KNN `0.7`.

# Discussion

## Project2_NNs.ipynb (SVM, KNN, NCC)

The results indicate a strong performance of the Simple Support Vector Machine (SVM) model, achieving an accuracy of `0.9375`. This high accuracy underscores SVM's effectiveness in handling the dataset's linear separability. Notably, the application of cross-validation to SVM further enhanced its robustness, with accuracy reaching as high as `0.9901098`, depending on the number of splits. This variability in accuracy with different splits highlights the importance of cross-validation in evaluating model performance more comprehensively. However, the introduction of PCA (Principal Component Analysis) to SVM led to a significant decrease in accuracy, with the highest being only `0.5`. This suggests that dimensionality reduction via PCA might be removing critical information necessary for accurate classification in this specific dataset. In comparison, Nearest Neighbor (KNN) and Nearest Class Centroid (NCC) classifiers demonstrated lower accuracy, with NCC achieving 0.7625 and KNN 0.7. This disparity in performance could be attributed to SVM's superior ability to manage the feature space and its boundaries, as opposed to the distance-based classification approach used by KNN and the centroid-based approach of NCC. 

## Project3_NNs.ipynb (RBFN, KNN, NCC)
- **RBFN Insights**: Best performance with 50 neurons, indicating capacity for complex pattern recognition.
- **Prototype Initialization**: Lack of improvement with KMeans initialization.
- **Model Comparisons**: Superior performance of RBFN over KNN and NCC in specific configurations.

# Final Best Model

- **Simple Support Vector Machine (SVM) with cross validation** with a stagering accuracy of `0.9901098`
