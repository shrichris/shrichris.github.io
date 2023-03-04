# Lecture 2b: Computer Vision Architectures

* [FSDL page](https://fullstackdeeplearning.com/spring2021/lecture-2b/)
* [Video](https://youtu.be/rHGUVo6GjVA)
* [Slides](https://drive.google.com/file/d/1cnDRkRqNwZJtlJLZB-JwDQcm4Yybw6a3/view?usp=sharing)

## Imagenet

[Imagenet](https://image-net.org) is a Large Scale Visual recognition challenge running since 2010.

* 1.2M images
* 1000 categories
* task - classification (but also localization and detection)

## Convnet Architectures for image recognition
### AlexNet

Alexnet's performance on Imagenet challenege in 2012 using a deep neural network launched the CNN revolution
Progress since then tracked by ImageNet winners

Similar to LeNet - Introduced many innovations:

* ReLU
* Dropout
* Data augmentation

### ZFNet

Very similar to AlexNet. Introduced "deconvolutional visualizations"

* Each filter can be thought of as detecting an image patch. Paper introuced visualisations to show how detection becomes more specific

### VGG

Simple deep architecture. 

Innovation:

* Stacking smaller convolutional filters to increase receptive field with fewer parameters

### GoogleNet/Inception

As deep as VGG but with 3% parameters

* No fully connected layers
* Stack of inception modules which are different to the standard(conv-relu-conv-relu-pool) module.
* classification outputs at different portions of the network. 
#### Inception module

Inputs go through different filters or pooling simultaneously and the outputs get concatenated.

### ResNet

* Very deep architecture with 152 layers
* Most commonly used now
* Lowered error rate below human performance
* Authors observed that deeper models should be able to perform as well as shallower networks of same architecture, but don't due to vanishing gradients

Innovation:

* If a layer makes the gradient vanish, then skip around the layer by adding shortcuts 

#### ResNet variants

* DenseNet
    * Multiple skip connections
* ResNeXt 
    * combines inception and resent
* SENet
    * Adds a module of global pooling and fully connected layer to adaptively reweigh feature outputs maps

### SqueezeNet

Alexnet accuracy with 50x fewer parameters

## Comparision of architectures

[DawnBecnh](https://dawn.cs.stanford.edu/benchmark/)

## Applications

* classification
    * output the class of the image
* localization
    * Show where object is, in an image
* detection 
    * output every object's class and locations
* segmentation
    * label every pixel belonging to an object
* instance segmentation
    * differentiate objects of the same class

### Classification
### Localization

Predict bounding box co-ordinates as well as class using the same network
    * does not scale for detection of multiple objects
### Detection 

* slide a classifier over the image at multiple scales
    * very computationally expensive

Non Maxing Suppression:
When bounding boxes overlap, keep the one with the highest score.

* Overfeat 2013, used apprach of turning FC layers into convolutional layers
* YOLO/SSD ,utiple versions
    * You only look once, Single shot detection
    * Multiple versions, evaluated against Microsoft CoCo common objects in context, which is a large scale object detecttion, segmentation and captioning dataset.

#### Region proposal methods

Look only at and classify interesting portion of an image

* Region-CNN
* Faster R-CNN
* RPN
* Mask R-CNN
* uNet / Fully convolutional nets
### Segmentation

* label every pixel belonging to an object
* instance segmentation
    * differentiate objects of the same class

### Mesh RCN - predicts 3D mesh of a 2D image

* [Shapenet](https://shapenet.org)
### Facial Landmark Detection

* [Annotated faces in the wild](https://www.tugraz.at/institute/icg/research/team-bischof/lrs/downloads/aflw/)
* [Papers with code](https://paperswithcode.com/sota/face-detection-on-annotated-faces-in-the-wild)

### Pose estimation

* [Microsoft COCO](https://cocodataset.org/#home)

## Adverserial attacks on CNNs

* White box - with access to model parameters
* Black box - without access to model parameters

Examples:

* Panda -> Gibbon example - by ingroducing weel crafted "noise"
    * [Explaining and Harnessing adverserial examples](https://arxiv.org/abs/1412.6572)
* Pictures of real world physical objects that mess up models]
    * [Robust Physical-World Attacks on Deep Learning Visual Classification](https://openaccess.thecvf.com/content_cvpr_2018/papers/Eykholt_Robust_Physical-World_Attacks_CVPR_2018_paper.pdf)

Attack:

* Some form of modifying the input in the direction of the loss gradient

Defence:

* Training with adversarial examples - not very effective in practice
* Smooth class decision boundaries: Defensive distillation - train second NN that learns to provide the same output as a nn without seeing the raw data ??
## Style Transfer

## GANs

Produce life like fake images

## Links

* [Torchvision.models](https://pytorch.org/vision/0.8/models.html)
* [DawnBench](https://dawn.cs.stanford.edu/benchmark/)
* [Microsoft COCO](https://cocodataset.org/#home)
* [ShapeNet](https://shapenet.org)
* [Annotated Faces in the wild](https://www.tugraz.at/institute/icg/research/team-bischof/lrs/downloads/aflw/)
* [Papers with code](https://paperswithcode.com/sota/face-detection-on-annotated-faces-in-the-wild)
