<div align="center">
  <h1>Multiclass Classification: Structure Type Identification</h1>
</div>
<p style="font-style: italic;">Authored by Michael Dinh<p>
  
<h2>Introduction</h2>
  
This project is intended as the initial steps..
  
<h2>Problem Statement</h2>
The objective of this project is to accurately identify the manmade/natural structure presented in image files through convolutional neural network (CNN) using an image dataset of structures of different types, which includes buildings, forest, glacier, mountains, sea, and streets. The target percentage in both training accuracy and validation accuracy is to be at least 80%. When the target results are obtained, the model will have a web-based interface where images can be uploaded and classified.

<h2>Data</h2>
  [Kaggle](https://www.kaggle.com/puneet6060/intel-image-classification)
  
<h2>Exploratory Data Analysis</h2>

  

<p align="center">
  <img src="https://user-images.githubusercontent.com/46685852/126672473-2e2409b2-9384-4654-84a9-4b120fb0fb03.png">
</p>
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/46685852/126688519-aa63c645-e6ad-448a-b543-d6ef80fecd47.png">
</p>
  
### Limitations

## Preprocessing

## VGG19 Modeling 

**OUTPUT:**
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

## RESNET50 Modeling

## Results

## Conclusion

## Next Steps

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
