Encoder-Decoder Architecture in NLP


1. What is Encoder-Decoder Architecture?

Encoder-Decoder is a deep learning architecture used for Sequence-to-Sequence (Seq2Seq) learning.

It consists of two main components:

Encoder: Processes the input sequence and converts it into a numerical representation.

Decoder: Uses the encoded representation to generate the output sequence.

It is commonly used in machine translation, text summarization, question answering and text generation.

Example: Machine Translation

Input (English): We are learning NLP.

Output (Hindi): Hum NLP sikh rahe hain.

Here, the input and output are both sequences of text, but they belong to different languages.


2. Why Do We Need Encoder-Decoder?

Consider machine translation.

We want to convert an English sentence into Hindi.

A traditional classification model generally produces a fixed output, such as Positive or Negative.

However, machine translation requires generating an entire sequence of words.

This is called Sequence-to-Sequence (Seq2Seq) learning.

Examples:

Task

Input

Output

Machine Translation

English sentence

Hindi sentence

Text Summarization

Long paragraph

Short summary

Question Answering

Question and context

Answer

Chatbot

User message

Generated response

The input and output sequences can have different lengths.


3. Encoder-Decoder Architecture

Before processing text, we need to convert it into numerical representations because neural networks work with numbers.

Basic Architecture

Source Language (English)
          |
          v
      Tokenization
          |
          v
       Embedding
          |
          v
        ENCODER
          |
          v
   Context Representation
          |
          v
        DECODER
          |
          v
 Target Language (Hindi)


Step-by-Step Working


Step 1: Input Sequence

Input: We are learning NLP.


Step 2: Tokenization

The sentence is divided into tokens:

["We", "are", "learning", "NLP"]


Step 3: Embedding

Each token is converted into a numerical vector using an embedding layer.

These vectors represent the tokens in a form that the neural network can process.


Step 4: Encoder

The encoder processes the input vectors sequentially and captures information from the source sentence.


Step 5: Context Representation

The encoder's final states represent information from the input sequence.

In a basic LSTM Encoder-Decoder, the final hidden state and cell state are passed to the decoder.


Step 6: Decoder

The decoder uses the encoded representation to generate the target sentence, one token at a time.

Output: Hum NLP sikh rahe hain.


4. Role of Encoder

The encoder is responsible for processing the complete input sequence.

In an LSTM-based Encoder-Decoder, each time step receives:

Current input vector (x).

Previous hidden state (h).

Previous cell state (c).

It produces:

Updated hidden state (h).

Updated cell state (c).

Example:

Input: We are learning NLP.

We       → LSTM → h1, c1
are      → LSTM → h2, c2
learning → LSTM → h3, c3
NLP      → LSTM → h4, c4

After processing the complete sentence:

h4 = Final hidden state.

c4 = Final cell state.

These states are passed to the decoder.


5. What is a Context Vector?

A context vector is a numerical representation of the input sequence that helps the decoder generate the target sequence.

In a basic fixed-length Encoder-Decoder architecture, the encoder compresses the input information into a fixed-size representation.

Why is it needed?

The decoder needs information about the source sentence to generate the correct target sentence.

The encoder's final states provide this information.

Limitation: Compressing a long sentence into a fixed-size representation can cause information loss. This is one of the reasons Attention Mechanism was introduced.


6. Role of Decoder

The decoder generates the target sequence using the encoder's representation.

It receives:

Encoder's final hidden state.

Encoder's final cell state.

Start of Sequence (SOS) token.

It generates the output one token at a time.

Example:

Input: SOS       → Output: Hum
Input: Hum       → Output: NLP
Input: NLP       → Output: sikh
Input: sikh      → Output: rahe
Input: rahe      → Output: hain
Input: hain      → Output: EOS

The generation stops when the decoder produces EOS.
