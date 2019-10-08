1. List, explain, and identify the different types of data attributes (nominal, ordinal, interval, ratio).

Nominal: ==, !=
Ordinal: ==, !=, <, >, <=, >=
Interval: ==, !=, <, >, <=, >=, +, -
Ratio: ==, !=, <, >, <=, >=, +, -, *, /

2. Explain the difference between supervised and unsupervised learning.

Supervised: feature X with Label Y to predict(Regression, Classification).
Unsupervised: feature X to learn itself to describe(Density estimation, Clustering, Dimensionality reduction).

3. Explain the nature and significance of noise and outliers in data analysis.

Noise refers to modification of original values.
Outliers are data objects with characteristics that are considerably different than most of the other data objects in the data set.

4. List, explain, compare, and evaluate methods for handling missing data values.

Eliminate Data Objects: straightforward to implement, but signicantly limits the scope and power of study, and introduces bias when data is not missing at random.
Estimate Missing Values: Comparing to complete-case analysis, it can utilize all present data for analysis. However, some data imputation methods are only suitable when missing rate is low, e.g. mean- or median-lling and knn.
Ignore the Missing Value During Analysis.
Replace with all possible values(weighted by probabilities)

5. Explain the notion of sampling, and list and explain potential problems arising in
sampling data sets;

Sampling is the use of a subset of the population to represent the whole population.
Two key principles for effective sampling:
- using a sample will work almost as well as using the entire data sets, if the sample is representative.
- A sample is representative if it has approximately the same property as the original set of data.

6. Explain and understand how Principle Component Analysis(PCA) works and can be applied to do feature reduction;

When applying PCA, the resulted principle components are always orthogonal(perpendicular) to one another.

7. List, explain, and compare different methods for converting continuous attributes into discrete attributes.

Discretization
Attributes Transformation

8. Explain and compute the mean, median, modes, and Z-scores of sets of data values.

Frequency(频率或频数): 
Mean(平均数): very sensitive to outliers
Median(中位数): Summary of frequency distribution
Modes(众数):
Z-scores: the standard score is the signed fractional number of standard deviations by which the value of an observation or data point is above the mean value of what is being observed or measured.
Z-scores: (oneData - mean) / standardDeviation

9. Explain the notion of probability distribution and compute simple distributions from data frequencies.

10. Explain the notion of conditional probability and compute conditional probabilities from probability distributions.

11. Explain the notion of correlation of data attributes.

Correlation measures the linear relationship between objects.
Variance – measure of the deviation from the mean for points in one dimension.
Covariance – a measure of how much each of the dimensions varies from the mean with respect to each other.
$$Correlation(X, Y) = \frac{Covariance(X, Y)}{Variance(X)Variance(Y)}$$

12. Explain and give examples of the notion of decision trees.

Given a collection of records (training set ): Each
record contains a set of attributes, one of the
attributes is the class. (Categorical, discrete,
unordered)
Find a model for class attribute as a function of the
values of other attributes.
Goal: previously unseen records (test set) should be
assigned a class as accurately as possible.

13. Construct decision trees from small data sets by using entropy and information gain.

14. Compare alternative splitting attributes in decision tree construction by applying gini or entropy measures.

15. Explain the problems caused by underfitting and overfitting data, and by inexpressive representations.

Underfitting: when model is too simple, both training and test errors are large.
Overfitting: when model is complex where training error is small but test error is large.

16. Understand and explain: generalization error, optimistic error, pessimistic error; postpruning based on optimistic error, pessimistic error.

Generalization error: Generalization error is the true error for the population of examples we would like to optimize.
Optimistic error:
Pessimistic:

17. How to build decision trees with missing values and apply the decision tree to test data with missing values.

18. Chi-square Tests
$$X^2 = \sum{\frac{O_i - E_i}{E_i}}$$
O is pratical value.
E is theoretical value.

19. Explain the procedure of Hold-out, Stratified Sampling, Cross-Validation, and LOOCV.

Holdout: 2/3 for training and 1/3 for testing.
Stratified Sampling: sample in such a way that each class is represented in both sets.
Cross-Validation
LOOCV

20. Contrast and explain the notions of error rate and confusion matrices in classification.

21. Use confusion and cost matrices to compute which of two classifiers is better for a data set.

22. Explain the notion of Accuracy, Error Rate, Precision, Recall, F-measure.

$$Accuracy = \frac{TP+TN}{TP+FP+TN+FN}$$
$$Error Rate = 1 - Accuracy$$
$$Precision(p) = \frac{TP}{TP+FP}$$
$$Recall(r) = \frac{TP}{TP+FN}$$
$$F-Measure(F) = \frac{2rp}{r+p} = \frac{2TP}{2TP+FP+FN}$$

The Accuracy (or error rate=1-Accuracy) is an inadequate measure of the performance of an algorithm, it doesn’t take into account the cost of making wrong decisions.

23. Explain the notion of an ROC curve, AUC, and its meaning for classifier performance.

24. Use ROC curves to compare performance of different classifiers.

25. Understanding the procedure of Bagging and Boosting, especially the Adaboost.

26. Explain and understand how the bagging and AdaBoost works.

27. Explain how the K-nearest Neighbour classifier works.

28. Explain the notion of probabilistic or Bayesian methods.
29. State and explain Bayes theorem and its use in updating probability distributions to
incorporate new evidence, and use it to compute probabilities.
30. Diagram and explain the Naive Bayesian classification method.
31. Compute probabilities in small data sets and use these values in a naive Bayesian
classifier to classify data items.