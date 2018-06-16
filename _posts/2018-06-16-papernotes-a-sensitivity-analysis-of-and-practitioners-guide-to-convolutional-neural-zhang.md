---
layout: single
classes: wide
title:  "READING NOTES: Practitioners’ Guide to CNN on sentence classification (Zhang and Wallac)"
tags: [notes, paper]
date:   2018-06-16
---


Reading notes of [A Sensitivity Analysis of (and Practitioners’ Guide to) Convolutional Neural](https://arxiv.org/pdf/1510.03820.pdf)

# Main Idea:
How sentence classification performance of one-layer CNNs was effected on 9 datasets regarding to the following architecture components: 
- input word vector representations
- filter region size
- number of feature maps
- activation functions
- pooling strategy
- regularization

## CNN Architecture

- **use slide windows on sentence matrix**: sentence matrix constitute of word vectors ->
three filter sizes each with 2 filters = 6 feature maps ->
- **max-pooling**:
max-pooling on each feature map ->
- **concatenation**:
feature vector = concatenation of the 6 max features ->
- **softmax**:
softmax layer for classification

## Experiments and Results
- 9 datasets on sentence classification.(7 same in [Kim (2014)](http://www.aclweb.org/anthology/D14-1181))
- 10-fold cross validation on all datasets
- Effects of factor:
	- input word vectors: 
		- one-hot performs worse than embeddings on sentence classification (was originally used for doc classification);
		- **embeddings trained from scratch** may be best.
	- filter sizes 
		- **coarse grid search** could work
		- **multiple** different filters with size (close to optimal) may help
		- number of each filter (depend on datasets, 100-600, note might overfitting if too large)
	- activation function
		- Best: **ReLU, tahn**, Iden (no activation)
		- if multiple hidden layers, consider ReLU and tahn
	- pooling
		- **global max pooling** better than local, k-max pooling, and average pooling
	- regularization:  not helping much
		- small dropout (0-0.5): depends on datasets 
		- large $$l2$$ norm 
		- increse number of feature maps to see if help


### Discussion
Well, hyperparameter tuning is always time-consuming and sometimes even frustrating.
Though it's task specific, the baseline configuration and suggestions included in the paper  could be useful for practitioners on this task:
- input word vectors: Glove 
- filter region size: (3,4,5)
- feature maps: 100
- activation function: ReLU
- pooling: 1-max pooling
- dropout rate: 0.5
- l2 norm constraint: 3

