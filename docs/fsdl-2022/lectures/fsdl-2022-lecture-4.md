---
layout: post
title: "FSDL-2022-Lecture-4"
date: 2023-02-22
categories: notes
learning_platform: 
specialization: 
course: FSDL
tags: 
---
# Data Management

## Most ML Tools are databses at their core

* [Weights and Biases]() is a database of experiments
* [Hugging Face]() is a database of models
* [Label Studio]() is a database of labels

## Platforms unifying structured and unstructured data

* [Book exploring topic from first principles](https://dataintensive.net/)
* [Snowflake](https://www.snowflake.com/)
* [Databricks](https://www.databricks.com/)

## Data Exploration

* SQL
* Dataframe
  * [Pandas](https://pandas.pydata.org/)
    * [DASK - Parallelise Pandas Operations over cores](https://examples.dask.org/dataframe.html)
    * [RAPIDS - Pandas operations om GPUs](https://rapids.ai/)
  
## Data Processing

Managing task dependencies/run models on schedule using a Directed Acyclic Graph workflow of data operations

* [Airflow](https://airflow.apache.org/)
* [Prefect](https://www.prefect.io/)
* [Dagster](https://dagster.io/)

## Feature stores

* [Uber - Michelangelo](https://eng.uber.com/michelangelo-machine-learning-platform/)
* [Tecton](https://www.tecton.ai/)
* [Feast](https://feast.dev/)
* [Featureform](https://www.featureform.com/)

## Datasets

* [Huggingface datasets](https://huggingface.co/docs/datasets)
* [Activeloop](https://www.activeloop.ai/)

## Data Labelling

* Self supervised learning - models can have elements of data masked and the model can use earlier parts of the data to preidct masked parts
    * [OpenAI-CLIP](https://github.com/openai/CLIP)
* Image data augmentation
    * [Torch Vision](https://github.com/pytorch/vision)
    * [SimCLR](https://ai.googleblog.com/2020/04/advancing-self-supervised-and-semi.html)
* Synthetic data

## Labelling Solutions

* Crowdsourced:
    * [Amazon Mechanical Turk](https://www.mturk.com)

* Full service:
    * [Scale](https://scale.com/)
    * [Labelbox](https://labelbox.com/)
    * [Supervisely](https://supervise.ly/)
    * [Labelstudio](https://labelstud.io/)
    * [Diffgram](https://diffgram.com/)
    * [AquariumLearning](https://www.aquariumlearning.com/)
    * [Scale-Nucleus](https://scale.com/nucleus)
    * [Snorkel](https://snorkel.ai/)

## Data versioning

* [DVC](https://dvc.org/)
