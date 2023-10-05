# Module 5: Ensemble Methods

## Bagging
- Idea:
	Performance can be improved by using a "large number" of "randomized" datasets
- *Bootstrap*:
	Random sampling with replacement

### Random Forest Bagging
Idea:
- Let each DT overfit.
	- Make all the leaves pure
	- This makes RF extremely easy to use: no hyperparameter optimization

*How many bootstrapped datasets do we need?*
- The more the better - up to computational limit
- Each DT will be independent → you can parallelize the RF

Extra randomness
- Each time we split the data, only split along d' < d randomly selected dimensions
	- $d' = \sqrt{d}$

#### Out of Bag evaluation
- Due to the replacement, a bootstrapped dataset typically has about 63% of the original dataset
- We can use the other ~37% of unselected data as test data

#### Summary of RF
- No data splitting needed
- Feature scaling not required
- No hyperparameter optimization required
- We get feature importance "for free"
- Easy to parallelize
*All this makes RF very easy to use.*


## Boosting
Idea:
- Sequentially improve a poor estimator to make a more powerful estimator by correcting errors

### AdaBoost (Adaptive Boost)
- Pay more attention to underfitted training data points by adjusting "weights"
- Can optimize learning rate, varies how quickly your decision boundary evolves



