
# Improving generalization via style transfer-based data augmentation: Novel regularization method

![Generated skin lesions: example.](https://github.com/AgaMiko/ST-DA/blob/master/Skin-lesions-examples.jpg)

## Introduction
Currently, deep learning (DL) algorithms are considered as state-of-the-art in many classification tasks,
and yet the problem of weak generalization is very common, widely mentioned, and still up-to-date.
One of the main goals in machine learning is to achieve the highest generalization ability of the trained model.
Although huge, multi-layered models are able to extract advanced features from great amounts of data,
unfortunately they often show a tendency to overfit.
The present paper focuses most on the data augmentation. In our method, new images are synthetized with neural style transfer (NST),
and the generated images are then used to train the convolutional neural network (CNN) in order to improve
its generalization abilities.  
The main contributions of this paper are:
*	The proposition of using neural style transfer for the data augmentation technique (ST-DA). This approach is presented on the skin lesion case study by transforming a benign skin lesion to a malignant lesion, and tested with dataset enrichment evaluation; 
*	Incorporating unlabeled, synthesized data into training by adding pseudo-labels generated by another CNN; 
*	Limiting the problem of noisy pseudo-labels in synthetic images used as a CNN training set by using only real images in validation and test sets;
*	Evaluating the ability to enrich the training dataset with artificially generated data with Deep Taylor Decomposition, 
* Proving that the ST-DA method significantly improves the performance and repeatability of training for deep neural networks.


## ST-DA
xxxx
### How-to

### Details
The result and details of the method can be found in the original paper here: [xxx](xxx)
## Database 
### Download
We generated 248 489 out of of 1088 malignant skin lesions and 12433 benign images. In particular, only 418 malignant lesions were used from the original dataset to create the database.  
Database can be download [here](xxx)
#### If you use this database please star the repository and cite the following paper:

### Source of original skin lesions
The used database was the publicly available dataset of Dermatoscopic images of the most common classes of skin lesions from The International Skin Imaging Collaboration: Melanoma Project Archive (Codella et al., 2018; Tschandl, Rosendahl, & Kittler, 2018). 

### Style transfer
The neural style transfer used in this work is based on [xx], with improvements detailed in [xx], and implemented in Keras 2.0. Going into the details, the VGG16 Convolutional Neural Network was used with the input image of 224x224 px and Conv5_2 as the content layer (detailed notation in [xxx]). Each image was initialized by the content picture, the content weight equal to 0.025, the style weight equal to 1.0, and the pooling layer with pool size defined by the maximum operator. 

### Architecture and training
For pseudo-labelling, VGG16 trained on a skin lesion dataset was used (full description in [xxx]).
Moreover, VGG8 and VGG11 implementations as described in (Grochowski, Kwasigroch, & Mikolajczyk, 2019) were used, along with VGG16 and DenseNet121 from Keras 2.0 [xxx]. The following regularization techniques were applied to each tested network: traditional data augmentation (rotation, zoom, shear, reflection), dropout, and early stopping. All the experiments were performed with the same hyperparameters, regularization techniques, and architectures, in order to make comparison reliable.


**xxxx

## Sources

The database was generated using following sources:

* *Image generation:*
  * **Style transfer original paper:** xxxx
  * **Style transfer implementation:** [SmoothGrad](https://arxiv.org/abs/1706.03825) averages the gradient over number of inputs with added noise.
* *Explaiability method:*
  * **Deep Taylor decomposition:** [DeepTaylor](https://www.sciencedirect.com/science/article/pii/S0031320316303582?via%3Dihub) computes for each neuron a rootpoint, that is close to the input, but which's output value is 0, and uses this difference to estimate the attribution of each neuron recursively.
   * **Repository:** [iNNvestigate](https://github.com/albermax/innvestigate) library contains implementations for the
   SmoothGrad, DeConvNet, Guided BackProp,  PatternNet, DeepTaylor, PatternAttribution, IntegratedGradients and DeepLIFT.  
* *Source database:*
  * **ISIC Archive:** The [ISIC Archive](https://www.isic-archive.com) contains over 23k images of skin lesions, labeled as 'benign' or 'malignant'.
  * **ISIC Archive Downloader:** A [script](https://github.com/GalAvineri/ISIC-Archive-Downloader) to download the ISIC Archive of lesion images 
* *Other:*
  * **VGG8** [Selected ....](link) applies a ReLU in the gradient computation instead of the gradient of a ReLU.
