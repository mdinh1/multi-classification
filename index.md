# Image Classification: Scenic Type Identification using CNN

### _Authored by Michael Dinh_
  
## Introduction
  
Image classification is the task of classifying an input image of its respective class from a set of 2 or more classes. In this case, the problem presented in this project will be a multi-class classification one where there are 6 possible categories the input image can be classified as. 

The purpose of selecting image classification as the subject of this project is to present myself with some new and fun challenges in applying the general machine learning workflow. This project is also intended to familiarize myself with the concept of convolutional neural networks and the practices involved when implementing the algorithm which ultimately allows for the ability to solve common computer vision problems like facial recognition or geolocation classifiction. 

### Problem Statement

The objective of this project is to accurately identify the type of structure presented in images using convolutional neural network (CNN) with the dataset that consists of scenic images of various structure types categorized by:
```
['buildings': 0, 'forest': 1, 'glacier': 2, 'mountain': 3, 'sea': 4, 'street': 5]
```
The target percentage in both training accuracy and validation accuracy is to be **at least 80%**. When the target results are achieved, the model will be demonstrated through a web-based interface where images can be uploaded and accurately classified to its respective structure type.

Questions that will be considered throughout this project:

- Of the pre-trained models available for convolutional neural networks, which ones will be tested?
- Which model is going to perform the best and how will that be measured?
- In the dataset, are there any images that may "confuse" the model?


## Data

