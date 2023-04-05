# Forest Aerial Segmentation

## What is Image segmentation

mage segmentation is a method in which a digital image is broken down into various subgroups called Image segments which helps in reducing the complexity of the image to make further processing or analysis of the image simpler. Segmentation in easy words is assigning labels to pixels. All picture elements or pixels belonging to the same category have a common label assigned to them.
Image segmentation is a function that takes image inputs and produces an output. The output is a mask or a matrix with various elements specifying the object class or instance to which each pixel belongs.

## About the problem statement

Automatic categorization and segmentation of forest cover is of great importance for sustainable development and urban planning. The importance of forests cannot be underestimated as they support the flow of essential ecosystem services such as fibre, energy, recreation, biodiversity, carbon storage and flux and water. Forests are also important areas to identify before commencing any kind of industrial activity that requires on field work. Satellite or remote sensed images can be used to identify and segment the forest cover regions in the image and get a clear idea about how much land does forest cover. This problem is defined as a **binary segmentation task** to detect forest areas.

## Dataset

- Automatic categorization and segmentation of forest cover is essential for sustainable development and urban planning.
- Forests provide vital ecosystem services such as carbon storage, water flow, biodiversity, and recreation.
- Forest areas need to be identified before commencing any industrial activity that requires on-field work.
- Satellite or remote sensed images can be used to detect and segment forest cover regions in an image.
- Forest area segmentation is a binary segmentation task that aims to detect forest areas by assigning a binary label (e.g., 1 for forest and 0 for non-forest) to each pixel in the image.

> **Note** : The dataset used for this experiment was taken via [Kaggle](https://www.kaggle.com/datasets/quadeer15sh/augmented-forest-segmentation).

## U-Net

The U-Net architecture was proposed in the [U-Net: Convolutional Networks for Biomedical Image Segmentation paper](https://arxiv.org/pdf/1505.04597.pdf) in 2015.  
With this U-Net architecture, the segmentation of images of sizes 512X512 can be computed with a modern GPU within small amounts of time. There have been many variants and modifications of this architecture due to its phenomenal success. Some of them include LadderNet, U-Net with attention, the recurrent and residual convolutional U-Net (R2-UNet), and U-Net with residual blocks or blocks with dense connections.  
**Building blocks of U-Net :**

- Encoder : series of layers that extract image features using progressively deeper, narrower filters. The encoder might be pre-trained on a similar task (e.g., image recognition), allowing it to leverage its existing knowledge to perform segmentation tasks.
- Decoder : series of layers that gradually convert the encoder’s output into a segmentation mask corresponding with the input image’s pixel resolution.
- Skip connections : multiple long-range neural network connections allowing the model to identify features at different scales to enhance model accuracy.

**Architecture of the U-Net**

<p align="center">
  <img src="https://blog.paperspace.com/content/images/size/w1000/2021/05/image-26.png" />
</p>
The contracting and expansive paths mirror each other. The name U-Net comes from the shape of the network, which forms a U-shape.  
The encoder block has a constant reduction of image size with the help of the max-pooling layers of strides 2. We also have repeated convolutional layers with an increasing number of filters in the encoder architecture. Once we reach the decoder aspect, we notice the number of filters in the convolutional layers start to decrease along with a gradual upsampling in the following layers all the way to the top. We also notice that the use of skip connections that connect the previous outputs with the layers in the decoder blocks.  
This skip connection is a vital concept to preserve the loss from the previous layers so that they reflect stronger on the overall values. High-resolution features from the contracting path are combined with the upsampled output to improve the network's localization capacity.
