# Performing Feature Selection in Python

Question: Why do we do feature selection? 
Answer: In order to have the most predictive model we can for the least computational cost. 

How we do this is by eliminating independent variables that are nonpredictive or only marginally so. This reduces the chance of overfitting to the features, increases accuracy and shortens time to convergence. 

This notebook is a walk through several of the examples in the scikit learn site(https://scikit-learn.org/stable/modules/feature_selection.html#univariate-feature-selection), back-to-back. I not only show you how to find out the most predictive features, I show you how to display them to the screen and put these top features into a new dataframe so that you can use that dataframe as input to a downstream process (something often frustratingly not shown my others). 

The Feature Selection Techniques covered are: 
* SelectKBest
* Recursive Feature Elimination (RFE)
* RFE with Cross Validation (a favorite of mine as my students know)
* SelectFromModel
    * Lasso
    * RandomForestClassifier
* Extra Tree Classification

The biggest problem with scikit's implementation of univariate feature selection algorithms is that they return numpy arrays when you call them making it very hard for a non-Python aficionado to reassociate that with the sores of the features in the model without doing some fairly unintuitive hijinks. And this is exactly what a data scientist wants to know--which features scored highest. They don't just want the model, they want to understand the model, interact with data providers to help them reine their instruments, display the best (and possible worst) variables and visualize them *in context*. It's not enough to see it on the raw data--it is needed on the scores as well.

Caveat: I do the conversion to a new dataframe for each method. I could have done it as a a #def--but this would mean that each of the methods wouldn't stand alone. If someone wants to take a stab at it, great. On the one hand, that means you can just use each section as a "complete" notebook. I often do this because it is easier in the classroom to show everything associated with the process inline. Also, it is unlikely you'd use more than one of these (though you can). There are also some slight variations due to different attributes that are available for each feature selection method. The only downside is that this notebook is much longer than most of the ones I publish.

NOTE: these are being used for classification and the dataset is the extended Wisconsin Breast Cancer dataset: https://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data. 
