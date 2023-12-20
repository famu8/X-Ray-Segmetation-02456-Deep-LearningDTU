# U-Net architecture 

U-Nets are Convolutional Neural Networks (CNNs) whose structure follows a characteristic \textit{U} shape, conferred by the contracting and the expansive symmetric paths. The contracting path initiates with a series of convolutions alternated with max-pooling layers. This process reduces spatial dimensions and augments the number of feature maps, taking the network to its bottleneck, where the input is represented as a 1-D vector.

The expansive path operates in reverse, employing alternating convolutional and up-convolutional layers to increase spatial dimensions and decrease feature map numbers, ultimately restoring the input to its original shape. The final layer has a softmax activation function, which assigns a probability to each class label for each pixel. Each convolution has a ReLu activation function, except for the last one, and the max-poolings and up-convolutions are performed with a 2x2 kernel.

The original purpose for U-Nets was the segmentation of biomedical images. U-nets were revolutionary due to the presence of the skip connections present in their structure. These connections join the pair of symmetric steps in the contracting and expansive paths and allow the network to concatenate feature maps, preserving fine-grained details and localization information.


## Hyperparameters for U-Net model
| Learning Rate | Batch Size | Epochs |
|---------------|------------|--------|
| 1x10^-3       | 32         | 35     |


