# Lecture 3: RNN

* [FSDL page](https://fullstackdeeplearning.com/spring2021/lecture-3/)
* [Video](https://youtu.be/2b0TPDmzoaQ)
* [Slides](https://drive.google.com/file/d/1bn801i0Brs2FypxDyjBIzJyrNYQof80J/view?usp=sharing)

RNNs are analogues of CNN for sequence data.

## Sequence Problems

Either the input, or output or both can be sequence data.

* Time series forecasting
    * Predict the next value given a time series
* Sentiment classification
    * given text, determine sentiment
* Tranlation
* Speech recognition and generation
* Text, music generation
* Question/Answer
  
### Types

Input - > Output

* one to many
  * Input image - > Output text description
* many to many
* many to one
    * use last output of the many to many in RNN

### Why not use feedforward networks?

* Does not handle sequences of arbitrary length
* Would need to learn patterns everywhere they may occur in a sequence. This ignore the temporal nature of the problem

## RNNS

Key idea: stateful computations
o/p depends on input at current time step as well as the (hidden) state from previous step(s)

### Vanishing gradients


### LSTM



## CTC Loss

## Non recurrent sequence algorithms