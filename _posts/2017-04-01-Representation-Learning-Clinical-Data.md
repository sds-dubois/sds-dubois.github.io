---
layout: post
section-type: post
title: Representation Learning for Clinical Data
featured: true
post-preview: One of my main focus at the [Shah Lab](https://shahlab.stanford.edu/) was to design data-driven models to learn effective, low-dimensional representations of clinical data. I present in this post the common challenges that working with clinical data raises and two different approaches to representation learning and transfer learning.
---
One of my main focus at the [Shah Lab](https://shahlab.stanford.edu/) was to design data-driven models to learn effective, low-dimensional representations of clinical data.
I present in this post the common challenges that working with clinical data raises and two different approaches to representation learning and transfer learning.

### Challenges raised by clinical data

At the Shah Lab we work with Electronic Health Records (EHR) which are basically logs of everything that happens to a patient in a hospital. So these records contain a large set of numerical features such as patient demographics (e.g. age, gender, ethnicity), lab measurements (e.g. blood gases, fluid balances, vital signs), binary indicators for diseases and medical procedures, as well as free-text clinical notes from nurses. In our data warehouse for Stanford Hospital, the total number of unique features is nearly half a million.  

The first challenge is that the data is very sparse with regards to observations: usually, just a few of these 500k features will be non-null. The second challenge is that in many cases populations quickly become scarce when restricted to cohorts of interest. For example I worked on a project to identify patients who are latent, un-diagnosed cases of Familial Hyperlipidemia (FH, which is a genetic disorder characterized by high cholesterol and increased risk of heart disease). Stanford physicians have identified only 89 patients with FH, whereas the population prevalence of FH suggests around 5-10k patients.

Learning in this setting is very challenging and practitioners often rely on feature engineering and selection based on domain expertise:  each new research question or predictive model requires starting from scratch, acquiring new domain expertise to guide both feature engineering and the search for a solution to the absence of labels.
That is why Representation Learning and Transfer Learning could benefit a lot to the field.


### Cross-channel auto-encoders

The idea behind this approach is that our data is redundant and that we can use this to provide supervision in a auto-encoder like architecture.
For example, if a patient as diabete, we expect this information to be encoded in his records both with the diagnosis codes (ICD9) and the clinical notes.

Therefore, we split the features into two categories (eg medical codes vs. text-derived features) and use one split as input, the other as output, to train auto-encoder (and vice versa).
Such models are then used as feature extractors, on top of which we can fit logistic regressions, or other simple models, even with very small data sets (we tested with groups of 500 patients). This approach consistently outperformed the classic bag-of-word aggregation of codes.

### Representation Learning for Clinical Notes

This approach focuses on clinical notes since it is an unstructed, complex source of information which is often under-used in medical settings.
One additional challenge to our use case is that for de-identification purposes, the order of words in clinical notes is removed. Thus, we can view a patient's history
as a sequence of un-ordered collection of words (notes are ordered by timestamps accross visits).

We investigated two seperate approaches:  
- embed and aggregate: compute word level embeddings that are aggregated at the note level first, and then at the patient level. Embeddings are computed with Glove 
or word2vec after re-generating notes with words in a random order.  
- using recurrent neural nets (RNN) whose inputs are a sequence of bag-of-words vectors representing the clinical notes for a given patient’s input era. This approach jointly learns word-, note-, and patient-level embeddings through weak supervision of high-level disease codes.  

Both approaches showed compelling advantages over BOW and topic model representations across a range of tasks and cohort sizes. The embed-and-aggregate method in particular represents a sweet spot in the performance/complexity trade-off because it is remarkably simple to learn, distribute and use, requiring little in the way of specialized hardware or software.   



### Publications

-[ Learning Effective Representations from Clinical Notes](https://arxiv.org/abs/1705.07025)  
-[ The Effectiveness of Transfer Learning in Electronic Health Records Data](https://openreview.net/pdf?id=B1_E8xrKe) (ICLR 2017 Workshop)