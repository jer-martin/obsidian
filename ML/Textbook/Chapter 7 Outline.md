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


