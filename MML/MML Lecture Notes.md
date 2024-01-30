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
## Nearest Neighbor Predictor
- We are given data set $(x_{1},y_{1}),...,(x_{n},y_{n})$
- among $x_{1},...,x_{n}, x_{i}$ is the nearest neighbor of $x$ if $$||x-x_{i}||\le||x-x_{j}||,\: j=1,...,n$$
- <font color="HotPink" style="font-style: italic;">nearest neighbor predictor</font>:
	- given new sample $x$, find its nearest neighbor $x_{i}$
	- then predict $\hat{y}=f(x)=y_{i}$
- works for both regression and classification
- 'training' is easy: requires no computation
- model requires to memorize the entire data set $(x_{1},y_{1}),...,(x_{n},y_{n})$
- *what is the complexity when making one prediction?*
	- $\mathcal{O}(mn)$, you have to check all data
##### Example
- prediction function $f$ is a piece-wise constant function
![center](../zassets/Pasted%20image%2020240116123650.png)
- dots show data points $(x_{i},y_{i}), x_{i} \in \mathbb{R}^{2}\;\; (d=2),$ red surface is $\hat{y}=f(x)$

### $k$-nearest neighbor predictor
- given data set $(x_{1},y_{1}),...,(x_{n},y_{n})$
- given new sample $x$, find its $k$ nearest neighbors $x_{i1},...,x_{ik}$
- <font color="HotPink" style="font-style: italic;">k-nearest neighbors regression</font> predicts the average $$\hat{y}=f(x)=\frac{1}{k}(y_{i1}+...+y_{ik})$$
- <font color="HotPink" style="font-style: italic;">k-nearest neighbors classification</font> (binary) predicts the majority vote $$\hat{y}=f(x)=\text{argmax}_{\text{c=1,2}}(\text{ \# of points in } x_{i1},...,x_{ik}\text{ with }y_{i}=c\;) $$
	- usually with odd $k$
	- could extend to multiple classes, but *needs to solve problems with tie votes*
- again, training is easy: requires no computation
- model requires memorization of dataset

## K-Means Clustering
### Clustering
- given $n$ $d$-vectors $x_{1},...,x_{n}$
- goal: partition into $k$ groups
- want vectors in the same group to be close to one another
##### Examples
- topic discovery and document classification
	- $x_{i}$ is word count histogram for document $i$
- patient clustering
	- $x_{i}$ are patient attributes, test results, symptoms
- costumer market segmentation
	- $x_{i}$ is purchase history and other attributes
- color compression of images
	- $x_i$ are RGB pixel values
- financial sectors
	- $x_{i}$ are $n$-vectors of financial attributes

#### Clustering objective
- $\mathcal{G}_{c}\subset{1,...,n}$ is group $c$, for $c=1,...,k$
- $c_{i}$ is group that $x_{i}$ is in: $i\in\mathcal{G}_{ci}$
- <font color="HotPink" style="font-style: italic;">group representatives</font>: $d$-vectors $y_{1},...,y_{k}$
- clustering objective is $$L^{clust}=\sum\limits^{m}_{i=1}||x_{i}-y_{ci}||^{2}$$
	mean square distance from vectors to associated representative
- $L^{clust}$: smaller means good clustering
- goal: choose clustering $c_{i}$ and representatives $y_{c}$ to minimize $L^{clust}$
#### Partitioning the vectors given representatives
- suppose representatives $y_{1},...,y_{k}$ are given
- *how do we assign the vectors to groups? i.e., choose* $c_{1},...,c_{n}$
- $c_{i}$ only appears in term $||x_{i}=y_{ci}||^{2}$ in $L^{clust}$
- to minimize over $c_{i}$, choose $c_{i}$ so $||x_{i}-y_{ci}||^{2}=\text{min}_{c=1,...,k}||x_{i}-y_{c}||^{2}$
- i.e., assign each vector to its nearest representative
#### Choosing representatives given the partition
- suppose partition $\mathcal{G}_{1},...,\mathcal{G}_{k}$, i.e., the assignments $c_{1},...,c_{n}$ are given
- how do we choose representatives $y_{1},...,y_{k}$?
- $L^{clust}$ splits into a sum of $k$ sums, one for each $y_{c}$ $$L^{clust}=\sum\limits_{i\in\mathcal{G}_{1}}||x_{i}-y_{1}||^{2}+...+\sum\limits_{i\in\mathcal{G}_{k}}||x_{i}-y_{k}||^{2}$$
- $y_{c}$ should be the average (<font color="HotPink" style="font-style: italic;">centroid</font>) of the points in the partition $$y_{c}=\text{argmin}_{y}\sum\limits_{i\in\mathcal{G}_{c}}||x_{i}-y||^{2}=\frac{1}{\mathcal{G_{j}}}\sum\limits_{i\in\mathcal{G}_{c}}x_{i} $$
### K-Means Algorithm
- alternate between updating the partition, then the representatives
- a famous algorithm called $k$-means
- objective $L^{clust}$ decreases in each step
##### Algorithm Steps:
1. given $x_{1},...,x_{n}\in\mathbb{R}^{d}$
2. initialize $y_{1},...,y_{k}\in\mathbb{R}^{d}$
3. **repeat**
	1. <font style="color:crimson;font-weight:bold">update partition:</font> assign $i$ to $\mathcal{G}_{c}$ where $c=\text{argmin}_{c}||x_{i}-y_{c}||^2$ 
	2. <font color="crimson" style="font-weight: bold;">update centroids:</font> $y_{c}=1/|\mathcal{G}_{c}|\sum\limits_{i\in\mathcal{G}_{c}}x_{i}$
4. **until** $y_{1},...,y_{k}$ stop changing

#### Convergence of K-Means
- $L^{clust}$ goes down in each step until the $y_{c}$'s stop changing
- but (in general) the $k$-means algorithm <font color="crimson" style="font-weight: bold;">does not</font> find the partition that minimizes $L^{clust}$
- $k$-means is a <font color="HotPink" style="font-style: italic;">heuristic</font>:
	- it is not guaranteed to find the smallest value of $L^{clust}$
- the final partition (therefore its value of $L^{clust}$) can depend on initialization
- common approach:
	- run $k$-means 10 times, with different (often random) initial representatives
	- take as final partition the one with the smallest $L^{clust}$

## Linear Functions
- $f\;:\;\mathbb{R}^{d}\rightarrow\mathbb{R}$ means $f$ is a function that maps $d$-vectors to numbers
- $f$ satisfies the <font color="HotPink" style="font-style: italic;">superposition property</font> if $$f(\alpha x +\beta y)=\alpha f(x)+\beta f(y)$$
	holds for all numbers $\alpha, \beta$ and $d$-vectors $x,y$
- *be sure to parse this very carefully!*
- a function that *satisfies superposition* is called <font color="HotPink" style="font-style: italic;">linear</font>
- can be extended to more elements $$f(\alpha_{1}x_{1}+...+\alpha_{n}x_{n})=\sum\limits^{n}_{i=1}\alpha_{i}f(x_{i})$$
#### The Inner Product Function
- with $w$ an $m$-vector, the function $$f(x)=w^{\top}x=w_{1}x_{1}+...+w_{n}x_{n}$$
	is the inner product function
- $f(x)$ is a weighted sum of the entries of $x$
- the inner product function is linear $$f(\alpha x + \beta y)=a^{\top}(\alpha x + \beta y) = \alpha a^{\top}x + \beta a^{\top}y = \alpha f(x) + \beta f(y)$$
- and all linear functions are inner products! $$f(x)=f(x_{1}e_{1}+...+x_{d}e_{d})=x_{1}f(e_{1})+...+x_{d}f(e_{d})=w^{\top}x$$
	where $w_{i}=f(e_{i})$ for $i = 1,...,d$

#### Affine Functions
- a function is called <font color="HotPink" style="font-style: italic;">affine</font> if and only if $$f(\alpha x +\beta y)=\alpha f(x)+\beta f(y)$$
	holds for $\alpha, \beta$ with $\alpha + \beta=1$ and all $d$-vectors $x,y$
- the inner product function plus a constant $f(x)=w^{\top}x+v$ is affine $$f(\alpha x + \beta y)=w^{\top}(\alpha x + \beta y) +v= \alpha(w^{\top}x+v) + \beta(w^{\top}y+v)= \alpha f(x) + \beta f(y)$$
- and all affine functions have such forms $$\begin{align}f(x)&=f(x_{1}e_{1}\;+...+\;x_{d}e_{d}+(1-1x)0)\\&=x_{1}f(e_{1})+...+x_{d}f(e_{d})+(1-1x)f(0)=w^{\top}x+v\end{align}$$
	where $w_{i}=f(e_{i})-f(0)$ for $i=1,...,d$ and $v=f(0)$

<font color="crimson" style="font-weight: bold;">LINEAR FUNCTIONS MUST GO THROUGH ORIGIN - THEREFORE, ALL LINEAR FUNCTIONS ARE AFFINE, BUT ALL AFFINE FUNCTIONS ARE NOT LINEAR</font>

#### Affine Approximation
- Suppose $f$: $\mathbb{R}^{d}\rightarrow\mathbb{R}$ (not necessarily linear or affine)
- first-order Taylor approximation of $f$, near point $z$: $$\hat{f}(x;z)=f(z)+\frac{\delta f}{\delta x_{1}}(z)(x_{1}-z_{1})+...+\frac{\delta f}{\delta x_{d}}(z)(x_{d}-z_{d})$$
- $\hat{f}(x;z)$ is close to $f(x)$ when all $x_{i}$ are close to $z_i$
- $\hat{f}$ is affine (slang: linear approximation)
- can write inner product as $$\hat{f}(x;z)=f(z)+\nabla f(z)(x-z)$$
	where $n$-vector $\nabla f(z)$ is the gradient of $f$ at $z$
##### Example
- consider the nonlinear function $f$: $\mathbb{R}^{2}\rightarrow\mathbb{R}$ $$f(x)=x_{1}+\text{exp}(x_{2}-x_{1})$$
- gradient of $f$ at $z = (1,2)$ $$\nabla f(z)=\left[\ 
                \begin{array} 
                  - 
                  1-\text{exp}(z_{2}-z_{1})\\ 
                  \text{exp}(z_{2}-z_{1})
                \end{array} 
              \right]=\left[\ 
                \begin{array} 
                  - 
                  -1.7183\\ 
                  2.7183
                \end{array} 
              \right]$$
- first order Taylor approximation at $z$ $$\hat{f}(x;z)=3.7183+\left[\ 
                \begin{array} 
                  - 
                  -1.7183\\ 
                  2.7183
                \end{array} 
              \right]^{\top}\left[\ 
                \begin{array} 
                  - 
                  x_{1}-1\\ 
                  x_{2}-2
                \end{array} 
              \right]=3.7183-1.7183(x_{1}-1)+2.7183(x_{2}-2)$$
![center](../zassets/Pasted%20image%2020240118095316.png) 

 
### Regression model
- regression model is a hypothetical relationship between $x$ and $\hat{y}$ $$\hat{y}=w^{\top}x+v$$
	is an affine function of $x$
- $x$ is a feature vector; its elements $x_{i}$ are called regressors
- $d$-vector $w$ is the weight vector
- scalar $v$ is the offset
- scalar $\hat{y}$ is the prediction (of some actual outcome or dependent variable, labeled $y$)
- simplified notation $$\hat{y}=\left[\ 
                \begin{array} 
                  - 
                  v\\ 
                  w\\ 
                \end{array} 
              \right]^{\top}\left[\ 
                \begin{array} 
                  - 
                  1\\ 
                  x\\ 
                \end{array} 
              \right]=w^{\top}x$$
##### Example
- $y$ is selling price of house in $1000 (in some location, over some period)
- regressor is $$x = \text{(house area, \# of bedrooms)}$$
	(house area in 1000s of sq.ft.)
- regression model weight vector and offset are $$w=(148.73,-18.85),\;v=54.40$$
- prediction performance
![center](../zassets/Pasted%20image%2020240118100009.png)

![center](../zassets/Pasted%20image%2020240118100033.png)

#### Finding a linear regression model
- how to find good choice of $w$ and $v$?
- fit the model to the data set $(x_{1},y_{1}),...,(x_{n},y_{n})$
- residual for data sample $i$ is $$r_{i}=w^{\top}x_{i}+v-y_{i}=w^{\top}x-y_{i}$$
- <font color="HotPink" style="font-style: italic;">least squares regression:</font> choose $w$ that minimizes sum of squared residuals $$\text{minimize}_{w}\;\;\sum\limits^{n}_{i=1}(w^{\top}x_{i}-y_{i})^{2}$$
	equivalent to minimizing the mean squared error (MSE) <font color="crimson" style="font-weight: bold;">(why?)</font>
- we will learn how to solve it in the sequel

### Linear Classification
#### Binary Classification
- data fitting with two possible outcomes
	- true or false
	- spam or not spam
	- positive or negative
	- 0 or 1
- we encode outcomes as +1 (true) and -1 (false)
- classifier has form $\hat{y}=f(x),f:\mathbb{R}^{d}\rightarrow\{+1,-1\}$
- a linear classifier $f:\mathbb{R}^{d}\rightarrow\{\pm1\}$ has form $$\hat{y}=\text{sign}(w^{\top}x+v)=\text{sign}(w^{\top}x)$$
	the sign of an affine function of $x$

#### Confusion Matrix
- only four possibilities
	- true positive: $y = +1, \hat{y}=+1$
	- true negative: $y=-1,\hat{y}=-1$
	(in these two cases the prediction is correct)
	- false positive: $y=-1,\hat{y}=+1$
	- false negative: $y=+1,\hat{y}=-1$
	(in these two cases, the prediction is incorrect)
- given data set and classifier, count each of the four outcomes
![center](../zassets/Pasted%20image%2020240118101637.png)
- many error rates and accuracy measures are used
	- error rate: $n_{fn}+n_{fp}/n$
	- false positive rate (false alarm): $n_{fp}/n_{n}$
	- true positive rate (recall): $n_{tp}/n_{p}$
	- precision: $n_{tp}/(n_{tp}+n_{fp})$

##### Example
- spam filter performance on a set of emails (say)
![center](../zassets/Pasted%20image%2020240118101817.png)
- error rate: $(19+32)/1266=4.03\%$
- false positive rate: $19/1139=1.67\%$
- recall: $95/127=74.8\%$
- precision: $95/114=83.33\%$

#### Multi-way classification
- we have $k > 2$ possible labels, with label set $\{1,...,k\}$
- predictor is $\hat{f}:\mathbb{R}^{d}\rightarrow\{1,...,k\}$
- for given predictor and data set, confusion matrix is $k \times k$
- some off-diagonal entries may be much worse than others

#### Multi-way linear classifier
- create a "linear" function $w^{\top}_{c}x-v_{c}$ for each of the $c = 1,...,k$ classes
- a linear classifier $f:\mathbb{R}^{d}\rightarrow\{1,...,k\}$ has form $$\hat{y}=\text{arg}\text{max}_{c=1,...,k}(w^{\top}_{c}x+v_{c})=\text{arg}\text{max}_{c=1,...,k}(\tilde{w^{\top}_{c}\tilde{x}}))$$
- for example, with $$\tilde{w}^{\top}_{1}\tilde{x}=-0.7,\;\tilde{w}^{\top}_{2}\tilde{x}=+0.2, \;\tilde{w}^{\top}_{3}\tilde{x}=+0.8$$
	then $\hat{y}=3$, i.e., we predict it belongs in the 3rd class

#### Finding a linear classification model
- binary classifier $f(x) = \text{sign}(w^{\top}x+v)=\text{sign}(\tilde{w}^{\top}\tilde{x})$
- fit the model to the data set $(x_{1},y_{1}),...,(x_{n},y_{n})$
- we wish $\tilde{w}^{\top}\tilde{x}_{i}$ to be close to $+1$ if $y_{i}=+1$ and near $-1$ if $y_{i}=-1$ (though not necessary)
- least squares classification: choose $\tilde{w}$ that minimizes sum of squared residuals $$\text{minimize}_{\tilde{w}}\;\sum\limits^{n}_{i=1}(\tilde{w}^{\top}\tilde{x}_{i}-y_{i})^{2}$$
	looks almost identical to least squares regression
- Multi way classification $f(x)=\text{argmax}_{c}(\tilde{w}_{c}^{\top}\tilde{x})$
- each $\tilde{w}_{c}$ obtained form binary classifier ($c$ vs not $c$)

### Linear Independence
- a set of $n$-vectors $a_{i},...,a_{k}$ is <font color="HotPink" style="font-style: italic;">linearly dependent</font> if $$\gamma_{1}a_{1}+...+\gamma_{k}a_{k}=0$$
	holds for some $\gamma_{1},...,\gamma_{k}$ that are not all zero
- equivalent to: at least one $a_{i}$ is a linear combination of the others
- we say '$a_{1},...,a_{k}$ are linearly dependent'
- ${a_{1}}$ is linearly dependent only if $a_{1}=0$
- $\{a_{1},a_{2}\}$ is linearly dependent only if one $a_{i}$ is a multiple of the other
- for more than two vectors, there is no simple to state condition
##### Example
- the vectors $$a_{1}=\left[\ 
                \begin{array} 
                  - 
                  0.2\\ 
                  -7\\ 
                  8.6 
                \end{array} 
              \right],\;a_{2}=\left[\ 
                \begin{array} 
                  - 
                  0.1\\ 
                  2\\ 
                  -1 
                \end{array} 
              \right],\;a_{3}=\left[\ 
                \begin{array} 
                  - 
                  0\\ 
                  -1\\ 
                  2.2 
                \end{array} 
              \right]$$
    are linearly dependent, since $a_{1}+2a_{2}-3a_{3}=0$
- can express any of them as linear combination of the other two, e.g., $$a_{2}=-\frac{1}{2}a_{1}+ \frac{3}{2}a_{3}$$
### Linear Independence
- set of $n$-vectors $a_{1},...,a_{k}$ is <font color="HotPink" style="font-style: italic;">linearly independent</font> if $$\gamma_{1}a_{1}+...+\gamma_{k}a_{k}=0$$
	holds only when $\gamma_{1}=...\gamma_{k}=0$
- equivalent to: no $a_{i}$ is a linear combination of the others
- we say '$a_{1},...,a_{k}$ are linearly independent'

#### Linear combinations of linearly independent vectors
- suppose $b$ is a linear combination of linearly independent vectors $a_{1},...,a_{k}$: $$b=\gamma_{1}a_{1}+...+\gamma_{k}a_{k}$$
- the coefficients $\gamma$ are <font color="HotPink" style="font-style: italic;">unique</font> if $$b=\gamma_{1}a_{1}+...+\gamma_{k}a_{k}$$
	then $\gamma_{i}=\gamma_{i}$ for $i=1,...,k$
- this means that (in principle) we can deduce the coefficients from $b$

### Basis
- if $\{a_{1},...,a_{k}\}\subset\mathbb{R}^{n}$ is linearly independent, then $k\le n$
- a set of $n$ linearly independent $n$-vectors $a_{1},...,a_{n}$ is called a basis
- <font color="crimson" style="font-weight: bold;">any</font> $n$-vector $b$ can be expressed as a linear combination of them $$b=\gamma_{1}a_{1}+...+\gamma_{n}a_{n}$$
	for some $\gamma$
- and these coefficients are <font color="crimson" style="font-weight: bold;">unique</font>
- formula above is called an <font color="HotPink" style="font-style: italic;">expansion</font> of $b$ in the $a_{1},...,a_n$ basis

### Subspace
- given $a_{1},...,a_{k}$, the set of all linear combinations of them is a <font color="HotPink" style="font-style: italic;">subspace</font> $$\text{span}\{a_{1},...,a_{k}\}=\{\sum\limits^{k}_{i=1}\gamma_{i}a_{i}:\gamma_{i}\in\mathbb{R}\}$$
- if $a_{1},...,a_{k}$ are independent, then the <font color="HotPink" style="font-style: italic;">dimension</font> of the subspace is $k$ $$k\le n$$
- for a subspace $\mathcal{S}\subset \mathbb{R}^{n}$ with dimension $k$, define its orthogonal complement $$\mathcal{S}^{\perp}=\set{y\;|\;b^{\top}y=0,\vee b\in \mathcal{S}}$$
	dimension of $\mathcal{S}^{\perp}$ is $n-k$
- $\mathcal{S} ⨁ \mathcal{S}^{\perp}=\mathbb{R}^{n}$
- $\mathcal{S} \cap \mathcal{S}^{\perp}=\set{0}$

### Orthonormal vectors
- set of $n$-vectors $a$ are (mutually) orthogonal if $a_{i}\perp a_{j}$ for $i \ne j$
- they are normalized if $||a_{i}||=1$ for $i=1,...,k$
- they are orthonormal if both hold
- can be expressed using their inner products as $$a_{i}^{\top}a_{j}=\left[\ 
                \begin{array} 
                  - 
                  1\;\;i=j\\ 
                  0\;\;i\ne j\\ 
                   
                \end{array} 
              \right]$$
- orthonormal sets of vectors are linearly independent
- by independence-dimension inequality, must have $k\le n$
- when $k=n$, $a$ are an <font color="HotPink" style="font-style: italic;">orthonormal basis</font> of $\mathbb{R}^{n}$

### Orthonormal Expansion
- expansion of $b$ in the $a$ basis $$b=\gamma_{1}a_{1}+...+\gamma_{n}a_{n}$$
	for some $\gamma$ they and they are unique
- if $a$ is an orthonormal basis, the coefficients are easy to find $$b=(a^{\top}_{1}b)a_{1}+...+(a_{n}^{\top}b)a_{n}$$
- called orthonormal expansion of $b$ (in the orthonormal basis)
- to verify formula, take inner product of both sides with $a_{i}$

### Orthogonal Decomposition
- given a subspace $\mathcal{S}$, any $b\in \mathbb{R}^{n}$ can be written in a unique way as $$b=b_{1}+b_{2},\;\;b_{1}\in\mathcal{S},\;\;b_{2}\in\mathcal{S}^{\perp}$$
- let $\mathcal{S} = \text{span}\set{a_{1},...,a_{k}}$ with $a$ orthonormal
- $b_{2}=b-b_{1}:\;\;b_{2}^{\top}a_{i}=0$ for $i = 1,...,k$
- if $a$ is an orthonormal basis and $\mathcal{S}=\text{span}\set{a_{1},...,a_{k}}$, then $\mathcal{S}^{\perp}=\text{span}{a_{k+1},...,a_{n}}$

### Gram-Schmidt algorithm
>*an algorithm to check if $a_{1},...,a_{k}$ are linearly independent*
	1. given $a_{1},...,a_{k} \in \mathbb{R}^{n}$
	2. **for $i=1,...,k$ do**
		1. orthogonization: $\tilde{q}_{i}=a_{i}-(q_{1}^{\top}a_{i})q_{1}-...-(q_{i-1}^{\top}a_{i})q_{i-1}$ 
		2. test for linear independence: if $||\tilde{q}_{i}||=0$, quit
		3. normalization: $q_{i}=\tilde{q}_{i}/||\tilde{q}_{i}||$
	3. **end for**
- if G-S does not stop early (line 4), $a_{1},...,a_{k}$ are linearly independent
- if G-S terminates at iteration $j$, then $a_{j}$ is a linear combination of $a_{1},...,a_{j-1}$
- it has many other uses

#### Analysis
> *proof by induction that $q_{1},...,q_{i}$ are orthonormal*
- assume its true for $i-1$
- orthogonalization step ensures that $$\tilde{q}_{i}\perp q_{1},...,\tilde{q}_{i}\perp q_{i-1}$$
- to see this, take inner product of both sides with $q_{j}, j<i$ $$\begin{align}q_{j}^{\top}\tilde{q}_{i}&=q_{j}^{\top}a_{i}-(q_{1}^{\top}a_{i})(q_{j}^{\top}q_{1})-...-(q_{i-1}^{\top}a_{i})(q_{j}^{\top}q_{i-1})\\&=q_{j}^{\top}a_{i}-q_{j}^{\top}a_{i}=0\end{align}$$
- so $q_{i}\perp q_{1},...,q_{i}\perp q_{i-1}$
- normalization $q_{i}=\tilde{q}_{i}/||\tilde{q}_{i}||$ ensures $||q_{i}||=1$

> *assuming G-S has not terminated before iteration* $i$
- $a_{i}$ is a linear combination of $q_{1},...,q_{i}$ $$\begin{align}a_{i}&=||\tilde{q}_{i}||q_{i}+(q_{1}^{\top}a_{i})q_{1}+...+(q_{i-1}^{\top}a_{i})q_{i-1}\end{align}$$
- $q_{i}$ is a linear combination of $a_{1},...,a_{k}$: by induction on $i$ $$q_{i}=\frac{1}{||\tilde{q}_{i}||}(a_{i}-(q_{1}^{\top}a_{i})q_{1}-...-(q_{i-1}^{\top}a_{i})q_{i-1})$$
	where each $q_{1},...,q_{i-1}$ is a linear combination of $a_{1},...,a_{i-1}$ (by induction)

> *suppose G-S terminates at iteration $j$*
- $a_{j}$ is a linear combination of $q_{1},...,q_{j-1}$ $$a_{j}=(q_{1}^{\top}a_{i})q_{1}+...+(q_{j-1}^{\top}a_{i})q_{j-1}$$
- and each $q_{1},...,q_{j-1}$ is a linear combination of $a_{1},...,a_{j-1}$
- so $a_{j}$ is a linear combination of $a_{1},...,a_{j-1}$

#### Complexity of G-S algorithm
- orthogonalization step at iteration $i$ requires $i-1$ inner products $$q_{1}^{\top}a_{i},...,q_{i-1}^{\top}a_{i} $$
	which costs $(2n-1)(i-1)$ flops
- another $2n(i-1)$ flops to calculate $\tilde{q}_{i}$
- $3n$ flops to calculate $||\tilde{q}_{i}||$ and $q_{i}$
- total is $$\sum\limits^{k}_{i=1}((4n-1)(i-1)+3n)=(4n-1)\frac{k(k-1)}{2}+3kn\approx2nk^{2}$$
	using $\sum\limits^{k}_{i=1}(i-1)=k(k=1)/2$
- $\mathcal{O}(nk^{2})$ complexity where $k\le n$

### Modified G-S*
> *to determine the dimension of* $\text{span}\set{a_{1},...,a_{k}}$
	1.  given $a_{1},...,a_{k}\in \mathbb{R}^{n}$
	2. $j\leftarrow 0$
	3. **for** $i=1,...,k$ **do**
		1. orthogonization: $\tilde{q}_{j+1}=a_{i}-(q_{1}^{\top}a_{i})q_{1}-...-(q_{j}^{\top}a_{i})q_{j}$ 
		2. test for linear independence: if $||\tilde{q}_{i}||=0$, continue
		3. normalization: $q_{j+1}=\tilde{q}_{j+1}/||\tilde{q}_{j+1}||$
		4. $j\leftarrow j+1$
	4. **end for**
- G-S runs the full $k$ iterations with complexity $\mathcal{O}(nk^2)$
- if $j=r$ at the end, then the dimension of $\text{span}\set{a_{1},...,a_{k}}$ is $r$

## Matrices
- a matrix is a two-dimensional array of numbers, e.g., $$\begin{bmatrix} 
  0 & 1 & -2.3 & 0.1 \\ 
  1.3 & 4 & -0.1 & 0 \\ 
  4.1 & -1 & 0 & 1.7 \\ 
\end{bmatrix}$$
- size is given by (rows)x(columns)
- denoted by a boldface capital letter, e.g., $\mathbf{A}\in \mathbb{R}^{m\times n}$ or $\mathbf{A}\in\mathbb{C}^{m\times n}$ 
- $A_{ij}$ is $i,j$ element of matrix $\mathbf{A}$
- $i$ is row index, $j$ is column, indices start at 1
- two matrices are equal (=) if they're the same size and corresponding entries are equal
### Matrix Shapes
- an $m\times n$ matrix $\mathbf{A}$
	- tall if $m > n$
	- wide if $m < n$
	- square if $m = n$
- a $1 \times 1$ matrix is a number (scalar)
- an $n \times 1$ matrix is an $n$-vector
- a $1 \times n$ matrix is a row vector of length $n$

### Transpose
- the transpose of $\mathbf{A} \in \mathbb{R}^{m\times n}$ is $\mathbf{A}^{\top}\in \mathbb{R}^{m\times n}$ $$\matrix{\mathbf{A}^{\top}}_{ij}=A_{ji}, \;\;i=1,...,n\;j=1,...,m$$
- $(\mathbf(A)^{\top})^{\top}= \mathbf{A}$
- a matrix is <font color="HotPink" style="font-style: italic;">symmetric</font> if $\mathbf{A}= \mathbf{A}^{\top}$

### Block Matrices
- a matrix can be partitioned into blocks $$A=\begin{bmatrix} 
  B & C \\ 
  D & E  

\end{bmatrix}$$
	where $B, C, D, E$ are matrices
- matrices in each block row must have the same number of rows
- matrices in each block column must have same number of rows

### Column and row representations of a matrix
- $\mathbf{A}$ is an $m \times n$ matrix
- can express as a block matrix with its columns $a_{1},...,a_{n}$
	- or as a block matrix with its rows $\tilde{a}_{1},...,\tilde{a}_{n}$
- 4 fundamental subspaces defined by matrix $\mathbf{A}$
	- $\text{Ran}( \mathbf{A}) = \text{span}\set{a_{1},...,a_{n}}$
	- $\text{Ran}( \mathbf{A}^{\top}) = \text{span}\set{\tilde{a_{1}},...,\tilde{a_{n}}}$
	- $\text{Null}(\mathbf{A})=\text{Ran}( \mathbf{A}^{\top})^{\perp}$
	- $\text{Null}(\mathbf{A}^{\top})=\text{Ran}( \mathbf{A})^{\perp}$

### Special Matrices
- $m \times n$ zero matrix has all entries zero, written as $0_{m\times n}$ or simply $0$
- identity matrix $\mathbf{I}$ is square with $\mathbf{I}_{ii}=1$ and $\mathbf{I}_{ij}=0$ for $i\ne j$, e.g., $$\begin{bmatrix} 
  1 & 0 & 0 &\\ 
  0 & 1 & 0  \\ 
  0 & 0 & 1 \\ 
\end{bmatrix}$$
- sparse matrix: most entries are zero

### Matrix Operations
#### Addition, multiplication, scalar norm
- (just like vectors) we can add or subtract matrices of the same size $${[\mathbf{A}+ \mathbf{B}]_{ij}}=A_{ij}+B_{ij}$$
- scalar multiplication: $$[\alpha \mathbf{A}]_{ij}=\alpha A_{ij}$$
	- many obvious properties
- matrix (Frobenious) norm: $$||A||_{F}=\sqrt{\sum\limits^{m}_{i=1}\sum\limits^{n}_{j=1}A^{2}_{ij}}$$
#### Matrix Vector Multipication
- matrix-vector product of $m\times n$ matrix $\mathbf{A}$ and $n$-vector $x$, denoted by $\mathbf{y= Ax}$ with $$y_{i}= A_{i1}x_{1}+...+A_{in}x_{n}$$
- example: $$\begin{bmatrix} 
  0 & 2 & -1 \\ -2 & 1 & 1
\end{bmatrix}\begin{bmatrix} 
  2 \\ 1\\ -1
\end{bmatrix}= \begin{bmatrix} 
  3 \\ -4
\end{bmatrix} 
$$
##### Row interpretation
$$y_{i}=\mathbf{\tilde{a}_{i}^{\top}x}$$
	where $\mathbf{\tilde{a}^{\top}_{1},...,\tilde{a}^{\top}_{m}}$ are rows of $\mathbf{A}$
- $\mathbf{y=Ax}$ is a 'batch' inner product of all rows of $\mathbf{A}$ and $\mathbf{x}$

##### Column Interpretation
- $\mathbf{y=Ax}$ can be expressed as $$\mathbf{y}= \mathbf{x}_{1} \mathbf{a_{1}}+...+ \mathbf{x}_{n} \mathbf{a}_{n}$$
	where $a_{1},...,a_{n}$ are columns of $\mathbf{A}$
- so $\mathbf{y=Ax}$ is a linear combination of columns of $\mathbf{A}$ with coefficients $x_{1},...,x_{n}$
- important example: $\mathbf{Ae}_{j}=a_{j}$
- columns of $\mathbf{A}$ are linearly independent if $\mathbf{Ax}=0$ implies $x=0$
- the 4 fundamental subspaces: 
	- $\text{Ran}( \mathbf{A}) = \{\mathbf{Ax|x}\in \mathbb{R}^{n}\}$
	- $\text{Ran}( \mathbf{A}^{\top}) = \{\mathbf{A^{\top}y|y}\in \mathbb{R}^{m}\}$
	- $\text{Null}(\mathbf{A})=\{\mathbf{x|Ax}=0\}$
	- $\text{Null}(\mathbf{A}^{\top})=\{\mathbf{y|A^{\top}y}=0\}$

##### Complexity
- $m \times n$ matrix $\mathbf{A}$ stored as $m\times n$ array of numbers for sparse $\mathbf{A}$, store only $\text{nnz}( \mathbf{A})$ nonzero values
- matrix addition, scalar-matrix multiplication costs $mn$ flops
- matrix-vector multiplication cost $m(2n-1)\approx 2mn$ flops for sparse $\mathbf{A}$, around $2 nnz(\mathbf{A})$ flops

#### Feature matrix times weight vector
- $\mathbf{X}=[x_{1}x_{2}...x_{n}]$ is $m \times n$ feature matrix
- column $x_{i}$ is feature of $m$-vector of object or sample $i$
- $X_{ij}$ is value of feature $j$ for sample $i$
- $m$-vector $\mathbf{w}$ is weight vector
- $s=\mathbf{X}^{\top}\mathbf{w}$ is vector of scores for each sample: $s_{i}=\mathbf{x_{i}}^{\top}\mathbf{w}$
- $\mathbf{\tilde{X}}=\begin{bmatrix}1\;...\;1\\x_{1}\;...\;x_{n}\end{bmatrix} = \begin{bmatrix}1^{\top}\\X\end{bmatrix}$ is the feature matrix appended with $1^{\top}$
- $\mathbf{\tilde{X}^{\top}\tilde{w}}=[1\;\mathbf{X}^{\top}] \begin{bmatrix}v\\ w\end{bmatrix}=1v+\mathbf{X^{\top}w}= \begin{bmatrix}x_{1}^{\top}+v\\...\\ x_{n}^{\top}w+v\end{bmatrix}$ gives a batch of affine ("linear") predictions

#### Matrix multiplication
- can multiply $\mathbf{A} \in \mathbb{R}^{m\times p}$ and $\mathbf{B} \in \mathbb{R}^{p\times n}$ to get $\mathbf{C}=\mathbf{AB}\in\mathbb{R}^{m\times n}$ $$C_{ij}=\sum\limits^{p}_{k=1}A_{ik}B_{kj}=A_{i1}B_{1j}+\cdot\cdot\cdot\;+A_{ip}B_{pj}$$
	for $i=1,...,m$ and $j=1,...,n$
- $C_{ij}$ is the inner product of $i$th row of $\mathbf{A}$ and $j$th column of $\mathbf{B}$
- **properties**:
	- $\mathbf{(AB)C=A(BC)}$, so both can be written as $\mathbf{ABC}$
	- $\mathbf{A(B+B)+AB+AC}$
	- $\mathbf{(AB)^{\top}=B^{\top}A^{\top}}$
	- $\mathbf{AI=A}$ and $\mathbf{IA=A}$
	- $\mathbf{AB\ne BA}$ in general
- special cases:
	- scalar-vector product (with scalar on the right!): $\mathbf{x \alpha}$
	- inner-product: $\mathbf{a^{\top}b}$
	- matrix-vector product: $\mathbf{Ax}$
	- outer product of $\mathbf{a}\in \mathbb{R}^m$ and $\mathbf{b}\in \mathbb{R}^n$ $$\mathbf{ab}^{\top}=\begin{bmatrix} 
  a_{1}b_{1} & a_{1}b_{2} & ... & a_{1}b_{n} \\ 
  a_{2}b_{1} & a_{2}b_{2} & ... & a_{2}b_{n} \\ 
  ... &  & ._{._{.}} &  \\ a_{m}b_{1} & a_{m}b_{2} & ... & a_{m}b_{n}
\end{bmatrix}$$
- block matrices can be multiplied using the same formula, e.g. $$\begin{bmatrix} 
  a & b  \\
  c & d 
\end{bmatrix} \begin{bmatrix} 
  e & f  \\
  g & h 
\end{bmatrix}=\begin{bmatrix} 
  ae+bg & af+bh  \\
  ce+dg & cf+dh 
\end{bmatrix}$$
	provided the products all make sense

##### Inner product interpretation
- with $\tilde{a}_{i}^{\top}$ the rows of $\mathbf{A,b_{j}}$ the columns of $\mathbf{B}$, we have $$\mathbf{AB}=\begin{bmatrix} 
  \tilde{a}_{1}^{\top}b_{1} & \tilde{a}_{1}^{\top}b_{2} & ... & \tilde{a}_{1}^{\top}b_{n} \\  
  \tilde{a}_{2}^{\top}b_{1} & \tilde{a}_{2}^{\top}b_{2} & ... & \tilde{a}_{2}^{\top}b_{n} \\  
  ... &  & ._{._{.}} &  \\ \tilde{a}_{m}^{\top}b_{1} & \tilde{a}_{m}^{\top}b_{2} & ... & \tilde{a}_{m}^{\top}b_{n} 
\end{bmatrix}$$
- example: the <font color="HotPink" style="font-style: italic;">Gram matrix</font> of $\mathbf{B}$ is $$\mathbf{G=B^{\top}B}=\begin{bmatrix} 
  b_{1}^{\top}b_{1} & b_{1}^{\top}b_{2} & ... & b_{1}^{\top}b_{n} \\  
  b_{2}^{\top}b_{1} & b_{2}^{\top}b_{2} & ... & b_{2}^{\top}b_{n} \\  
  ... &  & ._{._{.}} &  \\ b_{n}^{\top}b_{1} & b_{n}^{\top}b_{2} & ... & b_{n}^{\top}b_{n} 
\end{bmatrix}$$
- Gram matrix gives all inner products of columns of $\mathbf{B}$
- $\mathbf{G=B^{\top}B=I}$ means columns of $\mathbf{B}$ are orthonormal

##### Outer product interpretation
- with $\mathbf{a}_{k}$ the columns of $\mathbf{A,\;\tilde{b}^{\top}_{k}}$ the rows of $\mathbf{B}$, we have $$\mathbf{AB=\sum\limits^{p}_{k=1}a_{k}\tilde{b}^{\top}_{k}=a_{1}\tilde{b}^{\top}_{1} +\cdot\cdot\cdot\;+ a_{p}\tilde{b}^{\top}_{p}}$$
- matrix product is the sum of the $p$ outer products between <font color="crimson" style="font-weight: bold;">corresponding</font> rows and columns
- example: the <font color="HotPink" style="font-style: italic;">Gram matrix</font> of $\mathbf{A}^{\top}$ is $$\mathbf{G=AA^{\top}}\sum\limits^{p}_{k=1}a_{k}a^{\top}_{k}=a_{1}a^{\top}_{1}+\cdot\cdot\cdot\;+a_{p}a^{\top}_{p}$$
##### Column Interpretation
- denote columns of $\mathbf{B}$ by $\mathbf{b}_{i}:\;\mathbf{B=[b_{1}\;b_{2}\cdot\cdot\cdot b_{n}]}$
- then we have $$\begin{align}\mathbf{AB}&= \mathbf{A}[b_{1}\cdot\cdot\cdot b_{n}]\\&= \mathbf{[Ab_{1}\cdot\cdot\cdot Ab_{n}]} \end{align}$$
- so $\mathbf{AB}$ is 'batch' multiple of $\mathbf{A}$ times columns of $\mathbf{B}$
- given $k$ systems of linear equations, with same $m \times n$ coefficient matrix $$\mathbf{Ax_{i}=b_{i},\;\;\;}i=1,...,k$$
- write in compact matrix form $\mathbf{AX=B}$
- $\mathbf{X=[x_{1}\cdot\cdot\cdot x_{k}],\;\;B=[b_{1}\cdot\cdot\cdot b_{k}]}$

#### Matrix Powers
 - for $\mathbf{A}$ square, $\mathbf{A}^2$ means $\mathbf{AA}$ and the same for higher powers
 - with convention $\mathbf{A^{0}=I}$ we have $\mathbf{A^{k}A^{l}=A^{k+l}}$
 - negative powers soon, fractional later in the class

##### Complexity
- to compute $C_{ij}=\mathbf{[AB]}_{ij}$ is inner product of $p$-vectors
- so total required flops is $(mn)(2p)=2mnp$ flops
- multiplying two $1000\times1000$ matrices requires 2 billion flops
	- can be done in well under a second on modern computers

### Inverse Matrices
#### Left Inverses
- a number $x$ that satisfies $x\alpha = 1$ is called the inverse of $\alpha$
- inverse exists if and only if $\alpha \ne 0$ and is unique
- a matrix $\mathbf{X}$ that satisfies $\mathbf{XA=I}$ is called left inverse of $\mathbf{A}$
- if a left inverse exists, we say that $\mathbf{A}$ is left-invertible
- example: the matrix $$\mathbf{A}=\begin{bmatrix} 
  -3 & -4  \\
  4 & 6  \\ 1 & 1
\end{bmatrix}$$
	has two different left inverses: $$\mathbf{B}=\frac{1}{9}\begin{bmatrix} 
  -11 & -10 & 16 \\ 7 & 8 & -11
\end{bmatrix},\;\;\;\;\mathbf{C}=\frac{1}{2}\begin{bmatrix} 
  0 & -1 & 6 \\ 0 & 1 & -4
\end{bmatrix}$$

##### Left inverses and column independence
- if $\mathbf{A}$ has a left inverse $\mathbf{C}$ then the columns of $\mathbf{A}$ are linearly independent
- to see this: if $\mathbf{Ax}=0$ and $\mathbf{CA=I}$ then $$0= \mathbf{C}0= \mathbf{C(Ax)}= \mathbf{(CA)x}= \mathbf{Ix=x}$$
- <font color="crimson" style="font-weight: bold;">a matrix is left-invertible if and only if its columns are linearly independent</font>
- matrix generalization of: a number is invertible if it is nonzero
- so left-invertible matrices are *tall* or *square*

#### Right Inverses
- a matrix $\mathbf{X}$ that satisfies $\mathbf{AX=I}$ is a right inverse of $\mathbf{A}$
- if a right inverse exists we say that $\mathbf{A}$ is right-invertible
- $\mathbf{A}$ is right-invertible if $\mathbf{A}^{\top}$ is left-invertible $$\mathbf{AX=I\Leftrightarrow(AX)^{\top}=I\Leftrightarrow X^{\top}A^{top}=I}$$
- <font color="crimson" style="font-weight: bold;">a matrix is right invertible if its rows are linearly independent</font>
- right-invertible matrices are *wide* or *square*

#### Inverse
- if $\mathbf{A}$ has a left and right inverse, they are unique and equal (and we say that $\mathbf{A}$ is <font color="HotPink" style="font-style: italic;">invertible</font>)
- so $\mathbf{A}$ must be square
- to see this: if $\mathbf{AX=YA=I}$ $$\mathbf{X=IX=(YA)X=Y(AX)=YI=Y}$$
- denoted as $\mathbf{A}^{-1}$ $$\mathbf{AA^{-1}=A^{-1}A=I}$$
- inverse of inverse: $\mathbf{(A^{-1})^{-1}=A}$

#### Invertible Matrices
- the following are equivalent for a square matrix $\mathbf{A}$:
	- $\mathbf{A}$ is invertible
	- $\mathbf{A}$ is nonsingular
	- columns of $\mathbf{A}$ are linearly independent
	- rows of $\mathbf{A}$ are linearly independent
	- $\mathbf{A}$ has a left inverse
	- $\mathbf{A}$ has a right inverse
<font color="crimson" style="font-weight: bold;"> if any of these hold, all others do </font>

##### Examples
- $\mathbf{I^{-1}=I}$
- $\text{diag}(a_{1},...,a_{n})^{-1}=\text{diag}(1/a_{1},...,1/a_{n})$
- if $\mathbf{Q}$ is orthogonal, i.e. square with $\mathbf{Q^{\top}Q=I}$, then $\mathbf{Q^{-1}=Q^{\top}}$. Also implies $\mathbf{QQ^{\top}=I}$
- $2\times 2$ matrix $\mathbf{A}$ is invertible if and only if $A_{11}A_{22}\ne A_{12}A_{21}$ $$\mathbf{A}^{-1}=\frac{1}{A_{11}A_{22}-A_{12}A_{21}}\begin{bmatrix} 
  A_{22} & -A_{12} \\ -A_{21} & A_{11}
\end{bmatrix}$$ <font color="crimson" style="font-weight: bold;">you need to know this formula</font>

#### Properties
- $\mathbf{(AB)^{-1}=B^{-1}A^{-1}}$ (provided inverses exist)
- $\mathbf{(A^{\top})^{-1}=(A^{-1})^{\top}}$ (sometimes denoted $\mathbf{A}^{-\top}$)
- negative matrix powers: $\mathbf{(A^{-1})^{k}}$ is denoted $\mathbf{A}^{-k}$
- with $\mathbf{A^{0}=I}$, identity $\mathbf{A^{k}A^{l}=A^{k+l}}$ holds for any integers $k,l$

### Triangular Matrices
- lower triangular matrix $\mathbf{L}$ with nonzero diagonal entries is invertible
- to see this, write $\mathbf{Lx}=0$ as $$\begin{align}&L_{11}x_{1}&=0\\ &L_{21}x_{1}+L_{22}x_{2}&=0\\&&.\\&&.\\&&.\\ &L_{n1}x_{1}+L_{n2}x_{2}+\cdot\cdot\cdot\;+L_{nn}x_{n}&=0\end{align}$$
	- from first equation, $x_{1}=0$ (since $L_{11}\ne 0$)
	- second equation reduces to $L_{22}x_{2}=0$, so $x_{2}=0$ (since $L_{22}\ne 0$)
	- and so on
	this shows columns of $\mathbf{L}$ are linearly independent, so $\mathbf{L}$ is invertible
- upper triangular $\mathbf{R}$ with nonzero diagonal entries is also invertible

### Determinant
- determinant of a $2\times 2$ matrix is $$\text{det}\begin{bmatrix} 
  a & b \\ c & d
\end{bmatrix} = ad-bc$$
- we can define $3\times3$ determinants from $2\times2$ determinants $$\text{det}\begin{bmatrix} 
  A_{11} & A_{12} & A_{13}  \\ A_{21} & A_{22} & A_{23} \\ A_{31} & A_{32} & A_{33}
\end{bmatrix}=A_{11}\text{det}\begin{bmatrix}A_{22} & A_{23} \\ A_{32} & A_{33}\end{bmatrix}-A_{12}\text{det}\begin{bmatrix}A_{21} & A_{23} \\ A_{31} & A_{33}\end{bmatrix}+A_{13}\text{det}\begin{bmatrix}A_{21} & A_{22} \\ A_{31} & A_{32}\end{bmatrix}$$
- and in general $$\text{det}\mathbf{A}=\sum\limits^{n}_{j=1}(-1)^{i+j}A_{ij}\text{det}\tilde{\mathbf{A}}_{ij}$$
	where $\tilde{\mathbf{A}}_{ij}$ is obtained from deleting the $i$th row and $j$th col of $\mathbf{A}$

#### Cramer's Rule
- define <font color="HotPink" style="font-style: italic;">Cofactor</font> matrix $\mathbf{C}$ $$C_{ij}=(-1)^{i+j}\text{det}\tilde{\mathbf{A}}_{ij}$$
	then $$\mathbf{A}^{-1}=\frac{1}{\text{det}\mathbf{A}}\mathbf{C}^{\top}$$
- example: $$\begin{bmatrix}a & b \\ c & d\end{bmatrix}^{-1}=\frac{1}{ad-bc}\begin{bmatrix}d & -b \\ -c & a\end{bmatrix}$$
- almost useless in practice due to rounding error

#### Properties
- $\text{det}\mathbf{A}$ is a linear function of each row/column
- $\text{det}\mathbf{A}=0$ iff rows/columns are linearly dependent (singular)
- $\mathbf{A}$ is nonsingular/invertible if $\text{det}\mathbf{A}\ne 0$
- $\text{det}\mathbf{A}=\text{det}\mathbf{A^{\top}}$
- $\text{det}\mathbf{AB}=\text{det}\mathbf{A}\;\text{det}\mathbf{B}$ (important) $$\Rightarrow\text{det}\mathbf{A}^{-1}=1/\text{det}\mathbf{A}$$
- $\text{det}\begin{bmatrix}\mathbf{A} & \mathbf{B}  \\ \mathbf{C} & \mathbf{D}  \end{bmatrix} = \text{det}\mathbf{A}\text{det}\mathbf{(D-CA^{-1}B)}$

#### Examples
- if $\mathbf{A}$ is orthogonal, then $\text{det}\mathbf{A}\pm1$
![center](../zassets/Pasted%20image%2020240130181850.png)




