---
layout: single
classes: wide
title:  "READING NOTES: Taskonomy (Zamir et al., 2018)"
tags: [notes, paper]
date:   2018-10-20
---

Reading notes of [the taskonomy paper](http://taskonomy.stanford.edu/). 
References: [1](http://taskonomy.stanford.edu/taskonomy_CVPR2018.pdf), [2](https://zhuanlan.zhihu.com/p/38425434)
## Main idea
- Define target tasks and source tasks and a task dictionary to find relationships between tasks in order to better solve tasks that has limited resources and find the optimized solution. 
- Steps： 
	- task-specific modeling
	- transfer modeling
	- ordinal normalization
	- global taxonomy

## Motivation
- are vision problems related or independent?
- Observations:
	- relationships between different tasks
	- the relationships can be computationally measured
	- tasks belong to a structure

### Task-specific modeling
- model:
	- encoder-decoder structure
		- use encoder to get **representation** and use **decoder for specific tasks** 

### Transfer modeling
- model
	- **readout function** $$D_{s\rightarrow t}$$
		- source task ------> target task (i.e. freeze the parameters in encoder, minimize loss of the output of encoder and target label to learn readout funciton)
		- multi-orders represents that multiple sources are used as input as multiple tasks are related to each other
		- different encoders provide different information for the readout funciton
	- encoder
	- decoder
	- loss functions

### Ordinal Normalization
- Why
	To see how different sources contribute to a specific task. Before normalization, the loss is different for different sources.

- Goal: Normalize different losses and obatin relationships and represent as an affine matrix. (i,j) in this matrix represent using source i how much it is better than using source j.


### Global Taxonomy: batch of targets
Given a batch of targets, design a global transfer policy based on the affine matrix to maximize the collective performance of all tasks, and minimize the used supervision, i.e. perform subgraph selection to find the optimized sources for specific tasks.


## Experiments
- 26 tasks, 4 source only tasks, 22 target tasks.
- ~4M images
- Results:
	- Quality and Gain: compared how transfer tasks learning with limited data from
		- training with limited data from scratch
		- training with large dataset form scratch 
		![](http://i.markdownnotes.com/image_5AeUk5C.jpg)[img source](http://taskonomy.stanford.edu/taskonomy_CVPR2018.pdf)
	- Generalize to novel tasks
		![](http://i.markdownnotes.com/image_sCUvxGN.jpg)[img source](http://taskonomy.stanford.edu/taskonomy_CVPR2018.pdf)
		
## Discussion
The idea is cool to learn relationships between tasks and try to solve tasks with limited resources from various source tasks, however the generated taskonomy may vary from the data it trained on, which saying that to apply the taskonomy, pretraining on customerized datasets may be needed for good performance.