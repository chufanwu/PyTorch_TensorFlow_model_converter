# PyTorch TensorFlow model converter
This work aims to convert a PyTorch pretrained model to TensorFlow and train on TensorFlow environment. It also can convert TensorFlow trained model back to Pytorch.

### Purpose of the project
It is very convenient to load ResNet pretrained model using PyTorch. However, some of the Reinforment Learning based code was written in TensorFlow. We want to load the pretrained PyTorch model to Tensorflow for training. After the training, the model will be saved and convert back to PyTorch model and test on PyTorch environment.


### Differences between PyTorch and TensorFlow implementation
There are several major differences between Pytorch and TensorFlow implementation
- the dimension of images for PyTorch Tensor is `(N, H, W, C)`  but the dim for TensorFlow Tensor and numpy data is `(N, C, H, W)`.
- the dimension of convolutional filters for PyTorch is `(out, in, H, W)` but is `(H, W, in, out)` in TensorFlow.
- the dimension of fully connected layer weight is `(out, in)` in PyTorch but is `(in, out)` in TensorFlow. (if using `tf.matmul` implementation for fc layer)

## the usage of each file

### layers.py
This file defines the basic module using TensorFlow implementation to mimic the PyTorch code.
- padding: 