# Pix2Pix architecture 

Generative Adversarial Networks (GANs) are a type of neural network introduced by Goodfellow et al. 
GANs consist of two distinct architectures, a generator and a discriminator, which are trained simultaneously through adversarial training. 
The generator creates synthetic data, while the discriminator evaluates its authenticity.
The competition between these two networks results in the generator producing increasingly realistic data, making GANs particularly effective for image synthesis, style transfer, and data generation tasks. 


In particular, Pix2Pix is a specific architecture that is based on conditional GANs (cGANs) and that was designed for image-to-image translation tasks. 
Unlike traditional GANs that generate images from random noise, cGANS like Pix2Pix is composed of a generator that takes an input image and transforms it into a corresponding output image, while the discriminator evaluates the generated images and tries to distinguish them from real images in the output domain. 

The Pix2Pix's discriminator works as a classifier, determining if the synthetic image is real or not; whereas the generator's objective function is described as a combination of two terms. 
The first term, represents the adversarial loss, pushing the generator to produce images that are convincing to the discriminator. 
The second term, is the L1 loss, ensuring that the generated images are structurally similar to the ground truth images. 
Thus, the Pix2Pix generator has two ways of updating its weights during training, one is by the internal circuit, and an external path is provided by the comparison of results between ground truth and fake images from the discriminator. Thus, the generator learns to produce segmented images that resemble more the target segmentations.


## Hyperparameters for Pix2Pix model
| Learning Rate           | Batch Size         |      Epochs      | B_1 Weights          |
|------------------------|---------------------|-----------------|-----------------------|
| 2x10-3                 | 4                   | 35              | 0.9                   |


