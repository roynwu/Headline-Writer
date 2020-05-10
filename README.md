# Headline-Writer
### Abstractive Text Summarization with Attention and Pointer-Generator Network

This repository contains implementations of Sequence-to-sequence (Seq2Seq) neural networks for abstractive text summarization. We implement Attention mechanism, Teacher Forcing algorithm, and Pointer-Generator Network (inspired by [Get To The Point: Summarization with Pointer-Generator Networks](https://arxiv.org/pdf/1704.04368.pdf)) in our experiment to improve our baseline models.

Sequence-to-sequence (Seq2Seq) neural networks have been proved to be effective in tasks that involve transforming text from one form to another (e.g. machine translation and speech recognition). They can also be used to generate summarization from text input. In this project, we compare summarization results of a non-deep learning method and results of different implementations of the seq2Seq network. The deep learning implementations include using Bi-directional long short-term memory (BiLSTM), additive attention, and teacher forcing in the Seq2Seq network. More advanced approaches using pointer-generator and coverage are also applied to improve the summarization results.

## Dataset

We use [“All the news”](https://components.one/datasets/all-the-news-articles-dataset) dataset published by Thompson (2019).  This dataset contains 204,135 news articles with headlines from 18 different American publications. It is an updated version of tbe dataset posted on Kaggle, containing over 50,000 more articles from a great number of publications.

## Methods

Pipeline

<p align="center">
  <img src="https://github.com/roynwu/Headline-Writer/blob/master/pipeline.png">
</p> 

Summary of methods used in our experiments

<p align="center">
  <img src="https://github.com/roynwu/Headline-Writer/blob/master/methods_table.png">
</p> 

Figure of Pointer-Generator Network

<p align="center">
  <img src="https://github.com/roynwu/Headline-Writer/blob/master/pointer%20generator.png">
</p> 

## Results

Loss curves

<p align="center">
  <img src="https://github.com/roynwu/Headline-Writer/blob/master/loss%20curve.png">
</p> 

Result comparison on data subset

<p align="center">
  <img src="https://github.com/roynwu/Headline-Writer/blob/master/results_table.png">
</p> 

Example

<p align="center">
  <img src="https://github.com/roynwu/Headline-Writer/blob/master/generated%20text.png">
</p> 

## Conclusion

* 1 - BiLSTM is the base RNN unit that has the best performance in our application scenario, (possible reason may be that BiLSTM can utilize the information from both previous and posterior context)

* 2 - Self-attention can help improve generator’s performance when dealing with long source article (by learning a probability distribution that tells us which part of the source text should be paid more attention to, which makes up for the flaw of BiLSTM that tends to forget the long-term dependencies)

* 3 - Teacher forcing is an effective training approach that can be used for Seq2Seq model scenario, (to prevent the error from previous prediction being passed into next state)

* 4 - Pointer generator and coverage approach can significantly reduce the occurrence of the model generating faulty information by including the probability of directly outputting words from the source text

* 5 - Our best model (BiLSTM with self-attention, pointer generator, and coverage structure) beats our main source paper’s BLEU score of 0.010 [Lopyrev](https://arxiv.org/pdf/1512.01712.pdf) by 0.075

## References

See report for details.
