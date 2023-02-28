---
layout: post
title: "FSDL-2022-Lab-O-overview"
date: 2023-02-22
categories: notes
learning_platform: 
specialization: 
course: FSDL
tags: 
---



# The FSDL App

* [Lab Overview - FSDL](https://fullstackdeeplearning.com/course/2022/lab-0-overview/)
* [Setup instructions](https://github.com/full-stack-deep-learning/fsdl-text-recognizer-2022-labs/tree/main/setup#colab)
* [Lab Overview - Colab](https://colab.research.google.com/github/full-stack-deep-learning/fsdl-text-recognizer-2022-labs/blob/main/overview.ipynb)
* [The deployed FSDL text recognizer application](https://fsdl-text-recognizer.ngrok.io/)
* [repo for the FSDL text recognizer application](https://github.com/full-stack-deep-learning/fsdl-text-recognizer-2022)
* [repo for the labs](https://github.com/full-stack-deep-learning/fsdl-text-recognizer-2022-labs)

## Tech Stack:

* Model Serving 
    * [Ingress as a service](https://ngrok.com)
    * [Frontend Library - Gradio](https://gradio.app/)
    * Model is wrapped in a [Docker](https://docker.com/) container
    * Model is deployed serverlessly using [AWS Lambda](https://aws.amazon.com/lambda/)
    * The container image lives in Amazon's [Elastic Container Registry](https://aws.amazon.com/ecr/)
* Monitoring
    * [Monitoring Model Performance](https://gantry.io/)
* Model Training
    * [Lambda Labs GPU](https://lambdalabs.com/service/gpu-cloud)
    * [The Pytorch Library](https://pytorch.org/) provides GPU accelerated array math and fucntionality for model training
    * [The Pytorch Lightning Library](https://pytorch-lightning.readthedocs.io/en/stable/) provides the framework for training models using Pytorch.

## Tutorials:

  * [Docker Tutorial](https://docker-curriculum.com/)
  * [What is serverless](https://sst.dev/chapters/what-is-serverless.html)
  * [Convert Pytorch Models to Pytorch Lightning ](https://www.youtube.com/watch?v=QHww1JH7IDU)

## Experiment and artefact Tracking

* [Weights and Biases](http://docs.wandb.ai/) stores
  * PyTorch lighting checkpoits that can be used to restart model training if interrupted. This enables used of chepaer [preemptible cloud instance](https://www.determined.ai/blog/scale-your-model-development-on-a-budget). These are essentially excess capacity that a cloud provider has which can be utilised, with the caveat that resources can be pre-empted (allocated away at the cloud provider's will)
* deployed model files

## Model Handoff to production

* Pytorch lightning models are compiled down to a dialect of Torch called [torchscript](https://pytorch.org/docs/stable/jit.html)
  
