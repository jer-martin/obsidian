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

*The learned relationship* $y \approx f(x)$ is ***inductive, not deductive***
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

#### Empirical Risk Minimization
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
#### Common Function Families $F$
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
- Vector of size $m$ is an <font color="HotPink" style="font-style: italic;">m-vector</font>
- Numbers (1-vectors) are referred to as <font color="HotPink" style="font-style: italic;">scalars</font>

#### Conventions
- We use symbols to denote vectors, e.g. $a, X, p, \beta, E^{aut}$
- Prof likes using lowercase bold $\textbf{a}$ (i will just use $a$)
- Set of $m$-vectors with real elements is denoted $\mathbb{R}^m$
$$a\in\mathbb{R}^{m}$$
- $j$th element of $m$-vector $a$ is denoted $a_{j}$
- if $a$ is above vector, $a_{3}=3.6$
- in $a_{j},\,j$ is the index
- for an $m$-vector, indexes run from $j = 1$ to $j = m$

<font color="red" style="font-style: italic; font-weight: bold;">WARNING</font> : sometimes $a_{i}$ refers to the $i$th vector in a list of vectors

- two vectors a and b of the same size are equal if $a_j = b_j$ for all $j$
- we overload “=” and write this as $a = b$

#### Block vectors and sub-vectors
- suppose $b, c,$ and $d$ are vectors with sizes $m, n, p$
- the <font color="HotPink" style="font-style: italic;">stacked vector</font> or <font color="HotPink" style="font-style: italic;">concatenation</font> (of $b, c$ and $d$) is $$a=\left[\
                \begin{array}
                  0
                  b\\
                  c\\
                  d
                \end{array}
              \right]$$
- also called a <font color="HotPink" style="font-style: italic;">block vector</font>, with block entries $b$, $c$, and $d$
- $a$ has size $m + n + p$ $$a = (b_{1},b_{2},...,b_{m},c_{1},c_{2},...,c_{n},d_{1},d_{2},...,d_{p})$$
- reversely, $b$, $c$, and $d$ are called <font color="HotPink" style="font-style: italic;">subvectors</font> of $a$
- <font color="HotPink" style="font-style: italic;">colon notation</font> (borrowed from CS) $$b=a_{1:m} \quad c=a_{(m+1):(m+n)} \quad d=a_{(m+n+1):(m+n+p)}$$
#### Zero, ones, and unit vectors
- $m$-vector with all entries $0$ is denoted $0_{m}$ or just $0$
- $m$-vector with all entries $1$ is denoted $1_{m}$ or just $1$
- a <font color="HotPink" style="font-style: italic;">unit vector</font> has one entry $1$ and all others $0$
- denoted $e_{j}$ where $j$ is the index of the entry that is $1$
- unit vectors of length 3: $$e_{1}=\left[\ 
                \begin{array} 
                  0 
                  1\\ 
                  0\\ 
                  0 
                \end{array} 
              \right] \quad e_{2}=\left[\ 
                \begin{array} 
                  0 
                  0\\ 
                  1\\ 
                  0 
                \end{array} 
              \right] \quad e_{3}=\left[\ 
                \begin{array} 
                  0 
                  0\\ 
                  0\\ 
                  1 
                \end{array} 
              \right]$$
#### Sparse vectors
- a vector is <font color="HotPink" style="font-style: italic;">sparse</font> if many of its entries are $0$
- can be stored and manipulated efficiently on a computer
- $nnz(x)$ is a number of entries that are nonzero
- examples: zero vectors, unit vectors

#### Location or displacement in 2-D or 3-D
- 2-vector $(x_{1},x_{2})$ can represent a location or a displacement in 2-D or 3-D

#### Signals or time series
- elements of $m$-vector are values of some quantity at $m$ different times
	- hourly temperature over period of $m$ hours
	- daily return of a stock for period of $m$ training days
	- cash flow: payments to an entity over $m$ periods (e.g. quarters)

#### Images, video
- monochrome image: grayscale of $M\times N$ pixels stored as $MN$-vector
	- e.g. row-wise
$$a=\left[\ 
                \begin{array} 
                  0 
                  x_{1}\\ 
                  ...\\ 
                  x_{n} 
                \end{array} 
              \right]=\left[\ 
                \begin{array} 
                  0 
                  0.65\\ 
                  ...\\ 
                  0.28 
                \end{array} 
              \right]$$
- color image: $3MN$-vectors with R,G,B values of the $MN$ pixels
- video: $3MNK$-vectors with $K$ frames of colored images with $MN$ pixels

#### Word count vectors
- a short document $$\text{[Word] count vectors are used [in] computer based [document] analysis. [Word].} $$
- a small <font color="HotPink" style="font-style: italic;">dictionary</font> and <font color="HotPink" style="font-style: italic;">word count vector</font> $$\left[ 
                \begin{array} 
                   0
                  \text{word}\\ 
                  \text{in}\\ 
                  \text{document} \\
                  \text{dog}
                \end{array} 
              \right]=\left[\ 
                \begin{array} 
                  0 
                  2\\ 
                  1\\ 
                  1\\
                  0
                \end{array} 
              \right]$$
<div style="text-align: center; width: 100%;">dictionaries used in practice are much larger... </div>

#### Feature vectors
- contain values of variables or attributes that describe members of a set
**examples:**
- age, weight, blood pressure, gender, ... , of patients
- square footage, # bedrooms, list price, ... , of houses in an inventory=
**note:**
- vector elements can represent very different quantities, in different units
- can contain categorical features (e.g. 1/0 for house/condo)
- ordering has no particular meaning


 
