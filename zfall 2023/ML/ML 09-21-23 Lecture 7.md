### Hyperparameter Optimization

- Specify CPU usage by using the 

		n_jobs = x

	- Where X is the number of CPUs you want to use. Put -1 for maximum amount.

### Evaluation Metrics
- *So far, we have been using accuracy for classification performance. Is this sufficient?*

![center](../zassets/Pasted%20image%2020230921104549.png)

<div style="text-align: center; width: 100%;">Confusion Matrix</div>

#### Accuracy
- $(TP + TN)/(TP+TN+FP+FN)$
- Maximize the total number of correct predictions

#### Precision
- $TP/(TP+FP)$
- minimize number of false positives (e.g. clinical trial for new drug)

#### Recall (completeness)
- $TP / (TP+FN)$
- minimize number of false negatives (e.g. cancer diagnosis)

#### F-Score
- There is a trade off between optimizing precision and optimizing recall
- $F1 = \frac{\text{precision}*\text{recall}}{\text{precision}+\text{recall}}$ 

## Support Vector Machines: The Idea
- Let's construct a hyperplane that can separate two classes
- If a dataset is linearly separable, you can find an infinite number of separating hyperplanes.
	- What is the optimal plane?
		- The optimal hyperplane is the one that maximizes "margin" between support vectors

#### How does SVM maximize the margin?
- Select two parallel planes which separate the data with no points between them
- Maximize their difference
- The average line will be the decision boundary