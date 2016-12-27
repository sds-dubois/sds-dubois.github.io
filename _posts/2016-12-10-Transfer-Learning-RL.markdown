---
layout: post
section-type: post
title: Transfer Learning in Reinforcement Learning
post-preview: This project addresses the challenge of knowledge transfer in Reinforcement Learning. We focused on Q-learning with global approximation, and studied methods to leverage access to simple source tasks in order to later tackle a target task. Benefits of such transfer include improved initial or asymptotic performance, reduced learning time...
---
I worked on this project with [Guillaume Genthial](https://fr.linkedin.com/in/guillaumegenthial/en) for my
course on [Decision Making under Uncertainty](http://web.stanford.edu/class/aa228/#!index.md) at Stanford.
We were interested in investigating methods to transfer knowledge in reinforcement learning from some *source* 
tasks to a *target* task. The source tasks can differ by the state-actions domains,
dynamics (transition functions) and objectives (reward functions). 
Precisely, we wanted to address the case where the target task is a difficult, real-world problem for which we 
can't afford to learn directly in this environment (eg driving a car or a plane), but for which we can design 
imperfect models and simulations (the source tasks). 


We narrowed our project to the framework of Q-learning with global approximation, and to the case where the source tasks' 
state-action domain is a subset of the target state-action domain. To transfer knowledge, we first train agents on simple 
source tasks. Then, we use this to train an agent on a more complicated target task. Our models learn the target Q-function 
using the source Q-functions as features and some (light) interaction with the environment. 


We tested our algorithms against the [mountain-car benchmark from OpenAI Gym](https://gym.openai.com/envs/MountainCar-v0) and observed 
general improvement in both speed and performance.
[Our code](https://github.com/GuillaumeGenthial/Q-transfer) is available on Github and the full report is **[here](http://bit.do/transferRL)**. 

<center><img src="https://sds-dubois.github.io/img/projects/TransferRl-Env.png"></img></center>  
