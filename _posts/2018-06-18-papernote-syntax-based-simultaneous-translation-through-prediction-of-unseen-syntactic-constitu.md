---
layout: single
classes: wide
title:  "READING NOTES: Syntax-based Simultaneous Translation through Prediction of Unseen Syntactic Constituents (Oda et.al)"
tags: [notes, paper]
date:   2018-06-18
---

Reading notes of [Syntax-based Simultaneous Translation through Prediction of Unseen Syntactic Constituents
](http://www.aclweb.org/anthology/P15-1020)

# Main Idea:
Simultaneous machine translation by 
- predicting unseen syntactic constituents which assist for complete parse tree generation
- waiting for more information if fluent translation not available.

## Motivation
- In SMT, between languages of siginificant syntatic differences, information can be missing in the source language needed to generate target translation, long distance reordering are often needed for translation. 
Another strategy is too predict the missing component to reduce translation latency.
- most parsing methods assume complete syntactic phrase, which is true when giving complete phrase, but results in incorrect parsing if the given unit is incomplete.

## Methods
- Conduct incomplete parsing with:  
$$T = argmax_{T}Pr(T|\mathbf{L}},\mathbf{w},\mathbf{R})$$, where $$\mathbf{L}$$ can be retrieved from history as it was already seen.
- Predict syntactic constitutents: multilabel prediction with linear SVMs based on features including words, pos tags, parse, length of the consititutents.
- Apply the syntactic prediction to MT (Tree to string translation):  if future component needs reordering -->  take a wait action; assume constitutent tag as word.

## Experiments and Results
- predicting syntactic constituents: recall lower than precision
- simultaneous translation on TED talks of EN-JP: waiting strategy for reordering has higher BLEU score.
$$a$$





