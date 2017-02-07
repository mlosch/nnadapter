# nnadapter
Generic python interface to simplify access to neural networks trained in machine learning libraries such as Caffe and Torch

## What is nnadapter?

NNAdapter is a lightweight interface to deep learning libraries to simplify the creation of analysis toolchains. The focus is on processing images with pretrained image recognition models, manipulating parameters (e.g. to lesion a set of units) as well as reading parameters and output values of arbitrary layers. Hence, no training is supported with the nnadapter-interface.
Currently supported machine learning libraries (backends) are:

- Caffe
- Torch

## Core functionality
The base class defines the following functionality:

- `forward(4d_numpy_tensor)`
    - Process a batch of images.
- `preprocess(list_of_images)`
    - Preprocess a list of images for use with the neural network.
- `get_layers()`
    - Get an ordered dictionary assigning a layer type to each layer name. The order is equal to the sequence of layers within that model.
- `get_layeroutput(layer_name)`
    - After `forward` has been called, get the output of layer with name `layer_name`.
- `get_layerparams(layer_name)`
    - Get the weights and bias parameter of layer with name `layer_name`.
- `set_weights(layer_name, weight_tensor)`
    - Assign new weights to the given layer
- `set_bias(layer_name, bias_tensor)`
    - Assign a new bias to the given layer
    

## Prerequisites

- General
    - numpy (>= 1.11.1)
    - scikit-image (>= 0.12.3)
- Using Caffe as backend
    - [caffe](https://github.com/BVLC/caffe)
    - pycaffe
- Using torch as backend
    - [torch](http://torch.ch)
    - [PyTorch](https://github.com/hughperkins/pytorch) (>= 4.1.1-SNAPSHOT)
    
## How-To

- See the [example notebook](examples/summary_statistics.ipynb) on how to use NNAdapter to calculate summary statistics on pretrained caffe or torch models.