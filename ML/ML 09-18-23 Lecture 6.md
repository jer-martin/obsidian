### Recap: Decision Trees
- Very similar to kNN in philosophy
	- similar inputs have similar outputs
- Can we make kNN more efficient?
	- Can we reduce tree depth?
	- Do we need to prune?
	- Do we always need to reduce distance?

- *How is DT different from KD tree?*
	- We split nodes along the "optimal" dimension
	- We don't have to split a node into exactly half
	- We don't need to compute the distance
	- We don't need to split "pure" nodes
	- We don't prune nodes

### Hyperparameter Optimization

*Let's think about a hypothetical situation in which we built a model, but the test result is not satisfactory. What do we do?*

- Obtain more training data
- Improve quality of data set
- Try smaller set of features (remember the Curse of Dimensionality)
- Try including additional features (if existing features do not represent classification well)
- Try a different ML algorithm
- *Hyperparameter optimization*

### The Philosophy Behind Splitting Data
- One of the goals of AI/ML is to make accurate predictions for data sets that are *previously unseen*
- We split data into training and test sets to examine how well the model *generalizes* to new, previously unseen data
- ##### Potential issue with single split
	- We can be lucky/unlucky depending on how data sets are split

#### Cross Validation
- The purpose of cross validation is to asses the generalization performance more accurately
- Standard k-fold CV
- 
![center](../zassets/Pasted%20image%2020230919105357.png)