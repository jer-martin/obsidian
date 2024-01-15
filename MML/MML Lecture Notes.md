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
*Criterion to find $f(.)$:
$$\text{minimize}_{f}\text{ }E[l(y,f(x))]$$
- Among all possible $(x,y)$ pairs, treat as random variables
- $l(.,.)$ is some loss/risk function to measure error
- Pretend we know the distributions of $(x,y)$ generative models
- or, replace expectation $E[.]$ with sample average

*Generative models*:
- regression: Wiener filter
- classification: Gaussian discriminant analysis
- naive Bayes
- latent variable modeling for unsupervised learning:
	- Gaussian mixture model
	- Probabilistic PCA

#### Empirical Risk Minimization
*Replace expectation* $E[.]$ *with sample average*
$$\text{minimize}_{f} \text{} \frac{1}{n}\sum\limits^{n}_{i=1}l(y_{i},f(x_{i}))$$
*with no limit to choose* $f$, *can pick the following **bad** function*
$$f(x)=

    \alpha(x)=\left\{
                \begin{array}{ll}
                  y_{i}\text{ if}x=x_{i}\\
                  0\text{ else}
                \end{array}
              \right.
  
$$
*need to restrict the set of candidate functions* $f$ *to a family* $F$
#### Common Function Families $F$
- Linear models $$f(x)=w^{\top}x+v=w_{1}x_{1}+...+w_{d}x_{d}+v$$
- Generalized linear models $$f(x)=\theta_{1}\psi_{1}(x)+...+\theta_{m}\psi_{m}(x)=\theta^{\perp}\Phi$$
- (Deep) neural nets
- Kernel methods
	- Least squares, logistic regression, support vector machines (SVM)

## Vectors
### Overview
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

### Vector Operations
#### Vector Addition
- $m$-vectors $a$ and $b$ can be added, with sum denoted $a + b$
- to get sum, add corresponding entries $$\left[\ 
                \begin{array} 
                  - 
                  0\\ 
                  7\\ 
                  3 
                \end{array} 
              \right] + \left[\ 
                \begin{array} 
                  - 
                  1\\ 
                  2\\ 
                  0 
                \end{array} 
              \right] = \left[\ 
                \begin{array} 
                  - 
                  1\\ 
                  9\\ 
                  3 
                \end{array} 
              \right]$$
- subtraction works in the same way
##### Properties of Vector addition
- commutative: $a + b = b + a$
- associative: $(a + b) + c = a + (b + c), \; a + b + c$
- $a + 0 = 0 + a = a$
- $a - a = 0$
##### Adding Displacement
- if $2$-vectors $a$ and $b$ are displacements, $a + b$ is the sum displacement
![center](../zassets/Pasted%20image%2020240115140400.png)
- displacement from point $q$ to point $p$ is $p - q$
![center](../zassets/Pasted%20image%2020240115140431.png)

#### Scalar-Vector multiplication
- scalar $\beta$ and $d$-vector $a$ can be multiplied $$\beta a = (\beta a_{1},...,\beta a_{d})$$
- also denoted as $a\beta$ $$(-2)\left[\ 
                \begin{array} 
                  0 
                  1\\ 
                  9\\ 
                  6 
                \end{array} 
              \right]=\left[\ 
                \begin{array} 
                  0 
                  -2\\ 
                  -18\\ 
                  -12 
                \end{array} 
              \right]$$
##### Properties of Scalar-Vector multiplication
- associative: $(\beta\gamma)a = \beta(\gamma a)$
- left distributive: $(\beta + \gamma)a = \beta a + \gamma a$
- right distributive: $\beta(a + b) = \beta a + \beta b$

#### Linear combinations
- for vectors $a_{1},...,a_{n}$ and scalars $\beta_{1},...,\beta_{n}$, $$\beta_{1}a_{1},...,\beta_{n}a_{n}$$
	is a <font color="HotPink" style="font-style: italic;">linear combination</font> of the vectors
- $\beta_{1},...,\beta_{n}$ are the <font color="HotPink" style="font-style: italic;">coefficients</font>
- a simple identity: for any $m$-vector $b$ $$b = b_{1}e_{1}+...+b_{m}e_{m}$$
- two vectors $a_{1}$ and $a_{2}$ and linear combination $b = 0.75 a_{1}+ 1.5 a_{2}$
![center](../zassets/Pasted%20image%2020240115141229.png)

#### Inner Product
- <font color="HotPink" style="font-style: italic;">inner product</font> (or <font color="HotPink" style="font-style: italic;">dot product</font>) of $m$-vectors $a$ and $b$ is $$a^{\top}b= a_{1}b_{1}+...+a_{m}b_{m}$$
- other notations used: $$<a,b>\;\;<a|b>\;\;(a,b)\;\;\;\;a \cdot b$$
$$\left[\ 
                \begin{array} 
                  - 
                  -1\\ 
                  2\\ 
                  2 
                \end{array} 
              \right]^{\top}\left[\ 
                \begin{array} 
                  - 
                  1\\ 
                  0\\ 
                  -3 
                \end{array} 
              \right] = (-1)(1)+(2)(0)+(2)(-3)=-7$$
##### Properties of Inner Product
- commutative: $a^\top b = b^\top a$
- associative with scalar multiplication: $(\gamma a)^{\top}b = \gamma (a^{\top}b)$
- distributive with vector addition: $(a+b)^{\top}c=a^{\top}c + b^{\top}c$ 
- block vectors
$$\left[\ 
                \begin{array} 
                  - 
                  a_{1}\\ 
                  ...\\ 
                  a_{k} 
                \end{array} 
              \right]^{\top}\left[\ 
                \begin{array} 
                  - 
                  b_{1}\\ 
                  ...\\ 
                  b_{k} 
                \end{array} 
              \right] = a_{1}^{\top}b_{1} +...+a_{k}^{\top}b_{k}$$
    if the partitions make sense
#### Examples
- $e_{i}^{\top}a = a_{i}$ (picks out $i$th entry)
- $1^{\top}a=a_{1}+...+a_{m}$ (sum of entries)
- $a^{\top}a = a^{2}_{i}+...+a_{m}^{2}$ (sum of squares of entries)
- $w$ is weight vector, $f$ is feature vector; $w^{\top}f$ is score
- $p$ is price vector, $q$ is quantities; $p^{\top}q$ is total cost

### Complexity
##### Flop Count:
- total number of floating point operations in an algorithm
- in linear algebra, typically a polynomial of the dimensions in the problem
- a crude predictor of runtime: $$\text{runtime}=\frac{\text{\# of operations (flops)}}{\text{computer speed (flops / sec)}}$$
- dominant term: the highest order term in the flop count $$\frac{1}{3}m^{3} + 100m^{2}+ 10m + 5 \approx \frac{1}{3}m^{3}$$
- order: the power in the dominant term (big $\mathcal{O}$ notation) $$\frac{1}{3}m^{3}+100m^{2}+10n+5=\mathcal{O}(m^{3}) $$
##### Complexity of Vector Addition, Inner Product
- $x + y$ needs $m$ additions, so $m$ flops
- $\gamma x$ needs $m$ multiplications, so $m$ flops
- $x^{\top}y$ needs $m$ multiplications and $m-1$ additions, so $2m-1 \approx 2m$ flops
- all $\mathcal{O}(m)$ operations
- much less when $x$ or $y$ is sparse: $\mathcal{O}(\text{nnz})$

### Norm
- a function used to measure the size of a vector $a$, denoted $||a||$
- properties: for any $m$-vectors $a$ and $b$ and any scalar $\gamma$
	- non-negativity: $||a|| \ge 0$
	- definiteness: $||a|| = 0$ only if $a=0$
	- homogeneity: $||\gamma a||=|\gamma|\;||a||$
	- triangle inequality: $||a+b||\le ||a|| +||b||$
- the <font color="HotPink" style="font-style: italic;">Euclidean Norm</font> (or just <font color="HotPink" style="font-style: italic;">norm</font>) of an $m$-vector $a$ is $$||a||=\sqrt{a_{1}^{2}+...+a_{m}^{2}}=\sqrt{a\top a}$$
- reduced to absolute value for $m = 1$
- more generally: vector $\mathscr{l}_p$ norms $$||a||_{p}=(|a_{1}|^{p}+...+|a_{m}|^{p})^\frac{1}{p}$$
##### Special Cases
- $p =2$: Euclidian norm or $\mathscr{l}_{2}$ norm
- $p =1$: $\mathscr{l}_{1}$ norm, $||a||_{1} = |a_{1}|+...+|a_{m}|$
- $p = \infty$: $\mathscr{l}_{\infty}$ norm, $||a||_{\infty} = \text{max}(|a_{1}|,...,|a_{m}|)$

#### Euclidean Norm
- useful equality $$||a+b||^{2}=||a||^{2}+2a^{\top}b +||b||^{2}$$
- similarly, $$||a-b||^{2}=||a||^{2}-2a^{\top}b+||b||^{2}$$
#### Cauchy-Schwarz Inequality
- for two $m$-vectors $a$ and $b$, $|a^{\top}b\le||a||\;||b||$
- assume $\alpha = ||a||$ and $\beta = b$ $$2||a||^{2}||b||^{2}\pm2\;||a||\;||b||\;a^{\top}b$$
- equality if $a$ or $b$ is 0
- otherwise, divide by $2||a||\;||b||$ to get $$\pm a^{\top}b\le||a||\;||b||$$ $$|a^{\top}b|=||a||\;||b|| \text{ if } a=\gamma b \text{ for some scalar } \gamma$$
#### Triangle Inequality for Euclidean Norm
$$||a+b||\le||a||+||b||$$
### Distance
- (Euclidean) distance between $m$-vectors $a$ and $b$ is $||a-b||$
- agrees with ordinary distance for $m = 1,2,3$ ![center](../zassets/Pasted%20image%2020240115151219.png)
- triangle inequality $$||a-c||=||(a-b) + (b-c)||\le||a-b||+||b-c||$$![center](../zassets/Pasted%20image%2020240115151312.png)




 
