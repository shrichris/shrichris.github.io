# Lecture 3: RNN

* [FSDL page](https://fullstackdeeplearning.com/spring2021/lecture-3/)
* [Video](https://youtu.be/2b0TPDmzoaQ)
* [Slides](https://drive.google.com/file/d/1bn801i0Brs2FypxDyjBIzJyrNYQof80J/view?usp=sharing)

RNNs are analogues of CNN for sequence data.

## Sequence Problems

### Examples of Sequence Problems

Either the input, or output or both can be sequence data.

* Time series forecasting
    * Predict the next value given a time series
* Sentiment classification
    * given text, determine sentiment of the text
* Translation
    * given text in one language, output text in another language
* Speech recognition and generation
    * given input audio, output the transcript
* Text, music generation
* Captioning
* Question/Answer 
### Types of sequence problems

Input - > Output

* one to many
    * Input image - > Output text description
* many to many
    * Most general case. Where the goal is to produce an output at every step (for every input in the sequence)
* many to one
    * use last output of the many to many in RNN

### Why not use feed-forward networks?

* Does not handle sequences of arbitrary length well
    * could pad sequence to max length allowed
    * memory requirement will scale linearly in the number of timesteps - undesirable scaling property
* Would need to learn patterns everywhere they may occur in a sequence. This ignores the temporal nature of the problem.

## Sequence Architectures
### RNNs 

* Core idea of RNNs: Stateful computations
    * o/p depends on input at current time step as well as the (hidden) state from previous step(s)

#### Encoder/Decoder Architecture

* Encoder maps input to a vector/hidden state
* Decoder maps vector to output* Not parallelizable - slow in practice
* Flexible architecture that works for all types of sequence problems.

    * Many to one:
        * Encoder: RNN for text input
        * Decoder: Fully Connected

    * One to many:
        * Encoder: CNN for image input
        * Decoder: RNN for text output

    * Many to Many:
        * Encoder: RNN for character input sequences
        * Decoder: RNN for character input sequences
    
Thinking in terms of encoder and decoder architectures is a useful mental model only. In practice, they are not separate in any meaningful sense. The back-propagation propagates through the decoder and encoder portions of the network
#### Problems with vanilla RNN architectures

*  All information in input sequence (regardless of its size) is condensed to a single hidden state vector of a pre-determined dimension, on which the decoder operates.
*  Vanishing gradients:
      *  activation function such as sigmoid and tanh have derivatives <<1 near saturation. At each step, the magnitude of the gradients tends to decrease and after enough steps, the gradients could be so small that  they have "vanished"
* Exploding gradients:
    * problem with ReLU 

**To do** : Review Back-propagation through time
- unroll graph before performing back propogation steps

### LSTM architecture

The architectures used in practice to get around the problems associated with vanishing gradients. This is achieved by using a "cell state" that is propagated through the network.

* Forget gate:
    * decide which parts of old state to forget
* Input gate:
    * decide which new information to introduce into cell state
* Output gate:
    * produce the hidden state to be used at the next time step 

### Comparison of architectures - Studies may appear inconclusive

* Literature comparing sequence model architectures
    * [A Search Space Odyssey, Gref er al.]
        * Compared 9 variants, using 3 datasets
        * Cannot beat LSTM
    * [An empirical Exploration of RNN architectures, Josefowicz, Zaremna, Sutskever]
        * compared 10k architectures!
        * GRU is the best

Conclusion (FSDL):

* LSTM work well for most tasks
* Try GRU if LSTMs dont perform as well as expected

### LSTM problems and some innovation in Google Machine Translation approach (2016)

* Stacked LSTMs to improve learning
* Hard to train for very deep (>4) stacks of LSTMs
    * Sol: Skip connections
* Lots of information stacked in last time step
    * Sol: Attention: Give neural network access to the entire history to enable longer-term connections
    * For machine translation, relevance scores assigned to individual words in the input sequence
Also has applications in audio (e.g transcription) and image (e.g. captioning)
* Only consider backward context
    * Understanding how a sentence unfolds can depend on information that appears in the future.
    * Sol: Bi-directionality: Use one LSTM to process the sequence in the forward order and another in the backward order.

## CTC Loss algorithm

When attempting to convert (decipher :) handwritten text in image format, a convnet + LSTM architecture can be used to convert segments of the image to text. However, this approach is sensitive to common issues such as the scaling if the input image, which may result in repeated characters.

Sol: Combines repeating characters, with tokens to cater for expected repeating characters

* [Connectionist Temporal Classification](https://distill.pub/2017/ctc/)

## Non recurrent sequence algorithms

* Wavenet 
  * uses convolutions  
  * Wavenet (trained on internal Google datasets) 
  * uses a window of hidden layers, going all the way down to the input data
  * 1d causal convolutions - windows of inputs only in past
  * dilated convolutions to increase the receptive field (to look at wider array of inputs)
  * inherrently parallel in training
  * slow inference time - mitigated with parallel wavenet
* Transformer architecture
  * Since 2019, almost all sequence algorithms have been replaced by the Transformer architecture

## Links

* [The Unreasonable Effectiveness of Recurrent Neural Networks](http://karpathy.github.io/2015/05/21/rnn-effectiveness/)
* [When Recurrent Models Don't Need to be Recurrent](https://bair.berkeley.edu/blog/2018/08/06/recurrent/)
* [Attentional-Interfaces](https://distill.pub/2016/augmented-rnns/#attentional-interfaces)
* Visualising attention.
    * [Attentional-Interfaces](https://distill.pub/2016/augmented-rnns/#attentional-interfaces)
    * [Attention-Vis](https://lilianweng.github.io/lil-log/2018/06/24/attention-attention.html)
* [Connectionist Temporal Classification](https://distill.pub/2017/ctc/)
* [Attention Craving RNNs: Building Up To Transformer Networks](https://towardsdatascience.com/attention-craving-rnns-a-journey-into-attention-mechanisms-eec840fbc26f)