The dataset used to fit the CNN model was obtained through [Kaggle](https://www.kaggle.com/puneet6060/intel-image-classification) which was originally used in a computer vision competition hosted on [Analytics Vidhya](https://datahack.analyticsvidhya.com/contest/practice-problem-intel-scene-classification-challe). The data consists a total of 17,034 images (150 x 150 dimension) where the images are already pre-segmented into training and testing data where all images labeled by their structure type.

```
TRAINING: Class names and image count
=====================================

 buildings:            2191 image files
    forest:            2271 image files
   glacier:            2404 image files
  mountain:            2512 image files
       sea:            2274 image files
    street:            2382 image files

     TOTAL:           14034 image files
```

```
TESTING: Class names and image count
====================================

 buildings:             437 image files
    forest:             474 image files
   glacier:             553 image files
  mountain:             525 image files
       sea:             510 image files
    street:             501 image files

     TOTAL:            3000 image files
```

![image_dist](https://user-images.githubusercontent.com/46685852/126810969-c2d659b9-f50f-467f-88fc-462309af4a0f.png)

### Limitations

While skimming through the images that exists in the training portion of the dataset, I've taken noticed of some potential limitations of the data. The limitations that exists in this dataset includes images that may "confuse" the model. 

Examples: 

- Scenic images with multiple potential labels

    ![5233](https://user-images.githubusercontent.com/46685852/127090257-efe7e02d-25b7-4f1a-8bd4-b8674a0d3b6c.jpg)![image](https://user-images.githubusercontent.com/46685852/127092472-0c9125ff-7d3a-4b00-b57d-a1caacc54c98.png)


- The images below simply does not belong in the dataset.

    ![image](https://user-images.githubusercontent.com/46685852/127090792-0e32c5ef-5434-4d77-a1b2-9ef1f3c01fa9.png) ![image](https://user-images.githubusercontent.com/46685852/127091877-7d9c6859-ef40-4487-a329-fd3a57a18990.png)
 
### Exploratory Data Analysis

When observing the randomly displayed images below, there is a couple of assumptions that can be made:

- Given that many images in street containing building structures, it is likely that a significant portion of the images in street will be classfied as buildings.
- Same can be said about images in glacier and sea where many images of glacier contains a body of water.

![data_sample_cropped](https://user-images.githubusercontent.com/46685852/126811166-e1fcd172-140d-452e-a757-7f1c17029b2f.png)


## Implementing the Models
During my research on how to structure a CNN model, Keras pre-trained ImageNet models are a viable method of producing quick and reliable image classification models. These pre-trained models is trained using ImageNet database which contains more than 14 million images belonging to 20,000 classes. Keras provides a number of models, however, I will be focused on the more popular ones: `VGG19` and `ResNet50`.

- `VGG19` is known for its simpler architecture and consist of 19 layers

<!--   - Convolution layer uses filters that perform operations as it is scanning the input image to extract features.
  - -->

<!-- ![image](https://user-images.githubusercontent.com/46685852/126830547-9de7c3f9-0a3c-4e5b-9556-498f71ffdaf0.png) -->

- `ResNet50` or Residual Network is a much more complex architecture which consists of 50 layers.


## VGG19 Modeling 

**Model summary:**
```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
vgg19 (Functional)           (None, 512)               20024384  
_________________________________________________________________
batch_normalization_9 (Batch (None, 512)               2048      
_________________________________________________________________
dense_9 (Dense)              (None, 256)               131328    
_________________________________________________________________
batch_normalization_10 (Batc (None, 256)               1024      
_________________________________________________________________
dense_10 (Dense)             (None, 128)               32896     
_________________________________________________________________
batch_normalization_11 (Batc (None, 128)               512       
_________________________________________________________________
dense_11 (Dense)             (None, 6)                 774       
=================================================================
Total params: 20,192,966
Trainable params: 166,790
Non-trainable params: 20,026,176
_________________________________________________________________
```

When observing the graph below, as learning cycles are completed the overall accuracy in both training and validation data increases with relatively small diverging from one another. 
![vgg_acc_2](https://user-images.githubusercontent.com/46685852/127204852-95a29649-6935-4a37-b2e5-90fdf9b24b5d.jpg)

In order to understand how well the model is performing, we will be focused on the overall accuracy and the recall score of each class. The recall score is the percentage of images that were classified correctly of each class.

- Example: "buildings" has a recall score of 88%. This means that of all images that were classified as "building", 88% of those images were classified correctly.

```markdown
              precision    recall  f1-score   support

   buildings       0.87      0.88      0.88       437
      forest       0.95      0.98      0.97       474
     glacier       0.83      0.78      0.81       553
    mountain       0.80      0.84      0.82       525
         sea       0.91      0.91      0.91       510
      street       0.89      0.88      0.89       501

    accuracy                           0.88      3000
   macro avg       0.88      0.88      0.88      3000
weighted avg       0.88      0.88      0.88      3000
```

To reflect on the assumptions mentioned above:
- 9.4% of actual images of "street" is classified as "building". 
- 16% of actual images of "glacier" is classified as "mountain" with 3.6% is classified as "sea"
![vgg_matrix](https://user-images.githubusercontent.com/46685852/127094994-4f2bca7d-a597-4853-b043-f965e9dfb6d2.png)



```
CLASSIFICATION Confidence:
==========================

0 -  buildings:   0.01%
1 -     forest:   0.22%
2 -    glacier:   1.39%
3 -   mountain:   0.01%
4 -        sea:  98.37%
5 -     street:   0.01%

CLASSIFIED: "sea"
```
![image](https://user-images.githubusercontent.com/46685852/127204467-41531918-d575-405f-a4fd-32228cd2e813.png)


## RESNET50 Modeling

**Model summary:**
```
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
resnet50 (Functional)        (None, 2048)              23587712  
_________________________________________________________________
batch_normalization_6 (Batch (None, 2048)              8192      
_________________________________________________________________
dense_6 (Dense)              (None, 256)               524544    
_________________________________________________________________
batch_normalization_7 (Batch (None, 256)               1024      
_________________________________________________________________
dense_7 (Dense)              (None, 128)               32896     
_________________________________________________________________
batch_normalization_8 (Batch (None, 128)               512       
_________________________________________________________________
dense_8 (Dense)              (None, 6)                 774       
=================================================================
Total params: 24,155,654
Trainable params: 563,078
Non-trainable params: 23,592,576
_________________________________________________________________
```

![res_accfig3](https://user-images.githubusercontent.com/46685852/127201591-78e4ef35-fa0a-4f38-9c8b-0470bdbee93a.jpg)

With VGG19 model, "glacier" had the lowest recall score of 78% whereas ResNet50 predicts "glacier" more accurately with a recall score of 84%. "street" recall score has also increased from 88% to 93%.

Overall accuracy has improved from VGG19's 88% to ResNet50's 91%.

```markdown
              precision    recall  f1-score   support

   buildings       0.92      0.90      0.91       437
      forest       0.99      0.99      0.99       474
     glacier       0.85      0.84      0.85       553
    mountain       0.84      0.85      0.84       525
         sea       0.94      0.94      0.94       510
      street       0.91      0.93      0.92       501

    accuracy                           0.91      3000
   macro avg       0.91      0.91      0.91      3000
weighted avg       0.91      0.91      0.91      3000
```

![res_matrix](https://user-images.githubusercontent.com/46685852/127208754-bcc5a342-7c37-493d-85ab-131a26913c31.jpg)


```
CLASSIFICATION Confidence:
==========================

0 -  buildings:   1.04%
1 -     forest:   0.44%
2 -    glacier:  53.86%
3 -   mountain:  31.75%
4 -        sea:  12.48%
5 -     street:   0.43%

CLASSIFIED: "glacier"
```
![image](https://user-images.githubusercontent.com/46685852/127204467-41531918-d575-405f-a4fd-32228cd2e813.png)

## Next Steps

- The next steps I want to take is trying to understand the architecture of both models in order to have a better understanding of the results and try to visualize what each layer in the model is doing to the input image. 
- I also want to find ways to automate the removal of "confusing" images.


## Sources

[ImageNet: VGGNet, ResNet, Inception, and Xception with Keras](https://www.pyimagesearch.com/2017/03/20/imagenet-vggnet-resnet-inception-xception-keras/)

