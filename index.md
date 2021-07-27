# Image Classification: Structure Type Identification using CNN

### _Authored by Michael Dinh_
  
## Introduction
  
Image classification is the task of classifying an input image of its respective class from a set of 2 or more classes/labels. In this case, the problem presented in this project will be a multi-class classification one where there are 6 possible categories the input image can be classified as. 

The purpose of selecting image classification as the subject of this project is to present myself with some new and fun challenges in applying the general machine learning workflow. 
This project is also intended to familiarize myself with the concept of convolutional neural networks and the practices involved when implementing the algorithm which ultimately allows for the ability to solve common computer vision problems like facial recognition and/or geolocation classifiction. 

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
-- seg_test/
  -- buildings/
  -- forest/
  -- glacier/
  -- mountain/
  -- sea/
  -- street/

-- seg_train/
  -- buildings/
  -- forest/
  -- glacier/
  -- mountain/
  -- sea/
  -- street/
```

### Limitations


  
### Exploratory Data Analysis
![data_sample_cropped](https://user-images.githubusercontent.com/46685852/126811166-e1fcd172-140d-452e-a757-7f1c17029b2f.png)


```markdown
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

```markdown
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

## Preprocessing

## VGG19(OxfordNet) Modeling 

![image](https://user-images.githubusercontent.com/46685852/126830547-9de7c3f9-0a3c-4e5b-9556-498f71ffdaf0.png)

**Model summary:**
```markdown
Model: "sequential"
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

![vgg_loss](https://user-images.githubusercontent.com/46685852/126697633-6f0bf4a4-046c-4f64-b77e-533bb357f92b.jpg)

![vgg_acc](https://user-images.githubusercontent.com/46685852/126697638-0b9d9dd9-722c-436f-b722-a68f67ce04b5.jpg)



## RESNET50 Modeling

**Model summary:**
```markdown
Model: "sequential_1"
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

## Results

```markdown
              precision    recall  f1-score   support

   buildings       0.90      0.88      0.89       437
      forest       0.99      1.00      0.99       474
     glacier       0.87      0.82      0.84       553
    mountain       0.85      0.85      0.85       525
         sea       0.93      0.97      0.95       510
      street       0.88      0.92      0.90       501

    accuracy                           0.90      3000
   macro avg       0.90      0.91      0.90      3000
weighted avg       0.90      0.90      0.90      3000
```

## Conclusion

## Next Steps

## Sources

[pyimagesearch](https://www.pyimagesearch.com/2017/03/20/imagenet-vggnet-resnet-inception-xception-keras/) ImageNet: VGGNet, ResNet, Inception, and Xception with Keras

You can use the [editor on GitHub](https://github.com/mdinh1/multi-classification/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
