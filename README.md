# vggNet
Implementation of vgg on Tensorflow according to the original paper [1]. 

Batch normalization is added to speed up the training. [3]

Dataset is CIFAR100. Top-1 accuracy is 71.56%. Top-5 accuracy is 91.52%.




## Usage:
### Dataset
Download dataset from the following link. "train" and "test" are the CIFAR100 training dataset and testing dataset respectively. Same as the dataset published at [2].

https://drive.google.com/open?id=1m9Z4TXLoG0FHg4PuBms1yF1TnvmaO7Ov

https://drive.google.com/open?id=1y4pjIpnPUvf1gBn8TdT0sob23npSveDC


### Train vgg16 by yourself
Put the code in the same directory with data and run "python3 vggTrain.py".

### Use pretrained model 
Assuming the code is put in directory ".", please download the following three files and save it in the directory "./vggNet". Then you can run the model by "python3 vggRestore.py".

https://drive.google.com/open?id=1fDZDf7UpsVCn4CGGvI-Jssm3iFQgpyJw

https://drive.google.com/open?id=1ZJm8-6HIDOLBWXBt92MQjUKqWRbq_xpz

https://drive.google.com/open?id=1nXcmco9zrJIkOTQTTa4V3_VbTVajExWI

## Notes on training experience
1. The original paper [1] reported that VGG16 is hard to train. When I first write my code to implement VGG16, this is also observed by myself. The authors used pretrained small models to initialize a larger one. This way needs too much extra human work. Instead of that, I added two components to solve this problem: batch normalization [3] & xavier initialization [4]. After I added the two components mentioned above, the training process can proceed smoothly.

2. Another problem that I encountered is the order of batch normalization and relu. If I use the order conv-relu-batchNormalization, the accuracy would be 63%. Keeping everything else same and only changing the order to be conv-batchNormalization-relu, the accuracy would increase to 71.56%.

------------------------------------

[1] Very Deep Convolutional Networks for Large-Scale Image Recognition

[2] https://www.cs.toronto.edu/~kriz/cifar.html

[3] Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift

[4] Understanding the difficulty of training deep feedforward neural networks
