## What is ML?
- Find a function $y \approx \hat{y}=f(x)$ from data
### Overview
##### Supervised
- Data in the form $(x_{1},y_{1}),(x_{2},y_{2})...$
##### Unsupervised
- Data in the form $x_{1},...,x_{n}$

- $\text{dom y} \in \mathbb{R}$: regression (supervised), embedding ((dimensionality reduction)) (unsupervised)
- $\text{dom y} \in [k]$: classification (supervised), clustering (unsupervised)

*The process of using data to learn $f$ is called <font color="HotPink" style="font-style: italic;">learning</font> or <font color="HotPink" style="font-style: italic;">training</font>
- <font color="HotPink" style="font-style: italic;">machine learning</font> if the process is automated by computer programs

*The learned relationship $y \approx f(x)$ is **inductive, not deductive***
- data-driven
- not based on physics or any other type of science

### Applications
##### Supervised
- Spam filtering
- Handwriting recognition
- Face detection
- Stock market prediction
- Speech recognition
##### Unsupervised
- Document topic discovery
- Word embeddings
- Source separation / image segmentation
- Recommendation systems (clustering numbers and/or products)

### Supervised Learning
*Criterion to find $f(*)$:
$$\text{minimize}_{f}\text{ }E[l(y,f(x))]$$
- Among all possible $(x,y)$ pairs, treat as random variables
- $l(*,*)$ is some loss/risk function to measure error
- Pretend we know the distributions of $(x,y)$ generative models
- or, replace expectation $E[*]$ with sample average

*Generative models*:
- regression: Wiener filter
- classification: Gaussian discriminant analysis
- naive Bayes
- latent variable modeling for unsupervised learning:
	- Gaussian mixture model
	- Probabilistic PCA

### Empirical Risk Minimization
*Replace expectation $E[*]$ with sample average*
$$\text{minimize}_{f} \text{} \frac{1}{n}\sum\limits^{n}_{i=1}l(y_{i},f(x_{i}))$$
*with no limit to choose $f$, can pick the following **bad** function*
$$f(x)=

    \alpha(x)=\left\{
                \begin{array}{ll}
                  y_{i}\text{ if}x=x_{i}\\
                  0\text{ else}
                \end{array}
              \right.
  
$$
*need to restrict the set of candidate functions $f$ to a family $F$*
##### Common Function Families $F$
- Linear models $$f(x)=w^{\top}x+v=w_{1}x_{1}+...+w_{d}x_{d}+v$$
- Generalized linear models $$f(x)=\theta_{1}\psi_{1}(x)+...+\theta_{m}\psi_{m}(x)=\theta^{\perp}\Phi$$
- (Deep) neural nets
- Kernel methods
	- Least squares, logistic regression, support vector machines (SVM)

### Vectors
- A <font color="HotPink" style="font-style: italic;">vector</font> is an ordered list of numbers
- Written as $$\left[\
                \begin{array}
                  -1.1\\
                  0.0\\
                  3.6\\
                  -7.2
                \end{array}
              \right]$$
*or $(-1.1, 0.0, 3.6, -7.2)$, but still interpreted as column vector*

- Numbers in the list are the <font color="HotPink" style="font-style: italic;">elements</font> (entries, coefficients, components)
- Number of elements is the <font color="HotPink" style="font-style: italic;">dimension</font> or *length* of the vector
- Vector above has dimension 4; it's third entry is 3.6
- Vector of size $m$ is an m-vector
- Numbers (1-vectors) are referred to as <font color="HotPink" style="font-style: italic;">scalars</font>


- We use symbols to denote vectors, e.g. $a, X, p, \beta, E^{aut}$
- Prof likes using lowercase bold $\textbf{a}$ (i will just use $a$)
- Set of $m$-vectors with real elements is denoted $\mathbb{R}^m$
$$a\in\mathbb{R}^{m}$$
- $j$th element of $m$-vector $a$ is denoted $a_{j}$
- if $a$ is above vector, $a_{3}=3.6$
- in $a_{j},\,j$ is the index
- for an $m$-vector, indexes run from $j = 1$ to $j = m$
- <font color="red" style="font-style: italic; font-weight: bold;">WARNING</font> : sometimes $a_{i}$ refers to the $i$th vector in a list of vectors
- two vectors a and b of the same size are equal if $a_j = b_j$ for all $j$
- we overload “=” and write this as $a = b$
