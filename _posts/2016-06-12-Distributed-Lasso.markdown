---
layout: post
section-type: post
title: Distributed Lasso
post-preview: Studied distributed algorithms to solve L1-regularized linear regression (Lasso) and implemented a distributed version of Least Angle Regression (LARS) in Spark, which provides exact solution (hence guarantees sparsity in the coefficients) while computing the whole coefficient path.
---
I worked on this project with [Sebastien Levy](https://fr.linkedin.com/in/sebastien-levy-59826aa0) 
for a [Distributed Algorithms and Optimization](https://stanford.edu/~rezab/dao/) course at Stanford.

The Lasso is a simple linear model used to tackle a wide range of machine learning problems. By adding 
a L1 penalization to the ordinary least squares, it induces sparsity in the coefficients, making the algorithm 
very efficient even when the number of features is bigger than the number of observations. Another interesting 
characteristic of the Lasso is its piece-wise linear coefficient path, which can be leveraged for efficient 
computations. Although simple gradient methods can be applied to solve the underlying convex minimization problem, 
there exists a couple of exact methods which are as efficient, if not faster. Such methods are usually preferred 
in sequential frameworks to guarantee sparsity and compute the whole coefficient path. Unfortunately, the Lasso implementation
in Spark MLlib is based on Stochastic Gradient Descent.

So we designed and studied the complexity of distributed algorithms to solve the Lasso based on Least Angle Regression (LARS). 
Our algorithm guarantees the sparsity of the solution, can handle all types of distributed matrices, 
and computes the whole coefficient path.
We found that the complexity of the proposed algorithm was promising, since the communication cost is comparable 
to gradient methods, while providing a useful parallelization of the sequential version 
(similar amount of total work, logarithmic depth in the large dimension).
We also implemented a prototype in Spark.

Our project report contains all the details and can be found **[here](http://bit.do/dlars)**!