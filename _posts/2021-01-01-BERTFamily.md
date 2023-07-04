---
title: 'BERT Family'
date: 2021-01-01
permalink: /posts/2020/01/BERTFamily/
tags:
  - BERT
  - Trnasformer
  - NLP
---
Here are some unedited, raw notes I've collected over the years on various transformers. They're pretty much my cheat sheets that I thought you might find interesting. If you spot any errors or have any suggestions, feel free to let me know. All of the images are sourced from the respective papers, Enjoy!

   * [Attention is all you need](#attention-is-all-you-need)
   * [BERT](#bert)
   * [RoBERTa](#roberta)
   * [ALBERT](#albert)
   * [AMBERT: A Multigrained BERT](#ambert-a-multigrained-bert)

# Attention is all you need
[Paper](https://arxiv.org/abs/1706.03762) from Google



# BERT
BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

[Paper](https://arxiv.org/abs/1810.04805) from Google


BERT is based on subword token encoding and multi-layer transformer architecture. The transformer blocks are the same as the original transformer blocks introduced in “Attention is all you need” paper, however BERT only uses the Encoder part of the transformer architecture (and this is why it is not suitable for text generation tasks).

To train BERT, we feed it a massive amount of data and play a game of hide and seek. We mask 15% of the tokens in the text and ask BERT to predict what's hidden. But here's the twist, of these 15% tokens, we only really hide 80%, replace 10% with a random token, and leave the rest 10% as is. Why such an elaborate? Well, if we hid all the tokens, BERT would only focus on those, ignoring the rest. But with this method, BERT tries to predict every token, leading to a comprehensive learning process. 

Once trained, BERT can fine-tune its skills for various language tasks, be it translation, Named Entity Recognition (NER), Question-Answering (QA), or text classification. But remember, BERT isn't perfect. One flaw is that it treats each predicted token as independent and doesn't consider the joint probability between them. But despite that, BERT remains a significant leap in the field of NLP!

