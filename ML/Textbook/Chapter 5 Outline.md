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


