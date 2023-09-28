# SVM - Support Vector Machine
## Lagrange Multipliers
The minimum of a function $f(x, y)$ subject to the constraint $g(x,y) = 0$ happens when $L(x,y, \lambda) = f(x, y) - \lambda g(x,y)$ is maximized.
	→ $\nabla L = 0$

SVM maximizes the margin by minimizing $\frac{1}{2}|w|^{2}$ such that $y_{i}(w\cdot x_{i}+b) \ge 1$

Maximizing the margin depends only on the dot product of pairs of support vectors.


## What do inner products mean?
- Inner product provide a measure of similarity
- If two vectors are perpendicular (i.e. completely dissimilar), their inner product is 0.
- If two vectors are parallel, their inner product is 1.

- Case 1: If two features are completely dissimilar, they don't contribute to L.
- Case 2: If two features are similar and predict the same class, they decrease L.
- Case 3: If two features are similar and predict different classes, they increase L.

## Kernel Trick
- The kernel defines inner products in the transformed space
- In other words, the kernel defines similarity between datapoints in the transformed space
- The "trick" is that we work in the lower dimensional space, instead of explicitly applying the transformations to the higher-dimensional space
- Most commonly used kernels
	- linear: $K(x_{i},x_{j})=x_{i}\cdot x_{j}$
		→ linear SVM
	- polynomial: $K(x_{i},x_{j})=(\gamma x_{i}, x_{j}+r)^{d}$
	- gaussian radial basis function (RBF): $K(x_{i}, x_{j})=\text{exp} (-\gamma |x_{i}-x_{j}|^{2})$
		→ default in sklearn

# SVM Summary
- Idea
	- Construct a hyperplane that can separate two classes
	- The optimal hyperplane is the one that maximizes the margin between support vectors
- Strengths
	- Works the best with clear separation
	- Effective with nonlinear, high-dimensional data
	- Tends to avoid overfit
	- No need to store training dataset after model is built
- Weaknesses
	- Slow for larger dataset (training time ∝ $n^{2}$)
	- SMV does not directly provide probability estimates


