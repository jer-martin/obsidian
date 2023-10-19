## Ensemble Learning and Random Forests
- The main idea is: if you aggregate the predictions of a group of predictors, you will often get better predictions than the best individual predictor
- a group of predictors is called an *ensemble*

### Bagging and Pasting
- One way to get a diverse set of classifiers is to use completely different training algorithms
- Another way is to use the same classifier, but trained on different random subsets of the training set
	- When sampling is performed *with replacement*, that's called Bagging
	- *without* replacement is called Pasting
- In other words, both bagging and pasting allow training instances to be sampled several times across multiple predictors, but only bagging allows training instances to be sampled several times for the same predictor

- The aggregation function is typically the statistical mode (the most chosen prediction) for classification
- For regression we usually take the average


### Random Forests
- A Random Forest is just an ensemble of D-Trees, trained by bagging with max_samples set to the size of the training set
- With a few exceptions, a RandomForestClassifier has all the hyperparameters of a DecisionTreeClassifier (to control how trees are grown), plus all the hyperparameters of a BaggingClassifier to control the ensemble itself

### Boosting
- Boosting refers to any ensemble method that can combine several weak learners into a strong learner
- The idea of most boosting methods is to train predictors sequentially, each trying to correct it's predecessor
- There are many methods available, but by far the most popular are *AdaBoost* and *Gradient Boosting*

#### AdaBoost
- One way for a new predictor to correct its predecessor is to pay a bit more attention to the training instances that the predecessor underfitted
- For example:
	- The algorithm first trains a base classifier and uses it to make predictions
	- It then increases the relative weight of misclassified training instances
	- Makes a second classifier using the updated weights
	- et cetera
- AdaBoost is conceptually similar to Gradient Descent, but rather than tweaking a single predictor's parameters, AdaBoost continually adds more predictors, thereby making it better gradually
- *ADABOOST CANNOT BE PARALLELIZED SINCE EACH PREDICTOR CAN ONLY BE TRAINED AFTER THE PREVIOUS PREDICTOR IS EVALUATED*

#### Gradient Boosting
- Same as AdaBoost, GradBoosting sequentially adds correcting predictors to the ensemble
- Rather than tweaking instance weights, this method tries to fit the new predictor to the *residual errors* of the last predictor

![](Pasted%20image%2020231019091007.png)

