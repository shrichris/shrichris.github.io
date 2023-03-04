---
layout: post
title:  "Conda Notes"
date:    
categories: notes
tags: [conda]
---
# Init a repo with conda 

Setup a new repo for local development with conda

Workflow:

* Initiate a repo (nothing to do with conda - just makes things slightly easier)
    * create a new repo on github
    * clone repo
    * navigate into repo directory
* create a new conda env within the dir

```bash
conda create --prefix envs  
```

* activate environment

```bash
conda activate ./envs
```

* install stuff  

```bash
conda install pip
pip install mkdocs-material
```

* list conda environments

```bash
conda info --envs
```

* generate an environments file 

```bash
conda env export > environment.yml
```

* create an environment from an environment file

```bash
conda env create -f environment.yml
```
