
# Multiclass Classification: Structure Type Identification using CNN

### _Authored by Michael Dinh_
  
## Introduction
  
Briefly introduce image classifcation, the benefits and why you did this project.

### Problem Statement
The objective of this project is to accurately identify the type of structure presented in images through convolutional neural network (CNN) using a dataset that consists of scenes of various structure types, which includes:
```
['buildings': 0, 'forest': 1, 'glacier': 2, 'mountain': 3, 'sea': 4, 'street': 5]
```
The target percentage in both training accuracy and validation accuracy is to be **at least 80%**. When the target results are achieved, the model will be demonstrated through a web-based interface where images can be uploaded and accurately classified to its respective structure type.

### Convolutional Neural Network


## Data
[Kaggle](https://www.kaggle.com/puneet6060/intel-image-classification)
  
## Exploratory Data Analysis
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

### Limitations

## Preprocessing

## VGG19(OxfordNet) Modeling 

**Model summary:**
```markdown
Model: "sequential_3"
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
Model: "sequential_2"
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

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/mdinh1/multi-classification/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.

