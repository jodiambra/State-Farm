# State-Farm


## [Interactive Notebook](https://jodiambra.github.io/State-Farm/)

![Alt text](images/compare_models.png)

A Few classification models were tuned with a pipeline to compare AUC ROC scores. The XG boost model performed the best, while SVM performed the worst. Ultimately, XG boost was compared to the logistic regression model

![Alt text](images/confusion_matrix.png)

The XG boost model confusion matrix with the validation set shows better performance, with more true positive and true negative values. Neither model performed well in predicting the positive class, as imbalance was seen in the target. 


*************************

## Executive Summary 

The linear model is simple and easy to to interpret, however, it assumes a linear relationship between the features and the target. XG boost is a more powerful model that can handle non-linear data, categorical values, and datasets with many features. However, XG boost requires hyperparameter tuning to prevent overfitting, and is often more complex to implement. When it comes to picking between the two models, our main determinant is model performance. If our decision was not based on performance, but on interpretability, we would chose linear regression and show the top coefficients. Based on model performance on the validation set, I expect XG boost to perform better on the test set. In addition, the models in the pipeline that did not assume linearity performed better.  

As the AUC of a model is more often lower on the test set than on the validation set, we assume the XG boost model will perform slightly better on the test set, as it has a slightly higher AUC on the validation set. In addition, the XG boost made more correct predictions in the positive and negative classes, as evident by the confusion matrix of the validation set. We estimate the AUC score of the logistic regression model to be between 0.65-0.8, while the AUC of the xg boost model may be between 0.7-0.85. 

If we cannot use a scoring metric to compare the two models, we can compare the predictions of the two models on the test set. We can compare the true positive and true negative values of both models, as the model with more correct predictions will perform better. We can also compare the false positive and false negative values of both models. 