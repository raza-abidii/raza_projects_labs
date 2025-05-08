# Computational Labs and Projects with Python

Welcome to a growing collection of computational labs and projects built using Python. This repository includes hands-on notebooks across various domains such as Linear Algebra, Data Science, Machine Learning, and more.

Each lab is designed to be educational, beginner-friendly, and practical — with explanations, code examples, and visual outputs using libraries like **NumPy**, **Matplotlib**, and others.

## LAB1:- 
Basics of Linear Algebra
In this **Lab 1** of the Linear Algebra series using **NumPy** and **Matplotlib**. This lab explores essential operations for vectors and matrices — including dot products, transposes, inverses, eigenvalues, SVD, and image compression.

- Perform basic and advanced matrix operations using NumPy
- Understand and compute dot, inner, and outer products
- Apply matrix decomposition (SVD) for image compression
- Solve systems of linear equations programmatically

## Matrix Operations
- **Transpose**: `A.T`
- **Dot Product**: `np.dot(A, B)` or `A @ B`
- **Outer Product**: `np.outer(a, b)`

## Matrix Functions
- **Determinant**: `np.linalg.det(A)`
- **Inverse**: `np.linalg.inv(A)`
- **Matrix Power**: `np.linalg.matrix_power(A, n)`

## Eigen & Decomposition
- **Eigenvalues/Vectors**: `np.linalg.eig(A)`
- **SVD**: `U, S, V = np.linalg.svd(A)`

## Norms & Trace
- **Frobenius Norm**: `np.linalg.norm(A)`
- **Axis-wise Norm**: `np.linalg.norm(A, axis=1)`
- **Trace**: `np.trace(A)`

## Solving Linear Systems
- Solve `AX = B`: `np.linalg.solve(A, B)`

## Image Compression with SVD
```python
from skimage import data
import numpy as np
import matplotlib.pyplot as plt

# Load and normalize image
image = data.rocket() / 255.0
image = np.transpose(image, (2, 0, 1))

# SVD
U, S, V = np.linalg.svd(image)
Sigma = np.zeros((3, 427, 640))
for i in range(3):
    np.fill_diagonal(Sigma[i], S[i])

# Reconstruct with top-k components
k = 50
reconst = U @ Sigma[:, :, :k] @ V[:, :k, :]
reconst = np.transpose(reconst, (1, 2, 0))
plt.imshow(reconst)
plt.show()
