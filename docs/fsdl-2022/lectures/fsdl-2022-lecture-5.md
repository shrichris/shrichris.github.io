---
layout: post
title: "FSDL-2022-Lecture-5"
date: 2023-02-22
categories: notes
learning_platform: 
specialization: 
course: FSDL
tags: 
---
# Deployment

## Build a prototype / Separate your model and UI

* [Huggingface](https://huggingface.co/)
* [Gradio](https://gradio.app/)
* [Streamlit](https://streamlit.io/)
  
## Separate your model and UI

### Batch Prediction - Run model on each data point and store results in a database

* See [Data processing - Lecture 4](fsdl-2022-lecture-4.md)
* [Metaflow](https://metaflow.org/)

### Model as a service - Run the model as a separate service

### API

* REST
* GRPC
* GraphQL

## Learn the tricks to scale

## Consider moving your model to the edge when you really need to go fast


## Dependency Management

* [Docker]()
    * [Cog](https://github.com/replicate/cog)
    * [BentoML](https://github.com/bentoml/BentoML)
    * [Truss](https://github.com/trussworks)

## Monitoring Performace

* [Example FSDL Project](https://fullstackdeeplearning.com/course/2022/project-showcase/#full-stack-stable-diffusion)
    * [Inference - Triton](https://developer.nvidia.com/nvidia-triton-inference-server)
    * [Monitoring - Prometheus](https://en.wikipedia.org/wiki/Prometheus_(software))
    * [Analytics - Grafana](https://en.wikipedia.org/wiki/Grafana)

## Performance Optimization

Revisit later

## Edge deployment

* [Nvidia - TensorRT](https://developer.nvidia.com/tensorrt) 
* [Android - MLKit](https://developers.google.com/ml-kit)
* [iOS - CoreML](https://developer.apple.com/documentation/coreml)
* [ios and Android/Python](https://pytorch.org/mobile)
* [Tensoflow - TFLite](https://www.tensorflow.org/lite)
* [Browser - Tensorflow JS](https://www.tensorflow.org/js)
* [Target device agnostic - Apache TVM](https://tvm.apache.org/)

### Startups:

* [MLIR](https://mlir.llvm.org/)
* [OctoML](https://octoml.ai/)
* [TinyML](https://www.tinyml.org/)
* [Modular](https://www.modular.com/)
