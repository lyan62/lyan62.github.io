---
layout: single
classes: wide
title:  "READING NOTES: Sentence embeddings for linguistic properties (Conneau et al., 2018)"
tags: [notes, paper]
date:   2018-07-17
---


# Main Idea:
Probe linguistic properties of sentence embeddings using 3 encoders, trained in 8 ways, on 10 probing tasks.

Extend **probing task** to see if the sentence embeddings contains related information:
- probing task: e.g.sentence classification based on the tense of the main verb (input as a single sentence representation)
	- minimize interpretability problems
	-  easy to control for biases
	-  agnostic w.r.t encoder architecture

## Motivation
- previous intropspection techinuques  depend on specifics of encoder archtectures.
- to consider more models and tasks while ensuring using only a sentence embedding as input.
- to provide general purpose, cross-model evaluation.


## Experiments 
- 10 Tasks:
	- Overview: with single sentence embeddings inputs; large training sets for dl; with sentence length and lexical cues constraints
	- including:
		- _surface information_ : 
			- **SentLen**: predict sentence length (word-level length), trained with sentences binned by length. 
			- **WC**: recover original words given sentence embeddings
		- _syntatic information_ :
			- **bigram shift**: legal word order sensitivity test (identify sentences with inverted two random continuous words)
			- **tree depth** : infers tree depth
			- **top const**: classified in terms of  top constituents
		- _semantic information_ : generally also requires structure info
			- **Tense**: tense fo main-clause verb.
			- **subject number**:  how many subjects does the main clause contain?
			- **object number**: number of direct objects
			- **semantic odd man out** (SOMO):  tell if the sentence whose randomly noun or verb (in bigram) are replaced with comparable frequent alternatives.
			- **coordination inversion** (corrdInv): tell if the sentences with two coordinate clauses have inverted order.

- 3 Model (Encoders):
	- biLSTM-last/max:  sentence embeddings using last/max hidden state.
	- Gated ConvNet: gated output of conv layer, followed by max-pooling for feature maps 
 
- 8 Training methods: 
	-	NMT(EN-FR, GE-EN, EN-FIN) (trained on europarl)
	-	Autoencoder
	-	Seq2Tree
	-	skipthought
	-	NLI
- Data: Toronto Book Corpus (Zhu et al., 2015, Paperno et al. 2016)
	- training sets: 100k sentences, 10k validitaion and test, balanced classes



## Results
- Base lines: linear classifier on length; NB classifier with tfidf(uni, and bigrams), BoV-fastText for sentence representations.

- Performance: 
	- Models:
		- Bag-of-Vectors good overall (good on WC, SentLen, Tense,  subjnum, objnum, **topconst, treedepth**, random on bigram shift as no order info are captured);
		- Gated CNN on par with best LSTM
	-  Training methods: 
		-  NMT captures more linguitic features than NLI, NLI better at keeping shallow features,
		-  NMT & skipthought (good with WC as epochs increase, more training does not help on semantic odd man out and sentLen, claims that models tends to forget superfacial feature if caputers deeper linguistic properties.)
		-  seq2tree good on topconst, tense, subjnum, objnum and tree depth.
		-  seq2tree and NMT comparabel on SOMO and coordInv
		-  untrained BiLSTM already have very good performance on probing and downstream tasks. bias exists in juding modifeid compared to human.
		-  NMT trained BiLSTM generally good. Far from human bounds on treedepth, bigram shift, somo, and coodInv.

## Conclusion
- Relations between probing and downstream tasks: 
	- with WC positively related in  all downstream tasks, while SentLen being negative correlated; semantic odd man out relates to sentence entailment test; question classification relates to most of the probing tasks.
- Models: BoV good overall, bilstm good without training, different encoders results in different embeddings captures info with different focus.

