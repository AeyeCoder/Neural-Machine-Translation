English to Spanish Neural Machine Translation (Seq2Seq with LSTMs)

This project implements a sequence-to-sequence (seq2seq) model for translating English sentences into Spanish using TensorFlow/Keras. The implementation is built from scratch without relying on pretrained models, to demonstrate the fundamentals of neural machine translation.

Project Overview

The model is based on the encoder–decoder architecture with recurrent neural networks (RNNs). A bidirectional LSTM encoder processes English sentences, and a unidirectional LSTM decoder generates Spanish translations step by step. Tokenization is handled with TensorFlow’s TextVectorization layer, and custom start/end sequence tokens manage sentence boundaries during training and inference.

While attention and Transformers dominate modern NMT, this project revisits the classical seq2seq approach for educational value, highlighting the strengths and limitations of RNN-based translation.

Dataset

Source: spa-eng dataset

Pairs of English–Spanish sentences are preprocessed and split into training and validation sets.

Sentences are tokenized and padded to a fixed sequence length. Special tokens startofseq and endofseq are added for target sentences.

Model Architecture

Text Vectorization: Tokenizes and integer-encodes English and Spanish text.

Embedding Layers:

English embedding for encoder input.

Spanish embedding for decoder input.

Encoder:

Bidirectional LSTM

Concatenated forward and backward hidden states passed to the decoder.

Decoder:

LSTM initialized with encoder states

Outputs sequence of hidden states for prediction.

Dense Layer: Final softmax layer projects decoder outputs onto the Spanish vocabulary.

Training

Optimizer: Nadam

Loss: sparse_categorical_crossentropy

Metrics: Accuracy (on predicted tokens)

Training halted at ~11% accuracy after several epochs. This plateau demonstrates the practical limitations of training such models from scratch on modest hardware without attention.

Results

The model generates partially correct but noisy translations.

Frequent out-of-vocabulary tokens ([UNK]) and repetition illustrate the need for attention mechanisms and larger vocabularies.

Despite modest accuracy, the project successfully demonstrates how seq2seq architectures are trained end-to-end.
