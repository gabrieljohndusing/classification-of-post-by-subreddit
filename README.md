## Summary


### Data Source

Data was sourced from the subreddits `r/TwoSentenceHorror` and `r/TwoSentenceComedy` using the `redshift` api.

### Questions

- Is there a model that can accurately predicts whether a two sentence post is from the `r/TwoSentenceHorror` subreddit?
- Can the hyperparameters of a model be used to improve the accuracy of this model?

### Results

The baseline accuracy was 66% of the majority class (text from `r/TwoSentenceHorror`). The un-tuned models yield the following accuracy scores and Matthews Correlation Coefficient. As we can see, all models (except the svm classifier with count vectorizer) outperform the baseline accuracy.

In addition to the accuracy score, the matthews' correlation coefficient was used to score model performance. This metric is essentially tracking the correlation between the predicted and actual values. This is a value that falls between -1 and 1. A value of 0 means that the prediction is no better than a completely random prediction.

|vectorizer | model | accuracy score | matthews correlation coefficient (mcc) |
| :---: | :---: | :---: | :---: |
|count vectorizer | logistic regression | 70% | 26% |
| | knn classifier | 70% | 25% |
| | random forest classifier | 71% | 32% |
| | adaboost | 72% | 33% |
| | svm classifier | 34% | 5% |
| | multinomial naive bayes | 68% | 21% |
| tfidf | logistic regression | 76% | 43% |
| | knn classifier | 72% | 31% |
| | random forest classifier | 73% | 35% |
| | adaboost | 72% | 38% |
| | svm classifier | 77% | 46% |
| | multinomial naive bayes | 68% | 20% |

The models that were chosen for tuning were logistic regression and logistic regression, both with tfidf vectorizer. The results of the tuning was:

| model | accuracy score | matthews correlation coefficient |
| :---: | :---: | :---: |
| logistic regression | 77% | 46% |
| svm classifier | 76% | 44% |

While the logistic regression accuracy and mcc scores improved with tuning, both scores actually dropped for svm post tuning.

### Conclusions

- Hyperparameter tuning doesn't always yield the best results.
- When tuned properly, even 'basic' models can perform better than more elaborate models.