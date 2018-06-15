---
layout: single
classes: wide
title:  "READING NOTES: CNN for Sentence Classification (Yoon Kim)"
tags: [notes, paper]
date:   2018-06-15
---

Reading notes of [Convolutional Neural Networks for Sentence Classification](http://www.aclweb.org/anthology/D14-1181).

# Main Idea:
Sentiment analysis and question classifiction using CNN with (task-specific) pretrained word vectors. Better performance on 4 out of 7 datasets.

Pretrained word vectors --> One convolutional layer --> Sentence classification.

## CNN Model
**conv + max-pool** (multiple filter of different size) -> **FC layer** (dropout, softmax)
     
-  one feature with one filter: Slide window + max-pooling 
	- Window of $$h$$ words (filter) slides over matrix $$length\times dim_{embed}$$  ==> Obtain **feature map**: $$\mathbf{c} = [c_1, c_2, ..., c_{n-h+1}]$$
		where each $$c_i$$ is a nonlinear mapping of the words representation ($$h\times dim_{embed}$$) in the window.
	- Max-pooling on $$\mathbf{c}$$ ==> $$\hat{c}$$.
- Sentence representation $$\mathbf{z} = [\hat{c}_1,...\hat{c}_{filterNum}]$$  
	- use various filter size (window size)
- dropout  constrained on l2-norms of weight vectors


## Experiments and Results
- word representation variants:
	- random initialized
	- pretrained (static)
	- pretrained + task-specific fine-tuned
	- multichannel: static + fine tune in backprop
- better on 4 out of 7 datasets


### Discussion
The paper provides insights of how fine-tuned word representation (non-static channel) has words with similar meaning in close distance compared to static, and how hyperparameters such as dropout and initialization of word-embeddings influence classification accuracy.

