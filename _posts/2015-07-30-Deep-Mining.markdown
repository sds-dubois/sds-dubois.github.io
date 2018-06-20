---
layout: post
section-type: post
title: "Deep Mining: Auto-tuning machine learning pipelines"
featured: false
post-preview: I was a visiting student at MIT and worked on a project that we called *Deep Mining*. The goal was to automatically tune Machine Learning pipelines' hyper-parameters through a repeated process of candidate sampling and evaluation. While working on this project, I mainly focused on Bayesian optimization methods and on Gaussian Process-based regression. In particular I developed a new regression algorithm, a *non-parametric Gaussian Copula Process*, that we used to better model the performance of a pipeline given its hyper-parameters. In addition, since the earlier stages of the pipeline can be computationally expensive (data processing, feature engineering..), I also worked on finding efficient methods to estimate pipeline performance via sub sampling.
---

I was a visiting student at MIT and worked on a project that we called *Deep Mining*. The goal was to automatically tune Machine Learning pipelines' hyper-parameters through a repeated process of candidate sampling and evaluation. While working on this project, I mainly focused on Bayesian optimization methods and on Gaussian Process-based regression. In particular I developed a new regression algorithm, a *non-parametric Gaussian Copula Process*, that we used to better model the performance of a pipeline given its hyper-parameters. In addition, since the earlier stages of the pipeline can be computationally expensive (data processing, feature engineering..), I also worked on finding efficient methods to estimate pipeline performance via sub sampling.


<center style="margin-bottom:30px"><img src="https://sds-dubois.github.io/img/projects/DeepMining_workflow2.png"></center>   


This project is still in active development and continues to grow, so check the [project's website](https://hdi-dai.lids.mit.edu/projects/deep-mining/) for updates, and our code will soon be publicly available on **[GitHub](http://hdi-project.github.io/DeepMining/)**. I am also part of an initiative to improve hyper-parameter optimization solutions within Scikit-Learn (see the PR [here](https://github.com/scikit-learn/scikit-learn/pull/5491) and [here](https://github.com/scikit-learn/scikit-learn/pull/5185)). Please contact me if you'd like to contribute.


Publications:    
- [Deep Mining: Copula-based Hyper-Parameter Optimization for Machine Learning Pipelines](/downloads/deepmining_thesis.pdf) (Research thesis)    
- [Sample, Estimate, Tune: Scaling Bayesian Auto-Tuning of Data Science Pipelines](https://ieeexplore.ieee.org/document/8259796/) (IEEE International Conference on Data Science and Advance Analytics, 2017)     
