# Lecture 2a: CNNs

* [FSDL page](https://fullstackdeeplearning.com/spring2021/lecture-2a/)
* [Video](https://youtu.be/hO3kOdShwsI)
* [Slides](https://drive.google.com/file/d/1Q1T2P6Jzvo1_Z3hGvRmXPYAvwg_bvwPB/view?usp=sharing)

## Naive implementation of image classification for classification

For a 32*32 image, with 10 possible labels, the naive approach is to have a fully connected network:

* flatten the image into a matrix with 1024 columns 
* apply matrix multiplication on a 1024*10 matrix of weights to learn 10 classes.
    * (1 * 1024) * (1024 * 10) - > (1 * 10)

This approach: 

* scales poorly with the size of the input image - extremely inefficient
    * for a 64*64 image - 4 times as many weights as for 32* 32
    * for a 128*128 image - 16 times as many weights as for 32*32
* learns weights for every single pixel in the input image - overkill!
    * not all pixels contribute the key features that identify a class
* will not be invariant to transformations of the input image e.g. to scaling of the input image

## CNNs

Convolutions of the input image apply convolution filters of a given size (say 5*5) and slide this over the image. The (5*5) output of the filter can be flattened, and matrix multiplication applied on a much smaller matrix to learn a single output coresponding to a specific filter location.

### Input channels
For RGB images, the filter is applied to every channel. The size of the flattened input of the filter location will be 3 times that of the  grayscale case.

### Output channels

Multiple convolutional filters can be applied, to produce multiple output channels

### Stacking convolutional layers

Convolutional layers can be stacked in layers. In practive each convolutional layer will be followed by an activation layer to introduce non linearity

### Strides

Instead of sliding the filter pixel by pixel, a stride can be applied. This "skips" some locations ans is an approach to 'subsample' large input images

Typically strides are the same on both x and y dimensions.
### Padding

Padding with default values (usually 0) is applied to the edges of the image so that filters don't fall off the edges of the image.

* SAME padding - most common
* VALID padding is, confusingly, no padding 

### The art of determining the size of each output layer in a Neural network

Input: 

* (W*H*D) volume

Parameters:

* K filters, (F,F)
* Stride, (S,S)
* Padding P

Output:

  * W' = (W-F+2P)/S + 1
  * H' = (H - F +2P)/S + 1

Number of Paramters:

* Each filter has (F*F*D) parameters
* Total parameters at at layer = K*F*F*D)

## Insight

Hyperparameters such as strides and padding are are typically not "learnable" as the effects of changes in padding, cannot be pre-determined - they are not differentiable and cannot be learnt in inner loop of the learning process using standard gradient descent.

Meta learning - using an outer loop to select hyper parameters.

## Implementation notes

### Receptive Fields 

The "receptive field" is the portion of an input image that contributed to the output of a filter.

The receptive field can be increased by:

* stacking convolutions
    * stacking smaller sized filters typically performs better than using fewer larger filters
* using dilated convolutions can be used to "see" a large portion the the image by skipping pixels e.g. a (3*3) filter can have a (5*5) receptive field
* decreasing size of output tensor
    * Pooling 
        * sub-sampling a portion and applying an operation to reduce its size. Approaches include taking
            * Average of pixels
            * Max of pixels
                * (2*2) max pooling is the most common pooling option
        * less common to see with advances 
    * (1*1) convolution
        * Decreases number of channels in the tensor
        * Used in GoogleNet/inception

## CNN architecture

Notation: _n refers to the number of times the set of operations is performed

### LeNET

* ((Conv -> Non Linear (ReLu/tanh))_n -> Max pooling)_m -> (Fully conected layers)_l -> ReLU -> SoftMax
    * Non linearities are typically applied between the fully connected layers
    * There is typically no non-linearity after the very last fully connected layer (as loss functions expect as input, the output of a fully connected layer)

## Links
* [Image Kernels explained visually](https://setosa.io/ev/image-kernels/)
* [Guide to convolution arithmetic for DL](https://github.com/vdumoulin/conv_arithmetic)
* [Introduction to neural Style Transfer](https://towardsdatascience.com/a-brief-introduction-to-neural-style-transfer-d05d0403901d)
* [Improving how neural networks learn](http://neuralnetworksanddeeplearning.com/chap3.html)