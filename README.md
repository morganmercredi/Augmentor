# Augmentor

[![License](http://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat)](LICENSE.md) [![Project Status: WIP - Initial development is in progress, but there has not yet been a stable, usable release suitable for the public.](http://www.repostatus.org/badges/latest/wip.svg)](http://www.repostatus.org/#wip) [![PyPI](https://img.shields.io/badge/pypi-v0.1-blue.svg?maxAge=2592000)](https://pypi.python.org/pypi/Augmentor)

Image augmentation library in Python for Machine Learning. A Julia version of the package is also being developed as a sister project and is available [here](https://github.com/Evizero/Augmentor.jl). 

## Usage
The purpose of this package is to automate image data augmentation (artificial data generation) in order to create more samples for machine learning tasks, especially neural networks and deep learning.

The package works by building an augmentation pipeline as a series of operations to perform on a set of images. Operations, such as rotations or transforms, are added piece by piece in order to create an augmentation pipeline, which can then be executed in order to create an augmented dataset.

The package currently consists of two basic building blocks that allow for a pipeline to be built, the `ImageSource` class and the `Pipeline` class.

You start by initialising an `ImageSource` object where you define the source of your images. Then you define a `Pipeline` object that defines what operations you wish to perform on your dataset (defined in your `ImageSource` object).

### The `ImageSource` Class
Defines the source directory or directories where your original images are stored.

```python
summary()
```

### The `ImageDetails` Class
A container which comprises images, paths and other necessary information about the data pointed to.

### The `ImageOperations` Class
Includes mainly the different image operations and therefore the main functionality.

### The `Pipeline` Class
Defines the operations (rotations, mirroring, transforms, etc.) which should be applied to your original dataset. Once a pipeline has been built, the `execute()` method applies the operations to your images.
The currently implemented image manipulation functions are:

```python
addFlipX(chance=1)
addFlipY(chance=1)
addRotate90(chance=1)
addRotate180(chance=1)
addRotate270(chance=1)
addResize(height, width, chance=1)
addScale(height, width, chance=1)
addRotate(degree, chance=1)
addCrop(height, width, chance=1)
addConvertGrayscale(chance=1)
summary()
```

## Installation
__Currently beta. Mileage may vary.__

```python
# Currently testing. Mileage may vary.
pip install Augmentor
```

## Usage

The example can also be found in ```SimpleSample.py```

```python
from Augmentor import Pipeline

## set the path to the folder with images to manipulate
pathToImages = '\home\user\images'

## create pipeline
pipe = Pipeline.Pipeline(pathToImages)

## add function to pipeline
pipe.addFlipY()
pipe.addFlipX(0.6)

## add another function to pipeline
pipe.addCrop(45, 45)

## execute the functions in pipline
pipe.execute()

## all images are created in target folder

## print a summary
pipe.image_source.summary()
```
