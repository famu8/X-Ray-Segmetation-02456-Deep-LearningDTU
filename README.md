# Automating the Segmentation of X-ray Images with Deep Neural Networks
## X-Ray Segmetation 02456 Deep Learning DTU Fall 2023

**Authors**: _Alba Castrillo Perote (s230221@dtu.dk), Andrea Matamoros Alonso (s233514@dtu.dk), Fernando Augusto Marina Urriola (s233144@dtu.dk) and Jesus Díaz Pereira (s233142@dtu.dk)._

The authors would like to thank Salvatore De Angelis (sdea@dtu.dk) and Peter Stanley Jørgensen (psjq@dtu.dk) for their help and collaboration throughout the project.

### Introduction
In solid oxide fuel cells (SOFC) and electrolysis cells, electrode composition is crucial for optimal
performance. The state-of-the-art solution is nickel and yttria-stabilized zirconia cermet, but nickel
usage can lead to microstructural changes, degrading cell performance. To address these changes,
imaging techniques like ptychographic X-ray computed tomography (PXCT) are used. However,
manual or traditional segmentation methods are time-consuming and error-prone. Automating seg-
mentation is crucial for keeping up with data acquisition rates.
This paper proposes using deep neural networks to automate PXCT image segmentation, eliminating
the need for human intervention, by comparing two distinct neural network models, more specifically
a U-Net and a conditional Generative Adversarial Network (cGAN), Pix2Pix.

### Keypoints 
+ The training dataset comprises PXCT images and the results will be benchmarked against man-
ually labeled images. For more information about the acquisition process and information on the
dataset please contact: Salvatore De Angelis (sdea@dtu.dk)
+ The DICE coefficient was specifically selected as the evaluation metric to compare the archi-
tecture performance due to its effectiveness in quantifying the overlap between segmented regions
in the predicted and ground truth images.
+ U-Net architecture, comprising an encoder and decoder, has demonstrated notable success in var-
ious image segmentation tasks. The encoder captures hierarchical features, while the decoder
reconstructs the spatial information. During training, these components work collaboratively,
with the encoder extracting essential features and the decoder refining the segmentation.
+ cGANs consist of two distinct architectures, namely, a generator and a discriminator, which
are trained simultaneously through adversarial training. The generator creates a synthetic image
based on an input image, while the discriminator evaluates it.
+ We conducted a comparative analysis of the amount of training data required to achieve acceptable results. This is particularly crucial as the training process involves manual segmentation as
an initial step

```diff
- Dislcaimer: when performing the dynamic training to check the robustness of the models, the same dataset has been used, i.e. no image shuffle has been performed, training and testing with the same images in each iteration.  
```

### Results obtained
![Results_images_2](https://github.com/famu8/X-Ray-Segmetation-02456-Deep-LearningDTU/assets/105816142/bfc20239-965f-48e7-9677-ed1403f38fb6)
_(The figure displays random examples of the segmentation
results from both models on the test dataset. Each row shows
the original image, the ground truth, and the segmentation re-
sults from each network. As illustrated, both models were
able to segment the images with a high degree of quality, pro-
ducing similar results to the ground truth.)_

#### Quantitative results 
Obtained from the test set, including the Dice coefficient’s mean and standard deviation from each
model are reported in Table 1. The results show that Pix2Pix
achieved a slightly higher mean Dice Coefficient than U-Net
(0.987 vs. 0.905) indicating that it performed better on average.

| **Network** | **Mean Dice Coefficient** | **Mean Standard Deviation** |
|-------------|---------------------------|-----------------------------|
| Pix2Pix     | $0.987$                   | $0.001$                     |
| U-Net       | $0.905$                   | $0.136$                     |

*Table 1: Internal Test Results for Dice Coefficient*


### Discussion

This study aimed to compare the performance of PXCT image segmentation using standard U-Net and Pix2Pix architectures. Our hypothesis, based on the integration of a conditional Generative Adversarial Network (cGAN) in Pix2Pix, suggested superior results compared to a conventional U-Net model. Results from internal testing supported this hypothesis, highlighting Pix2Pix's advantages, particularly when using a reduced number of training images. Interestingly, we observed that Pix2Pix outperformed U-Net even with only 10% of the training data, significantly reducing the manual annotation workload. The absence of residual blocks in U-Net, contrary to their presence in the Pix2Pix Generator, may be a factor influencing results, suggesting their potential utility for reusing low-level features in images with intricate patterns. While our study provides valuable insights, future research should explore the robustness of these findings, especially considering the dataset's internal correlation. Further investigations should assess the generalization of these neural network architectures to different PXCT images, possibly by training models on 2D images from a single volume and evaluating their performance across remaining volume slices. Additionally, conducting sensitivity analyses under diverse imaging conditions and assessing model performance in the presence of noise in PXCT data will be crucial for evaluating reliability in real-world scenarios.












