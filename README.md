# Spectral Clustering for Unsupervised Learning

## Project Overview
This project implements the **Spectral Clustering** algorithm to cluster a synthetic dataset of 300 two-dimensional points. The dataset consists of five clusters, each generated from bivariate Gaussian distributions. By leveraging graph theory and eigenvalue decomposition, this approach provides an effective method for clustering data points based on their connectivity.

---

## Dataset
The dataset contains 300 data points, generated from the following Gaussian distributions:
- **Cluster 1**: Mean [2.5, 2.5], Covariance [[0.8, -0.6], [-0.6, 0.8]], Size: 50
- **Cluster 2**: Mean [-2.5, 2.5], Covariance [[0.8, 0.6], [0.6, 0.8]], Size: 50
- **Cluster 3**: Mean [-2.5, -2.5], Covariance [[0.8, -0.6], [-0.6, 0.8]], Size: 50
- **Cluster 4**: Mean [2.5, -2.5], Covariance [[0.8, 0.6], [0.6, 0.8]], Size: 50
- **Cluster 5**: Mean [0.0, 0.0], Covariance [[1.6, 0.0], [0.0, 1.6]], Size: 100

The dataset is provided in `data_set.csv` as a two-column CSV file containing the X and Y coordinates of the points.

---

## Methodology

### 1. Graph Construction
- **Connectivity Matrix**: Constructed based on pairwise Euclidean distances. Points are considered connected if the distance is ≤ 1.25.
- **Visualization**: Edges were drawn between connected points to illustrate the graph structure.

### 2. Spectral Clustering Steps
- **Degree Matrix (D)**: Diagonal matrix where each entry represents the degree of a node (number of connections).
- **Laplacian Matrix (L)**: Computed as \( L = D - W \), where \( W \) is the adjacency matrix.
- **Normalized Laplacian**: \( L_{sym} = I - D^{-1/2} W D^{-1/2} \).
- **Eigenvectors**: The five smallest non-zero eigenvectors of \( L_{sym} \) were selected to form a feature matrix \( Z \).

### 3. Clustering
- **K-Means**: Applied on the \( Z \) matrix to cluster the data into five groups.
- **Initialization**: Centroids were initialized using specific rows of the \( Z \) matrix.

### 4. Visualization
- The final clusters were plotted in different colors, showing the results of the spectral clustering algorithm.

![output_6_0](https://github.com/user-attachments/assets/45c5757a-958e-4ff5-a096-9d1cbaac8a70)

---

## Results
- **Graph Connectivity**: The graph effectively captured the connectivity between nearby points.
- **Cluster Separation**: Spectral clustering successfully identified the five underlying clusters, aligning with the dataset's true structure.
- **Iterations**: The K-Means algorithm converged after 15 iterations.

### Sample Visualizations
1. **Graph Connectivity**

![output_10_0](https://github.com/user-attachments/assets/8593c1bb-43fc-4fa0-b008-99456e371b85)


2. **Clustering Results**
   
![output_22_1](https://github.com/user-attachments/assets/ebc043c3-8fe0-453c-b1ee-a0dc2bae88dd)

---

## How to Run

### Prerequisites
- Python 3.x
- Required Libraries: `numpy`, `matplotlib`, `scipy`, `sklearn`

### Steps
1. Clone the repository and ensure `data_set.csv` is in the project directory.
2. Open and run `Notebook.ipynb` in Jupyter Notebook, or convert it into a `.py` script to execute.

---

## Key Learnings
- **Spectral Clustering**: Demonstrates the power of eigenvalue decomposition in unsupervised learning.
- **Graph-Based Methods**: Provides an intuitive way to model relationships between data points.
- **Eigenvectors and K-Means**: Combines spectral embedding with conventional clustering for improved results.

---

## Future Work
- Experiment with different thresholds for connectivity (𝛿).
- Apply spectral clustering to larger and higher-dimensional datasets.
- Compare with other clustering methods like DBSCAN and Gaussian Mixture Models.

---

## Acknowledgments
- Dataset and inspiration derived from graph-based clustering techniques in machine learning.
- Implementation follows foundational concepts in spectral graph theory.
