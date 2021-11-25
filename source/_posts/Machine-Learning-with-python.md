---
title: Machine Learning with Python
date: 2021-11-10
updated: 2021-12-15
tags: [Coursera, Python, Machine Learning]
group: todo
categories: 人工智能与大数据
---

> This course provided by IBM dives into the basics of machine learning using an approachable, and well-known programming language, Python. In this course, I've learned about the purpose of Machine Learning and where it applies to the real world and had a general overview of Machine Learning topics such as supervised vs unsupervised learning, model evaluation, and Machine Learning algorithms. The following are the notes I took during this course.

<!--more-->

{% pdf /pdf/ml-with-py.pdf %}

### Introduction to Machine Learning

#### What is machine learning

- Machine learning is the subfield of computer science that gives "computers the ability to learn without being explicitly programmed."
- Major machine learning techniques
  - Regression/Estimation: Predicting continuous values
  - Classification: Predicting the item class/category of a case
  - Clustering: Finding the structure of data, summarization
  - Associations: Associating frequent co-occurring items/events
  - Anomaly detection: Discovering abnormal and unusual cases
  - Sequence mining: Predicting next events, click-stream (Markov Model, HMM)
  - Dimension Reduction: Reducing the size of data (PCA)
  - Recommendation systems: Recommending items
- Difference between artificial intelligence, machine learning and deep learning
  - AI components: Computer Vision, Language Processing, Creativity, etc
  - Machine learning: Classification, Clustering, Neural Network, etc
  - Revolution in ML: Deep learning

#### Python libraries for machine learning

- NumPy, SciPy, Matplotlib, pandas, Scikit Learn
- Scikit Learn: Classification, Regression and Clustering algorithms, Works with NumPy and SciPy, Easy to implement
```python
from sklearn import preprocessing
x = preprocessing.StandardScaler().fit(X).transform(X)

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33)

from sklearn import svm
clf = svm.SVC(gamma=0.001, C=100.)
clf.fit(X_train, y_train)
clf.predict(X_test)

from sklearn.metrics import confusion_matrix
print(confusion_matrix(y_test, yhat, labels=[1,0]))

import pickle
s = pickle.dump(clf)
```

#### Supervised vs Unsupervised learning

- Supervised learning: Teach the model with labeled data, then with that knowledge, it can predict unknown or future instances
- Types of supervised learning: Classification and Regression
  - Classification is the process of predicting discrete class labels or categories (Classifies labeled data)
  - Regression is the process of predicting continuous values (Predicts trends using previous labeled data)
- Unsupervised learning: The model works on its own to discover information
- Unsupervised learning techniques: Dimension reduction, Density estimation, Market basket analysis, Clustering
- Clustering is grouping of data points or objects that are somehow similar by Discovering structure, Summarization and Anomaly detection (Finds patterns and groupings from unlabeled data)
- Supervised Learning has more evaluation methods than unsupervised learning, whereas unsupervised learning is a less controlled environment

### Linear Regression

#### Regression

- Regression is the process of predicting a continuous value
- Two types of regression model: Simple Regression and Multiple Regression
- Applications of regression: Sales forecasting, Satisfaction analysis, Price estimation, Employment income, etc.
- Regression algorithms
  - Ordinal regression
  - Poisson regression
  - Fast forest quantile regression
  - Linear, Polynomial, Lasso, Stepwise, Ridge regression
  - Bayesian linear regression
  - Neural network regression
  - Decision forest regression
  - Boosted decision tree regression
  - KNN (K-nearest neighbors)

#### Simple Linear Regression