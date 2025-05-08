### This repo is for the submintion of Projects and Labs
### LAB1:- 
Basics of Linear Algebra


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
