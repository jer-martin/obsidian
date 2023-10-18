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
	
