﻿# Text_classification

## Overview
The repository implements the common algorithms for multi-class text classification.
Note that it's just prototypes for experimental purposes only

- Word or char level representation: chi-square+tfidf, word2vec, glove, fasttext, elmo, bert, or concated one
- Model: CNN, BiLSTM, Self-attention,C-LSTM, RCNN, Capsule, HAN, SVM, XGBoost
- Multi task learning: for more than one multi_labels

## Dependencies
- Python 3.6
- Tensorflow 1.12.0

## Usage
`python run_classifier.py`
- for new data, set the `new_data=True`, the model will generate the tf_record and usage the model_params.py
- for existed data, set `new_data=False`, the model will run from the saved tf_record and config.json

## Pretrained
- `mkdir pretrained`, and make sure the word or char level, and chinese word segmentation use the same as pretrained model
- [word2vec Chinese pretrained dowmload](https://github.com/Embedding/Chinese-Word-Vectors)
- [fasttext Chinese pretrained download](https://fasttext.cc/docs/en/crawl-vectors.html)
- [bert Chinese pretrained download from google](https://storage.googleapis.com/bert_models/2018_11_03/chinese_L-12_H-768_A-12.zip)

## Purpose
- The classification is used to clarify the damaged part and damage type from vehicles comments

## Evaluation
- Check in tensorboard: `tensorboard --logdir=./outputs`
- Due to we have too many categories of labels (ca. 500 class for 100,000 examples), and they are not equally important, so we don’t use Macro- evaluation. And the Micro- precision/recall/F1 is the same for multi-label classification. So we check the accuracy and weighted F1.

## Ignored property
- Sometimes in one sample, more than one label are valid
- Some labels have hierarchy relationship
- imbalance issue: weighted loss, data argument, anomaly detection, upsampling and downsampling
