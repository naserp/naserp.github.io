---
title: 'BERT Family'
date: 2021-01-01
permalink: /posts/2020/01/BERTFamily/
tags:
  - BERT
  - Trnasformer
  - NLP
---
In the world of Natural Language Processing (NLP), Bidirectional Encoder Representations from Transformers (BERT) has become a game-changer. Developed by Google, BERT has set new benchmarks for tasks like sentiment analysis, named entity recognition and text classification. However, BERT is not a monolithic model; it's a family of related architectures, each designed for specialized use-cases. This post aims to review the BERT family, highlighting their distinct capabilities, applications, and how they compare to each other.

   * [Attention is all you need](#attention-is-all-you-need)
   * [BERT](#bert)
   * [RoBERTa](#roberta)
   * [ALBERT](#albert)
   * [AMBERT: A Multigrained BERT](#ambert-a-multigrained-bert)

# Attention is all you need
[Paper](https://arxiv.org/abs/1706.03762) from Google

It all originates from this and isn't actually a member of the BERT family. Rather, it serves as a sort of parent to BERT.

"Attention Is All You Need" introduced the Transformer architecture, revolutionizing how we process language by relying solely on attention mechanisms. BERT built on this, using bidirectional attention to understand word context, setting new standards in NLP tasks like text classification and question answering. Together, they've significantly impacted modern NLP.

# BERT
BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding

[Paper](https://arxiv.org/abs/1810.04805) from Google

![pic](https://github.com/naserp/naserp.github.io/blob/e8bcbc2cefe1e0c9398ecb6babb6a0af25d6a1b1/images/bert.png)

BERT is based on subword token encoding and multi-layer transformer architecture. The transformer blocks are the same as the original transformer blocks introduced in “Attention is all you need” paper, however BERT only uses the Encoder part of the transformer architecture (and this is why it is not suitable for text generation tasks).

To train BERT, we feed it a massive amount of data and play a game of hide and seek. We mask 15% of the tokens in the text and ask BERT to predict what's hidden. But here's the twist, of these 15% tokens, we only really hide 80%, replace 10% with a random token, and leave the rest 10% as is. Why such an elaborate? Well, if we hid all the tokens, BERT would only focus on those, ignoring the rest. But with this method, BERT tries to predict every token, leading to a comprehensive learning process. 

Once trained, BERT can fine-tune its skills for various language tasks, be it translation, Named Entity Recognition (NER), Question-Answering (QA), or text classification. But remember, BERT isn't perfect. One flaw is that it treats each predicted token as independent and doesn't consider the joint probability between them. But despite that, BERT remains a significant leap in the field of NLP!

# RoBERTa
RoBERTa: A Robustly Optimized BERT Pretraining Approach

[Paper](https://arxiv.org/abs/1907.11692)  from UW and Facebook AI

The RoBERTa paper puts BERT's functionalities under a microscope, playing around with its different components to see their impact on task performance. The findings? Larger batch sizes are better for performance, the Next Sentence Prediction (NSP) doesn't really make a difference, and dynamic masking outperforms static masking. They compiled these insights and served us RoBERTa, a more robustly optimized BERT approach.

 RoBERTa provides a better pre-trained compared to BERT by
- training the model longer, with bigger batches, over more data
- removing the next sentence prediction objective 
- training on longer sequences 
- dynamically changing the masking pattern applied to the training data

They found that BERT was far from reaching its full potential, so they beefed it up, feeding it a 160GB of text instead of the original 16GB, and amping up the batch size from 256 to 8k. They also showed NSP the door, as it wasn't really contributing to the model's performance.

The results? RoBERTa was a rockstar on the GLUE benchmark, matching XLNet's performance and setting new records in 4 out of 9 individual GLUE tasks. It also held its own on SQuAD and RACE, matching the best scores. So, in essence, RoBERTa was a power-up to BERT, a more robust and optimized transformer that took NLP performance to new heights.


# ALBERT
ALBERT: A Lite BERT for Self-supervised Learning of Language Representations

[Paper](https://arxiv.org/abs/1909.11942) from Google Research and Toyota Technological Institute 

ALBERT introduces two techniques for reducing the parameters in pre-trained models, overcoming scaling issues.

First up, we've got Factorized Embedding Parameterization. Unlike BERT, and RoBERTa where the WordPiece embedding size is the same as the hidden layer size, ALBERT decomposes the large vocabulary embedding matrix into two smaller ones. This way, we can increase the hidden layer size without drastically expanding the parameter size of the vocabulary embeddings. The reduction in embedding parameters is significant, especially when the size of the hidden layers is much larger than the size of the embeddings.

Next, ALBERT employs Cross-Layer Parameter Sharing. This smart strategy keeps parameters from ballooning with the network's depth. Both techniques dramatically cut down the number of BERT parameters without majorly affecting performance, giving us a model that's both effective and efficient. In fact, an ALBERT model similar to BERT-large has 18x fewer parameters and trains about 1.7x faster. These techniques also offer a bonus feature – they act as a form of regularization, stabilizing training and aiding generalization.

And there's more! ALBERT also introduces a self-supervised loss for sentence-order prediction (SOP) to further boost its performance. This helps the model better understand discourse-level coherence. SOP is a more challenging task than NSP but is able to solve the NSP task reasonably well.

Interestingly, ALBERT skips dropout. The powerful regularization effect of parameter sharing in ALBERT means dropouts aren't necessary. This shows that many assumptions we often take for granted may not always hold true. (Note that ALBERT v1 did include dropouts).

# AMBERT: A Multigrained BERT

[Paper](https://arxiv.org/abs/2008.11869) by ByteDance 

AMBERT brings a new spin to BERT by using dual tokenization. It employs both a fine-grained (subword or word level) and a coarse-grained (phrase level) tokenizer on the input.

Both inputs then use a shared BERT encoder. The process of a forward pass in the model includes these steps:

Text tokens to token embeddings (via individual weights): The model transforms each list of tokens, both fine and coarse-grained, into real-valued vectors using separate embedding matrices.
Token embeddings to contextual embeddings (via shared weights): Both real-valued vectors are then channeled into the same BERT encoder, a stack of Transformer layers. This can be done either one after the other through a single encoder copy, or concurrently through two encoder copies with tied parameters, resulting in two lists of per-token contextual embeddings.
While AMBERT's use of two separate embedding matrices (one for each tokenization type) means it has a higher parameter count than BERT (194M versus 110M for English Base models), the latency remains fairly consistent as the only addition in AMBERT is an extra set of dictionary lookups.
