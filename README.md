# State-Farm


## [Interactive Notebook](https://jodiambra.github.io/State-Farm/)

## Purpose

The purpose of this project is to demonstrate data science techniques on datasets provided by State Farm insurance company. The first step is to load and clean the data, as well as conduct exploratory data analysis to understand the data. Following EDA, a few classification models will be built and compared. A logistic regression and another model will be chosen as the final models. We will then compare and contrast the different models based on respective strengths and weaknesses. Finally, predictions will be made on the test data, in the form of class probabilities for belonging to the positive class. 



![Alt text](images/compare_models.png)

A Few classification models were tuned with a pipeline to compare AUC ROC scores. The XG boost model performed the best, while SVM performed the worst. Ultimately, XG boost was compared to the logistic regression model

![Alt text](images/confusion_matrix.png)

The XG boost model confusion matrix with the validation set shows better performance, with more true positive and true negative values. Neither model performed well in predicting the positive class, as imbalance was seen in the target. 


*************************

## Executive Summary 

One of the main issues with the dataset was the amount of missing values. Deleting missing values leads to a loss of valuable information, and model performance would suffer, unless the proportion of missing data is minimal. Imputing these missing values could recover some of the missing information, which can result in a better model. However, the reason why the data is missing, as well as the imputation method implemented, can have a significant impact on the model performance. 

The datasets were cleaned and preprocessed with ordinal encoding, standard scaling, simple imputing, and SMOTE. Ordinal encoding allowed us to convert categorical features into numerical labels, to then train our models. Standard scaling was implemented to improve the performance of the models, as features with much higher scales will be given greater weights, merely because they have larger values. By scaling features to the same level, we ensure the model interprets the weights of each feature equally. Simple imputer was used to fill in the missing values, while SMOTE was used to balance the minority class. 

Several models were trained, and two were selected: logistic regression and random forest. Logistic regression serves as a baseline model for the more complex random forest. The logistic model is simple and easy to to interpret, however, it assumes a linear relationship between the features and the target. Random forest is a more powerful model that can handle a large number of inputs, without suffering from overfitting, and the model is also less prone to overfitting with outliers and noisy data. However, random forest can still overfit noisy data, when datasets contain a large number of irrelevant features. Furthermore, random forest models are difficult to interpret, as they are comprised of several decision trees.

When it comes to selecting between the two models, our main determinant was model performance. If our decision was not based on performance, but on interpretability, we would choose logistic regression. However, Based on model performance on the validation set, I expect random forest to perform better on the test set. In addition, the models in the pipeline that did not assume linearity performed better.  

AUC, or area under the curve, calculates the true positive rate against the false positive rate, where 1 represents a perfect model, and 0 is the worst model. As the AUC of a model is more often lower on the test set than on the validation set, we assume the random forest model will perform significantly better than logistic regression on the test set, as it has a high AUC on the validation set. In addition, the random forest made more correct predictions in both the positive and negative classes, as evident by the confusion matrix of the validation set. We estimate the AUC score of the logistic regression model to be between 0.60-0.80, while the AUC of the random forest model may be between 0.9-1.0. AUC was the appropriate metric to evaluate our models, as accuracy is not suitable for data with imbalanced classes. This was further illustrated by the dummy model. We found using SMOTE significantly increased our model performance among non-linear models, as SMOTE balanced the minority class in the data. 

If we could not use a scoring metric to compare the two models, we can compare the predictions of the two models on the test set. We can compare the true positive and true negative values of both models, as the model with more correct predictions will perform better. We can also compare the false positive and false negative values of both models. 

Overall, the appropriate model and scoring to implement depends on the the data and the business needs. Many factors can determine the appropriate machine learning algorithm to use, from limited resources and large datasets, to categorical values and model interpretability. 