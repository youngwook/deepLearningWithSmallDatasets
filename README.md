# Deep Learning With Small Datasets
lean how to train small Datasets with CNN of Deep Learning
# Training Options
1. Data augmentation: it is a method of generating more training data from existing training samples. 
2. Use pre-trained network:it is generally pre-trained and stored networks of large data sets for large-scale image classification problems.
  1. Feature extraction with pre-trained network
  2. Fine tune your pre-trained network
## Environment Requirements
#### Using Virtual Machine
Develop Environment:
- OS: Ubuntu 14. 04 desktop 64
- Memory: 4GB=4096MB
- Hard disk: 100GB
- Network: bridge
- Software: 
  - tensorflow(CPU)
  - pip: python package installer
- Libraries:
  - Anaconda distribution of python, keras, tensorflow, os, shutil.
  
## Datasets
#### Datasets: web site [Kaggle](https://www.kaggle.com/c/dogs-vs-cats-redux-kernels-edition/data). 
- Training data: 25000 image.
- Test data: 12500 image. 
#### Datasets [pre-processing ](https://github.com/youngwook/deepLearningWithSmallDatasets/blob/master/Database-cat-dog-exam1.ipynb).
- make directories to store the data get from original datasets of kaggle.
- Training data 2000 (1000 cats, and dogs each), Test data 1000 and Validation data 1000.

## [Train data with a small dataset without using any regulatory measures to identify overfitting](https://github.com/youngwook/deepLearningWithSmallDatasets/blob/master/CNN-cat-dog-exam2.ipynb)
#### Data pre-processing(Read data from directory): 
1.The data is saved as a JPEG file in the folder and must be read.
2. Decode JPEG as RGB pixel value
3. Switched image size to 150 * 150. 
4. Converts to a floating point tensor and scales the pixel value from 0 to 255 to a scale of 0 to 1.

#### Generate model:
1. Composite convolution layer composed of Conv2D (relu activation function) and MaxPooling2D layer.
2. this is binary classification of cats and dogs, Therefore ends with dense layer with one node and sigmoid activation function.

#### Result of model:
1. Steps_per_epoch: Specifies how many data to enter in one epoch (as the batch size is 20, it is set to 100 to input 2000 data).
2. Epochs is Repeat count.
3. Result Demonstrate the nature of overfitting. Training accuracy increased linearly, but verification accuracy stopped at a certain position. While training losses continue to decline, validation losses also stopped at some point.

## [Data augmentation](https://github.com/youngwook/deepLearningWithSmallDatasets/blob/master/CNN-cat-dog-exam3.ipynb)
#### Data pre-processing: 
1. Read data from directory: When data is read from a directory, the data augmentation technique is used to transform the data.
2. Image conversion method
- Photo rotation : rotation_range is used to rotate pictures randomly.
- Horizontally and vertically shift photos : width_shift_range, height_shift_range are used to shift photos. 
- shearing transformation: shear randomly. 
- Enlarge photo : zoom_range is uded to enlarge photos randomly. 
- Flip image horizontally : horizontal_flip is used to flip image horizontally. 
- Pixel fill : fill_mode is used to specify how to fill the empty space due to rotation or horizontal / vertical movement. 

#### Generate model:
- The dropout layer is added to the fully-connected layer to suppress overfitting once again (since the image is read from the original, there is a high correlation between the input data).
#### Result of model:
1. Steps_per_epoch: Specify how many data to enter in one epoch (no need to fit the original size as the data is changed and entered).
2. Overfit disappears due to data propagation and dropout. Training and validation show similar curves.

## Use pre-trained network(Feature extraction)
#### [Use pre-trained convolution layer predict function to extract features](https://github.com/youngwook/deepLearningWithSmallDatasets/blob/master/Database-cat-dog-exam4.ipynb)
###### Generate model: 
1. The extracted feature is converted into a 1D vector to enter the fully connected layer.
2. Use dropout for overfitting. 
###### Result of model:
- High accuracy has been reached, but shows overfit characteristics.

####  [Replace the convolution layer with pre-trained one](https://github.com/youngwook/deepLearningWithSmallDatasets/blob/master/Database-cat-dog-exam5.ipynb)
###### Generate model:
1. Frozen convolution layer: Prevent weights from being updated while training.
2. Enter training data with data augmentation method. 
###### Result of model:
- Overfitting has been significantly reduced.

## [Use pre-trained network(Fine tune)](https://github.com/youngwook/deepLearningWithSmallDatasets/blob/master/Database-cat-dog-exam6.ipynb)
#### Generate model:
Fine tune only the top two or three layers of the convolution layer.
#### Result of model:
Overfitting has been significantly reduced.




######for github syntax [fefer to](https://guides.github.com/features/mastering-markdown/)
