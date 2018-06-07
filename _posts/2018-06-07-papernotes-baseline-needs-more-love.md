---
layout: single
classes: wide
title:  "READING NOTES: Baseline needs more love(Shen et.al)"
date:   2018-06-07
---

Reading notes of [Baseline Needs More Love: On Simple Word-Embedding-Based Models and Associated Pooling Mechanisms](https://arxiv.org/abs/1805.09843)

### Main Idea: 
Point to point comparision between **Simple word embedding based models**(pooling strategies) and **RNN/CNNs** on 17 datasets and three tasks:
1. long document classification
1. text sequence matching
1. short text tasks (classification & matching)

#### SWEM-based:
- Pooling strategies:
	1. **average pooling**: Average of word embeddings for input sequence.
	1. **max pooling** on fix dimension of word embedding matrix  --> most salient features
	1. **hierarchical pooling** --> abstract and keep spatial info
	 - average pooling in window of length $$n$$ =>
	 - max-pooling on features from all windows
	1. **concat features extracted from first two**

- Parameters and speed:
	faster than CNN/RNN by a factor of $$nd$$ or $$d$$.

#### Experiment details:
- Embeddings: Use GloVe embeddings  or refined embeddings with MLP
- Method: SWEM-based **v.s.** CNN/RNN/LSTM
- Tasks:
	- document categorization: topic categorization; sentiment analysis, ontology classification.
	- sentence matching
	- sequence tagging(CoNLL2000, CoNLLL2003 NER)

#### Results
SWEM-based methods with poolings strategies, especially hierarchical pooling, has comparable/better performance and is more computationally efficient. Not as good on classifying short sentences.


##### Discussion on word-order features
The paper has an interesting discussion on the importance of word-order features, and perform an experiment by **shuffling words in training, and keeping word order in test set** => LSTM has comparable accuracies on Yahoo and SNLI to unshuffeled training data! 

Sentiment analysis is more sensitive to word-order features than other tasks.



	
	
