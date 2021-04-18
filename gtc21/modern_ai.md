---
Title:    Modern Artificial Intelligence 1980s-2021 and Beyond
Author:   Jürgen Schmidhuber
---
# Modern AI 1980s-2021 and Beyond

## 1970

Mordern Backpropagation (or inverted mode of automatic differentiation) invented in Finland by Seppo Linnainmaa

## 1990

### Generative adversarial network

Artificial Curiosity (AAC): world model network (M) and controller network (C)

### Self-supervised learning

Making the world differentiable: On using self-supervised Fully RNN for Dynamic Reinforcement Learning and Planning in Non-Stationary Environment

### 1993

Internal spotlights of attention

### Unsupervised layer-wise pretraining

Neural history compressor

Discover vanishing and exploding gradients in training neural network

### Recurrent neural network

#### Neural history compressor

* unsupervised pre-training overcome long time lags between events,
* RNN stack or hierarchy through predictive coding
* Compress or distill chunker RNN (teacher) into automatizer RNN (student) re-trained on previous skills
* Lowest level RNN see character, self-supervised learning

### Long short-term memory network

Overcome gradient vanishing with gating mechanism, no need for unsupervised pre-training

## 2011

### DanNet

CNN using GPU, SOTA computer vision for 2011 and 2012 (before Alexnet)

## 2015

### Highway network

$$g(x)*x + t(x) * h(x)$$

Residual network is when $g(x) = t(x) = 1$

## 2019

### Reinforcement learning

LSTM trained by policy gradients OpenAI win Dota 2 game.

DeepMind play StarCraft
