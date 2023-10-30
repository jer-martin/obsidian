
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

```