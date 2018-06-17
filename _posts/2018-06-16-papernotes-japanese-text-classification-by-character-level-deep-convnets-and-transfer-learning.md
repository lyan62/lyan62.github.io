---
layout: single
classes: wide
title:  "READING NOTES: Japanese Text Classification by Character-level Deep ConvNets and Transfer Learning (Sato et.al)"
tags: [notes, paper]
date:   2018-06-15
---

Reading notes of [Japanese Text Classification by Character-level Deep ConvNets and Transfer Learning](http://www.scitepress.org/Papers/2017/61934/61934.pdf)

# Main Idea
Character-level deep Convnets and transfer learning for Japanese text classification (news category classification and sentiment analysis).
- does not require morphological analyzer (compared to word-level model)

## Character-level Convnet
- input:(1) onehot (2) char embeddings
- use filter window and max-pooling on concatenation of the representation vector of the sentence.
- while deep model has 6 conv layers and 3 maxpool layers, shallow model has only one of each.

## Experiments and Results
- baseline: Uses bag of words and bag of ngrams as baseline on news category classification and sentiment analysis. 
	- Bag of words wins on AFPBB news datasets as the datasets is relatively too small for the convnets to learn good features.

- transfer learning: use 16-category large-scale dataset for pretraining.
	- fine-tuning based on the pretrained weights of convnets works well.
	- large pretraining dataset scale is more important than similar topics between datasets.

- Features extracted using Char-level convnets are able of representing multiple ngrams.

### Discussion
Transfer learning between different tasks could be more interesting as mentioned as future work in the paper.

