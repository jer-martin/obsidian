
- This is how you collect multiple columns and combine them into one dataframe
	1. Collect deep field CFHTLS data only by choosing the objects with `cfhtls_source` = 0.
	2. Collect deep source subaru data only by choosing the objects with `subaru_source` = 0.
	3. Collect objects with redshift quality code `zquality` >= 3.
	4. Collect objects with `u_apercor` < 99.
	5. Collect objects with `y_apercor` < 99.
```
final_df = df[(df['cfhtls_source'] == 0) & 
              (df['subaru_source'] == 0) & 
              (df['zquality'] >= 3) & 
              (df['u_apercor'] < 99) & 
              (df['y_apercor'] < 99)]
```

- This is how you use k-fold CV
```
kf = KFold(n_splits=5, shuffle=True, random_state=42)

cv_scores = cross_val_score(rf, X_train, y_train, cv=kf, n_jobs=-1, scoring='neg_mean_squared_error')

# convert negative MSE to RMSE
rmse_scores = np.sqrt(-cv_scores)

print(f'5-Fold RMSE Scores: {rmse_scores}')
print(f'Average 5-Fold RMSE Score: {np.mean(rmse_scores)}')
```

- out of bag score
```
rf.fit(X_train, y_train)

oob_score = rf.oob_score_
```

- how to optimize hyperparams
	- make a param grid
```
param_grid = { 'max_features': [None, 'sqrt', 2], 'n_estimators': [50, 100, 150] }
```
- use gridsearch
```
# Create the GridSearchCV object 
grid_search = GridSearchCV(RandomForestRegressor(random_state=42, oob_score=True), param_grid, cv=5) 
# Fit to the training data 
grid_search.fit(X_train, y_train) 
# Get the best parameters and best score 
best_params = grid_search.best_params_ 
best_score = grid_search.best_score_ 
print(f"Best Parameters: {best_params}") 
print(f"Best Score: {best_score}") 
# Create and fit the best model 
best_rf = RandomForestRegressor(max_features=best_params['max_features'], n_estimators=best_params['n_estimators'], random_state=42, oob_score=True)
```
