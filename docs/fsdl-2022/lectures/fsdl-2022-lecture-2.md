---
layout: post
title: "FSDL-2022-Lecture-2"
date: 2023-02-22
categories: notes
learning_platform: 
specialization: 
course: FSDL
tags: 
---
# Development Infrastructure and Tooling

* [nbdev - Writing tests on Jupyter notebooks](https://nbdev.fast.ai/)
* [streamlit - Building Python web apps interactively](https://streamlit.io/)
  
## Frameworks for ML/AI

* [Pytorch](https://pytorch.org/)
    * The dominance of Pytorch (as of 2022)
        * https://www.assemblyai.com/blog/pytorch-vs-tensorflow-in-2022/
        * https://blog.mlcontests.com/p/winning-at-competitive-ml-in-2022?s=w
    * [Pytorch Lightning](https://www.pytorchlightning.ai/) 
* [Tensorflow](https://www.tensorflow.org/)
* [Jax](https://github.com/google/jax)
    * Deep Learning Libraries for JAX
      * [Haiku](https://github.com/deepmind/dm-haiku)
      * [Jax](https://github.com/google/flax)

## Meta Frameworks and Model zoos
  * [Onyx - Open standard for deep learning models](https://onnx.ai/)
  * [Hugging Face](https://huggingface.co/)
  * [TIMM - collection of CV models](https://github.com/rwightman/pytorch-image-models)

## Distributed Training

There are different scenarios depending on 
* whether data fits on a single GPU or not
* the model parameters fit on a single GPU or not

### When model fits on single GPU

#### Data parallelism

* [Using the Pytorch Distributed Data Parallel Library ](https://pytorch.org/tutorials/intermediate/ddp_tutorial.html)
* [Horovod](https://github.com/horovod/horovod)

https://www.reddit.com/r/MachineLearning/comments/hmgr9g/d_pytorch_distributeddataparallel_and_horovod/

### When the model does not fit on a single GPU

#### Sharded Data Parallelism

What takes up GPU memory?

* The model parameters that make up model layers
* The gradients needed to do back-propagation.
* The optimizer states include statistics about the gradients
* and, a batch of data for model development.

Sharded data parallelism shards model parametersm gradients and optimzer states, meaning that large batch sizes can be used. Examples are

* [Microsoft Zero](https://arxiv.org/pdf/1910.02054.pdf)
  * https://www.microsoft.com/en-us/research/blog/zero-deepspeed-new-system-optimizations-enable-training-models-with-over-100-billion-parameters/


Shared data parallelism is mplemented by:
* [Microsoft Deepspeed](https://github.com/microsoft/DeepSpeed)
* [Facebook Fairscale](https://github.com/facebookresearch/fairscale)
  * [Fairscale CPU offloading - Zero principle on a single GPU](https://fairscale.readthedocs.io/en/stable/deep_dive/offload.html)
* [Pytorch Fully-sharded data parallel](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/)

#### Pipelined Model Parallelism

This approach puts each layer on each GPU. However, this approach means that only one GPU is active at any
given time.

#### Tensor-parallelism

This approach distributes matrix multiplications across multiple GPUs.

* [NVidia Megatron-LM repo for the tranformer model](https://github.com/NVIDIA/Megatron-LM)

#### Combine all 3 options

* [Bloom](https://huggingface.co/blog/bloom-megatron-deepspeed)

### Resources to speed up model training

* [Deepspeed](https://www.deepspeed.ai/training/)
* [MosaicML](https://www.mosaicml.com/)
* [FFCV](https://ffcv.io/)

## Compute

### GPU benchmarks

* [Lambda Labs GPU benchmarks](https://lambdalabs.com/gpu-benchmarks)
* [AIME](https://www.aime.info/en/blog/deep-learning-gpu-benchmarks-2021/)

### Startups that provide GPU access

* [Paperspace](https://www.paperspace.com/)
* [Coreweave](https://www.coreweave.com/)
* [Lambda Labs](https://lambdalabs.com/)

### Comparing the cost of GPU access

[FSDL tool](https://fullstackdeeplearning.com/cloud-gpus/)

Insight: "the most expensive per hour chips are not the most expensive per experiment!"

## Resource Management

* [SLURM workload management](https://slurm.schedmd.com/documentation.html)
* [Managing ML projects with Docker + Kubernetes -> Kubeflow](https://www.kubeflow.org/)

#### End to end solutions for cluster/compute management

* [AWS Sagemaker](https://aws.amazon.com/sagemaker/)
* [Anyscale](https://www.anyscale.com/)
  * [Ray](https://github.com/ray-project/ray)
  * [Ray Train](https://docs.ray.io/en/latest/train/train.html)
* [Grid.ai](https://www.grid.ai/)
  * Uncertain future?
* [Determined.ai](https://determined.ai/)

## Experiment and model management

* [TensorBoard](https://www.tensorflow.org/tensorboard)
* [MLFlow](https://mlflow.org/)
* [Weights and Biases](https://wandb.ai/site)
  * [Hyperparameter Sweeping](https://wandb.ai/site/sweeps)
* [Nepture AI](https://neptune.ai/)
* [Comet ML](https://www.comet.ml/)
* [Determined AI](https://determined.ai/)

## All in One solutions

* [Graident](https://www.paperspace.com/gradient)
* [Domino Data Lab](https://www.dominodatalab.com/)
* [AWS Sagemaker](https://aws.amazon.com/sagemaker/)