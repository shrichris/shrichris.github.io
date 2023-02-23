---
layout: post
title:  "Coursera - Introduction to Tensorflow - Week 1"
date:   2023-02-09 
categories: notes
learning_platform: [coursera, deeplearning.ai]
specialization: DeepLearning.AI TensorFlow Developer Professional Certificate
specialization_url: https://www.coursera.org/professional-certificates/tensorflow-in-practice
course: Introduction to Tensorflow
course_url: https://www.coursera.org/learn/introduction-tensorflow
tags: [Coursera, Intro_Tensorflow] 
---
# Notes from auditing week 1 materials

## Insights

In traditional programming, a programmer has to formulate or code rules manually, whereas, in Machine Learning, the algorithm automatically formulates the rules from the data.

The Traditional Programming Paradigm
```
(Rules, Data) -> Answers
```

The Machine Learning Paradigm
```
(Answers/Labels, Data) -> Rules
```
## Coding the "Hello World" of Deep Learning with Neural Networks in Tensorflow

to figure out the relati  onship between x and y, given a training set with a small number of data points.

```python
import tensorflow as tf
import numpy as np
from tensorflow import keras
print(tf.__version__)

## Build a simple Sequential model
model = tf.keras.Sequential([keras.layers.Dense(units=1, input_shape=[1])])

## Compile the model
model.compile(optimizer='sgd', loss='mean_squared_error')

## Declare model inputs and outputs for training
xs = np.array([-1.0,  0.0, 1.0, 2.0, 3.0, 4.0], dtype=float)
ys = np.array([-3.0, -1.0, 1.0, 3.0, 5.0, 7.0], dtype=float)

## Train the model
model.fit(xs, ys, epochs=500)

## Make a prediction
print(model.predict([10.0]))
```
## Jupyter Notebooks

* [Notebook - Week 1 - Lab 1](https://github.com/https-deeplearning-ai/tensorflow-1-public/blob/main/C1/W1/ungraded_lab/C1_W1_Lab_1_hello_world_nn.ipynb)

## Links

* [Lecture Notes for this course](https://community.deeplearning.ai/t/tf1-course-1-lecture-notes/124222)
* [Tensorflow Playground](http://playground.tensorflow.org/)
  * [Repo for the Tensorflow Playground](https://github.com/tensorflow/playground)
  * [Convnet Demo - Andrej Karpathy](https://cs.stanford.edu/people/karpathy/convnetjs/demo/classify2d.html)
  * [Book: Neural Networks and Deep Learning, Michael Nielson](http://neuralnetworksanddeeplearning.com/index.html)
  * [Book: Deep Learning, Ian Goodfellow, Yoshua Bengio, and Aaron Courville.](https://www.deeplearningbook.org/)
  