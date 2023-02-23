---
layout: post
title:  "Coursera - Introduction to Tensorflow - Week 2"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
specialization_url: https://www.coursera.org/professional-certificates/tensorflow-in-practice
course: Introduction to Tensorflow
course_url: https://www.coursera.org/learn/introduction-tensorflow
tags: [Coursera, Intro_Tensorflow] 
---
# Notes from auditing week 2 materials

## Why Fashion_MNIST

"If it doesn't work on MNIST, it won't work at all" VS If it does work on MNIST, it may still fail on others."

## Training vs Test splits: 
60k images from Fashion_MNIST are used as training images and 10k as test.
The test data is used to check the accuracy of a model that has been trained on the training data. The test data has not previously been seen by the model, so it is a good measure of how well the model has been trained.

```python
model = keras.Sequential([
# Fashion MNIST images are 28*28 grayscale. The first layer loads an image and flattens from vector to a linear array of values
    keras.layers.Flatten(input_shape=(28,28)),
# Hidden layer with 128 neurons. We can think of each neuron as a fucntion that takes  the 28*28 = 784 input values from the previous layer and converts it into an output value corresponding to an item in the training dataset. 
    keras.layers.Dense(128, activation=tf.nn.relu),
# There are 10 items in the training set. Hence, the output layer has 10 neurons.
    keras.layers.Dense(10,activation=tf.nn.softmax)
])
```

The loss function is used to calculate how well the model did with a guess in a particular iteration.
The optimzer is used to generate a new guess.
Relu activation throws away negative values

## ReLU

```
if x > 0: 
  return x

else: 
  return 0
```
## Softmax intuition

Softmax takes a list of values and scales these so the sum of all elements will be equal to 1.

[Softmax details](https://www.youtube.com/watch?v=LLux1SW--oM)

```python
# Declare sample inputs and convert to a tensor
inputs = np.array([[1.0, 3.0, 4.0, 2.0]])
inputs = tf.convert_to_tensor(inputs)
print(f'input to softmax function: {inputs.numpy()}')

# Feed the inputs to a softmax activation function
outputs = tf.keras.activations.softmax(inputs)
print(f'output of softmax function: {outputs.numpy()}')

# Get the sum of all values after the softmax
sum = tf.reduce_sum(outputs)
print(f'sum of outputs: {sum}')

# Get the index with highest value
prediction = np.argmax(outputs)
print(f'class with highest probability: {prediction}')
```

* Input to softmax function: [[1. 3. 4. 2.]]
  * In this example, these can be thought of as the values output by a 4 node NN for a classification task, with each node coressponding to a class of item. So, class 0 has value 1, class 2 has value 4 etc.
* Output of softmax function: [[0.0320586  0.23688282 0.64391426 0.08714432]]
* Sum of outputs: 1.0
* Class with highest probability: 2 (i.e the node with the value 4)

## Training vs Testing Accuracy

The accuracy of training is a measure of how well the model performed after a given number of training iterations. So 0.9 means that the network is about 90% accurate in classifying the training data.

The evaluation accuracy is a measure of how well the model performs on unseen data i.e. the test data. It can be expected that the accuracy of training will be higher that the accuracy in evaluation.

## Jupyter Notebooks

* [Notebook - Week 2 - Lab 1 -  Fashion MNIST workbook](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W2/ungraded_labs/C1_W2_Lab_1_beyond_hello_world.ipynb)
* [Notebook - Week 2 - Lab 2 - Using callbacks to control training](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W2/ungraded_labs/C1_W2_Lab_2_callbacks.ipynb)
## Links

* [Fashion MNIST](https://github.com/zalandoresearch/fashion-mnist)
* [Responsible AI practices](https://ai.google/responsibilities/responsible-ai-practices/)