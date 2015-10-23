---
layout: post
section-type: post
title: Deep Mining
---
I was a visiting student at MIT and worked on a project that we called **Deep Mining**. The goal was to automatically find the best hyper-parameters for Machine Learning pipelines, so in other words, to **mine pipelines**, and that's where the name comes from. While working on this project, I mainly focused on Bayesian optimization methods and on Gaussian Process-based regression. In particular, I developed a new algorithm called **non-parametric Gaussian Copula Process** to better model the performances of a pipeline given its hyper-parameters. *See more details below.*

Here is a pipeline example for the [handwritten digit recognition problem](http://yann.lecun.com/exdb/mnist/) :
<center><img src="https://sds-dubois.github.io/img/projects/DeepMining_workflow2.png"></img></center>   
we can see that there are some hyper-parameters to tune, and every data scientist knows it's usually a painful task. The software I designed handle this by **testing iteratively, and smartly, some hyper-parameters in order to find as quickly as possible the best ones to achieve the best classification accuracy a pipeline can offer.** 

All my code is publicly available on [GitHub](http://hdi-project.github.io/DeepMining/), feel free to use/share/fork/modify and send feedback ! I am also part of an initiative to improve hyper-parameter optimization solutions within Scikit-Learn (see the PR [here](https://github.com/scikit-learn/scikit-learn/pull/5491) and [here](https://github.com/scikit-learn/scikit-learn/pull/5185)). Please contact me if you'd like to contribute.


***Abstract*** (I'll soon link a paper on arXiv):  
Every machine learning model has several hyper-parameters that need to be carefully chosen for they can hugely impact its quality. While grid search was the first automatic approach to tackle this problem, random search has proved to be much faster for such tasks. Recently some sequential models have been proposed in order to leverage the information acquired during the search process. We build our work upon such a technique which models the performances yielded by the hyper parameters with a Gaussian Process (GP).  First, I developed a novel non-parametric approach for Gaussian Copula Processes (nGCP), and use it for hyper-parameter optimization. In addition, I built a framework to auto-tune machine learning pipelines. Specifically, I considered noisy performance evaluations which speeds up the search and paves the way for parallel designs. I finally demonstrated that nGCP outperforms GP for regression. I also tested nGCP-based hyper-parameter optimization techniques on two classic problems involving text data and images. The results showed that even with noisy estimations our techniques outperform random search, and that nGCP-based methods are faster than GP-based ones. 
