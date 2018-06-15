---
layout: single
classes: wide
title:  "READING NOTES: FastText (Joulin et.al)"
tags: [notes, paper]
date:   2018-06-15
---


Reading notes of [Bag of Tricks for Efficient Text Classification](https://arxiv.org/pdf/1607.01759.pdf).
## Main Idea
State-of-art accuarcy, large scale, **fast** text classification using linear models with
- rank constraint
- fast loss approximation

### Linear model with Rank Constraint
Word representations (bag of ngram) --_averaged_--> text representation ==> classification (**softmax** , i.e. NECLoss).
- Complexity: $$O($$num_class * hidden_dim$$)$$
- Speeding up: **Hierachical Softmax** (based on Huffman coding tree) 
	- Complexity $$O($$hidden_dim * $$log_2$$(num_class)$$)$$
	- T top targets in $$O(log(T))time$$.

### Experiments and Results
-  Sentiment analysis
	- hidden_dim=10: bettern than char-CNN and char-CRNN, worse than VDCNN
	-  much much faster
- Tag prediction
	- higher accuray with bigrams
	- much much faster again

#### Discussion
The paper proposes simple but effective baseline method using averaged word representation. The method has on par performance with DL methods on the two classification tasks and is fast and easy to scale.

Seems like when to use LSTM, RNN for text classification would be a good question to ask.

