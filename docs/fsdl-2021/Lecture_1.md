# Lecture 1: Deep Learning Fundamentals

* [FSDL Page](https://fullstackdeeplearning.com/spring2021/lecture-1/)
* [Video](https://youtu.be/fGxWfEuUu0w)
* [Slides](https://drive.google.com/file/d/1Cc3oN9gQSTYPmT7HC7UDaeFXiyJuQwq_/view?usp=sharing)

## Mathematical model of a neuron

* Axons: Input(s) x_i (axon_i from a neighbouring neuron)
* Synapse: Weights w_i
* Cell body: 
    * sums input(s) w_ix_i and add a bias b
    * Output is determined by the activation function which determines whether the neuron "fires" or not.

## Activation Functions:

* Sigmoid
* Hyperbolic Tangent
* ReLU
 
## Universality of neural networks: 

Hornik's Theorem - Any continuous function can be approximated with a 2-layer neural networks with enough hidden units

* Exlore [interactively](http://neuralnetworksanddeeplearning.com/chap4.html)

## Types of learning

* Supervised  
    * Learn X given X->Y
* Unsupervised
    * Learn X 
* Reinforcement
    * Learn to interact with an environment

## Unsupervised Learning examples

* Predict next character (charRNN - Andrej K)
    * Radford et al - 2017
* Predict "nearby" words (word2vec)
    * Mikoloc et al - 2013
 * Predict next pixel (pixelCNN)
    * van den oord et al - 2016
* Variational Autoencoders (VAE) - Encode image down to  latent vector/variables and then decode back - used to learn complex images from compressed representations
    * Kigma and Welling - 2014
* Generative Adversarial Networks - use a latent image to generate x that is indistinguishable from real
    * Goodfellow et al - 2015
### Linear Regression - line fitting

Can be thought of a prediction problem - Given a number of inputs X and outputs Y, what is the output corresponding to a new X we have not seen before

 Achieved by fitting a line which is in turn achieved by finding parameters w and b for a line (y = wx + b) that minimize (optimizing) the squared error loss function (min_w_b(sum(wx_i + b =y_i)^2))

### Loss functions examples

* Mean Squared Error (MSE)
* Cross Entropy Loss

### Optimizing loss functions - gradient descent

All "learning" can be thought of as the problem of optimization loss functions

* choose weights randomly
* calculate the gradient (derivative) of the loss function with respect to chosen weights, using the observed measurements
* update weights by subtracting (learning rate * gradient) from current weight
* repeat

### Stochastic/Batch Gradient Descent

Essentially computing each gradient step on subsets of the data.

* noisy
* more efficient

## Encoding data in neural networks

* Computer Vision: Convolutional Neural Networks - leverage "spatial translation invariance" (objects look similar as we move through space)
* Natural Language Processing (sequence processing more generally): Recurrent Neural Networks - leverage "temporal invariance" (the rules of language do not change depending on where we are in a sentence)

## Links
* [Neural Networks Book](http://neuralnetworksanddeeplearning.com)
    * [Backpropagation](http://neuralnetworksanddeeplearning.com/chap2.html)
* [This X does not exist](https://thisxdoesnotexist.com/)
