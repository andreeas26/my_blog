---
aliases:
- /data-augmentation/deep-learning/error-analysis/learning-rate/notes/2021/03/31/dl-toolbox
categories:
- deep-learning
- notes
- learning-rate
- data-augmentation
- error-analysis
date: '2021-03-31'
description: A list of tools that can improve the performance of a DL model.
hide: false
layout: post
search_exclude: false
title: Deep Learning Toolbox
toc: true

---

![](images/toolbox.gif)

## Presizing

- Def: a strategy for performing data augmentation more efficiently by reducing the number of transformations and lossy operations
- Step 1: resize to a larged dimension than the one needed by the model
- Step 2: combine all the transformations (including the resize for the target dimension), on the GPU only once, and then one single interpolation in the end

## Learning Rate Finder

- Def: train one batch for several iterations while increasing the LR at each step and recording the loss; plot the loss as a function of the LR
- a simple method for finding a "more" optimal LR; see the [paper](https://arxiv.org/abs/1506.01186) by Leslie Smith 

## Discriminative Learning Rates
- train the layers of a network at different speeds, by using different LRs when doing transfer learning => early layers - lower LR, last (random) layers - higher LR
- fastai uses a `slice` object from Python to achieve this:  `a[start:stop:step] == a[slice(start, stop, step)]`

## Error analysis by clustering incorrect predictions
- select all incorrent predictions; it might be useful to sort them in descending order by the error
- apply a clustering algorithm
- manually check the clusters for common features
- not very feasible on images ?
