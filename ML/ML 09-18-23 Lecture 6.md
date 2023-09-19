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
- Standard $k$-fold CV (in figure, $k = 4$)

![center](../zassets/Pasted%20image%2020230919105357.png)

	iris = load_iris()
	model = DecidionTreeClassifier(max_depth=4, random_state=0)
	scores = cross_val_score(model, iris.data, iris.target)
	print("Cross-validation scores: {}").format(scores))
	print("Mean cross-validation scores: {}").format(scores.mean())

	Cross-validation scores: {0.967, 0.967, 0.9, 1, 1}
	Mean cross-validation scores: 0.96666666668

#### Variations on Cross Validation
- Stratified $k$-fold (useful for classification problems; sklearns' default)
	- This makes it so that there is both testing and training data in each Class, leading to better generalization

![center](../zassets/Pasted%20image%2020230919105803.png)

### Grid Search

	max_depth = np.arange(10) + 1
	best_score = 0

	for i in max_depth:
		model = DecisionTreeClassifier(max_depth=1, random_state=0)
		score = cross_val_score(model, X_train, Y_train)
		score = np.mean(score)
		if score > best_score
			best_score = score
			best_parameters = {'max_depth': 1}

	print("Best score: {:.2f}".format(best_score))
	print("Best parameters: {}".format(best_parameters))

	Best score: 0.95
	Best parameters: {'max_depth' : 2}


*People have already wrote these functions.*

This is why we are using sklearn.



