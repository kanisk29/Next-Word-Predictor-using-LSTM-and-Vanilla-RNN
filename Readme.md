Neural Language Modeling – RNN vs LSTM Text Generation

This module implements a word-level neural language model using SimpleRNN and LSTM architectures. The objective is to predict the next word given a fixed-length input sequence and generate coherent text using temperature-controlled sampling.

Problem Statement

Given a sequence of previous words, predict the next word in the sequence.

This is a next-word prediction (language modeling) task trained using sparse categorical cross-entropy loss and evaluated using perplexity.

Data Preprocessing

Raw text loaded from acc.txt

Lowercasing and line cleaning

Tokenization using Tokenizer

Sliding window sequence generation

Sequence length: 10 words

Input: 10-word sequence

Target: Next word

Example transformation:

Input:  w1 w2 w3 ... w10
Target: w11
Model 1 – SimpleRNN Baseline

Architecture:

Embedding (dimension = 16)

SimpleRNN (128 units)

Dense (Softmax over vocabulary)

Training:

Epochs: 20

Batch size: 64

Loss: Sparse Categorical Crossentropy

Performance:

Test Loss: 9.7209

Perplexity: 16662.26

Generated Sample:

inheritance values are often data created obtained context of a phrase schemas in

Observation:

High perplexity

Weak long-range context modeling

Limited coherence in generated text

Model 2 – Stacked LSTM

Architecture:

Embedding (dimension = 100)

LSTM (300 units, return_sequences=True, dropout=0.2)

LSTM (300 units, dropout=0.2)

Dense (Softmax over vocabulary)

Training:

Epochs: 20

Batch size: 64

Loss: Sparse Categorical Crossentropy

Performance:

Test Loss: 9.4513

Perplexity: 12724.68

Generated Sample:

the centre of the scientific html content for a topic for the

Observation:

Lower perplexity compared to SimpleRNN

Improved sequence coherence

Better contextual word prediction

Temperature-Based Sampling

Implemented probabilistic sampling using temperature scaling:

Temperature = 0.3 → More deterministic, repetitive

Temperature = 0.7 → Balanced creativity

Temperature = 1.1 → More diverse, less predictable

Example outputs:

Temperature 0.3:

the billionaire of the brain’s database did his help in the sea

Temperature 0.7:

the billionaire country using einstein’s rule and 2004 the indian language and

Temperature 1.1:

the billionaire country after researchers of the iconic to grow scientific us add
Key Takeaways

LSTM significantly outperforms SimpleRNN in language modeling tasks.

Perplexity is a better metric than accuracy for generative language models.

Stacked LSTM layers improve contextual understanding.

Temperature scaling controls randomness during text generation.
