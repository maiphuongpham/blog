---
title: "Machine Learning"
date: 2023-03-17T15:54:07-08:00
draft: true
math: true
---

# Supervised Machine Learning algorithms

## Penalized Regression

(Dimention Reduction)

$$\min \sum_{i=1}^{n} \epsilon_{i}^{2} + \lambda \sum_{i=1}^{k} |\hat{b_{k}}|$$

where $|\hat{b_{k}}|$ is the number of included features.

## Support Vector Machine

(Classification, Regression and Outlier Detection)

Maximize the probability of making a correct prediction by determining the (linear) boundary that is furthest from all observations.

Trade-off between a wider margin and a lower total error penalty.

## K-nearest Neighbour

(Classification (sometimes regression))

Classify new observations by finding similarities in the existing data.

Sensitive to irrelevant and correlated features.

## Classification and Regression Trees (CART)

## Ensemble Learning and Random Forests

# Unsupervised Machine Learning Algorithms

## Principal Components Analysis

(Dimention Reduction)

## Clustering

### K-mean clustering

### Hieracrchical clustering

# Deep Learning
## Neural Networks

(Classification, Regression supervised learning)

## Deep Learning Nets

Neural networks with many hidden layers (at least 3, typically >20)

(image, pattern, speech recognition)

## Reinforcement Learning

(unsupervised)

# Big Data
## Characteristics:

1. Volume
2. Variety
3. Velocity
4. Veracity

## Stages in Big Data project:

1. Conceptualize the task / Text problem formulation
2. Data Collection / Curation
3. Data Preparation / Preprocessing / Text wrangling

### Structured data
3.1. Data Cleansing
incomplete (missing entries), invalid (out of meaningful range), inaccurate (not true), inconsistent (conflicts with other data), non-uniform (different formatting), duplication
3.2. Data Processing
- Transformations: extraction (e.g. DOB to Age), aggregation (e.g. street address + city = GPS co-ordinates), filtration (e.g. only L2 CFA candidates), selection (e.g. eliminate extra columns), conversion (e.g. categorical into (0,1) values)
- Outliers: delete (trimming), winsorization (replace with min/max values)
- Scaling: normalization ($\frac{\x_{i} - x_{\min}}{x_{\max} - x_{\min}}$ rescales to (0,1) sensitive to outliers), standardization ($\frac{\x_{i} - \mu}{\sigma}$ centers and rescales for normal distribution),studentization ($\frac{x_{i} - \bar{x}}{s/\sqrt{n}}$)

### Unstructured data

Cleasing: remove html, punctuation (some), numbers, white spaces, tokenization (unigram / biogram / n-grams)

Normalize: lowercasing, remove stop words, stemming / lemmatization

result: 
bag of words, 'document term' matrix (encoded - structured)

4. Data Exploration
4.1. Data Exploratory Analysis (visualize)
4.2.Feature Selection
remove redundant features, statistical tests to determine relevancy, dimension reduction (PCA)

- remove most and least frequent:
$$TF: \frac{\# \text{obs}}{Total}$$

$$DF = \frac{# \text{docs}}{Total}$$

$$IDF: \ln \left( \frac{1}{DF}\right)$$
$$TF - IDF = TF \times IDF$$
- Chi-square test: identify tokens in classes.
- mutual information (MI): 0 - token's distribution is the same in all classes, 1 - token only occurs in one class

4.3.Feature Engineering
creating new feature, decompose into multiple features (e.g. numbers, n-grams, name entity recognition, parts of speech classification)

5. Model Training / Classifier output
5.1.Method Selection
depends on type of problem, size of data

5.2.Performance Evaluation
precision: $P = \frac{TP}{TP + FP}$
recall: $R = \frac{TP}{TP + FN}$
accuracy: $Acc = \frac{TP + TN}{TP + FP + TN + FN}$
$F1 = \frac{2\times P \times R}{P + R}$

receiver operating characteristic (ROC) - convex curve
False Positive Rate $FPR = \frac{FP}{TN + FP}$
True Positive Rate $TPR = \frac{TP}{TP + FN}$ (Recall)

Root mean squared error (RMSE)
$$RMSE = \sqrt{\sum_{i=1}^{n} \frac{(\hat{y_{i}} - y_{i})^2}{n}}$$

5.3.Tuning

minimize bias error + variance error (MSE) 