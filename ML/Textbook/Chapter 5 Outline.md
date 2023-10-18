## Support Vector Machines

- SVMs are powerful and versatile
	- Linear or nonlinear
	- Regression
	- Outlier detection
- Best suited for small to medium sized datasets
- **RELIES ON DISTANCE - USES FEATURE SCALING**
### Linear SVM Classification
- A linear SVM classifier wants to fit the "largest street" possible between the two datasets
![](Pasted%20image%2020231018170812.png)
- It does this by maximizing the margin between the fit line and the edges of the datasets
- Fully dependent on only the datapoints edge of the "street"
	- These are the *support vectors* (circled on figure above)

- The goal is to maximize the size of the street and limit *margin violations*
	- A *margin violation* is a datapoint that is in the middle or wrong side of the street

![](Pasted%20image%2020231018171137.png)

### Nonlinear SVM Classification
- Linear SVMs tend to work surprisingly well in a lot of cases
- However, many datasets *cannot be separated linearly*
	- One approach to this problem is to add polynomial features
		*The example below shows what happens if you take X1 and add a second feature X2 = X1^2*
![](Pasted%20image%2020231018171626.png)

- This can sometimes lead to a linearly separable dataset
#### Kernel Trick
- The kernel trick takes a certain number of parameters and uses a Gaussian mapping to raise the degree of the dataset

$$\phi(x)=\phi\left( \begin{array}{c} x_1 \\ x_2 \end{array} \right) = \left( \begin{array}{c} x_{1}^{2} \\ \sqrt{2}x_{1}x_{2} \\ x_{2}^{2}\end{array} \right)$$

- Notice how now that mapping $\phi$ is applied, the parameters are in 3 dimensions

![](Pasted%20image%2020231018172858.png)

- In machine learning, a *kernel* is a function capable of producing the dot product $\phi(a)^{T} \phi(b)$ based only on the original vectors $a$ and $b$
	- It shouldn't have to compute (or even know about) transformation $\phi$

- Here are some common kernels:
	- Linear: $K(a,b) = a^{T}b$
	- Polynomial: $K(a,b) = (\gamma a^{T}b+r)^{d}$
	- Gaussian RBF: $K(a,b)=\exp(-\gamma||a-b||^{2})$
	- Sigmoid: $K(a,b)=\tanh(\gamma a^{T}b+r)$

#### Polynomial Kernel
- At a low polynomial degree, this kernel can't deal with complex datasets
- At high degree, there is a huge number of features → becomes slow
	- This is why we use the kernel trick

- If your model is overfitting, reduce degree
	- Underfitting, increase

#### Similarity Features
- Another technique is to add a feature computed using a *similarity function*
	- *Similarity functions* measure how much each instance resembles a particular *landmark*
*How to select landmarks?*
- Simplest approach is to create a landmark at each instance in the dataset
	- This creates many dimensions, increasing chances that the new set will be linearly separable
	- The downside is that a training set with $m$ instances and $n$ features gets transformed into a training set with $m$ instances and $m$ features → large training set = large feature set

#### Gaussian RBF Kernel
![](Pasted%20image%2020231018174912.png)
- The plots show models trained with different values of hyperparameters gamma ($\gamma$) and C
- Increasing $\gamma$ makes the bell shaped curve narrower
	- As a result, each instance's range of influence is smaller
	- Decision boundary is more irregular
- Decreasing $\gamma$ makes the bell curve wider
	- Instances have a larger range of influence
	- Decision boundary is smoother
- Therefore, $\gamma$ is a regulation parameter
	- If model is overfitting, reduce. If underfitting, increase
		- Similar to the C hyperparameter

![](Pasted%20image%2020231018175133.png)

### SVM Regression
- As mentioned earlier, the SVM algorithm is versatile: not only does it support linear and nonlinear classification, but it also supports linear and nonlinear regression
- This is the exact opposite of classification
	- The XVM tries to fit as many instances as possible *on the street* while limiting margin violations (*off the street*)
- To do this, use SVR instead of SVC

