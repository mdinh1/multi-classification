<div align="center">
  <h1>Multiclass Classification: Structure Type Identification</h1>
</div>
<h3 style="font-style: italic;">Authored by Michael Dinh<h3>
  
## Introduction
  
This project is intended as the initial steps..
  
### Problem Statement
The objective of this project is to accurately identify the manmade/natural structure presented in image files through convolutional neural network (CNN) using an image dataset of structures of different types, which includes buildings, forest, glacier, mountains, sea, and streets. The target percentage in both training accuracy and validation accuracy is to be at least 80%. When the target results are obtained, the model will have a web-based interface where images can be uploaded and classified.

## Data
  [Kaggle](https://www.kaggle.com/puneet6060/intel-image-classification)
  
### Exploratory Data Analysis

  

<p align="center">
  <img src="https://user-images.githubusercontent.com/46685852/126672473-2e2409b2-9384-4654-84a9-4b120fb0fb03.png">
</p>
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/46685852/126688519-aa63c645-e6ad-448a-b543-d6ef80fecd47.png">
</p>
  
### Limitations

## Preprocessing

## VGG19 Modeling 

**CODE:**
```markdown
CODE:
from tensorflow.keras import Sequential, layers, regularizers, losses, callbacks, models
from tensorflow.keras.applications import VGG19
from tensorflow.keras import optimizers
  
num_classes = 6

vgg_model = Sequential([
    VGG19(include_top = False, pooling='avg', weights='imagenet'),
    layers.BatchNormalization(),
    layers.Dense(256, activation='relu'),
    layers.BatchNormalization(),
    layers.Dense(128, activation='relu'),
    layers.BatchNormalization(),
    layers.Dense(num_classes, activation='softmax')
])

vgg_model.layers[0].trainable = False

sgd = optimizers.Adam(learning_rate=0.001, beta_1=0.9, beta_2=0.999)
vgg_model.compile(optimizer=sgd, loss='categorical_crossentropy', metrics=['accuracy'])

vgg_model.summary()
```
**OUTPUT:**
```markdown
OUTPUT:
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

```markdown
CODE:
callback = callbacks.EarlyStopping(monitor='val_loss', patience=4, restore_best_weights=True)
vgg_results = vgg_model.fit(train_set, validation_data=test_set, epochs=100, steps_per_epoch=10, validation_steps=10, callbacks=[callback])

OUTPUT:
Epoch 1/100
10/10 [==============================] - 2s 155ms/step - loss: 1.5690 - accuracy: 0.4250 - val_loss: 1.4302 - val_accuracy: 0.5781
Epoch 2/100
10/10 [==============================] - 1s 127ms/step - loss: 0.6622 - accuracy: 0.7812 - val_loss: 0.9832 - val_accuracy: 0.6531
Epoch 3/100
10/10 [==============================] - 1s 127ms/step - loss: 0.5124 - accuracy: 0.8344 - val_loss: 0.8827 - val_accuracy: 0.7531
Epoch 4/100
10/10 [==============================] - 1s 127ms/step - loss: 0.4731 - accuracy: 0.8281 - val_loss: 0.6478 - val_accuracy: 0.7937
Epoch 5/100
10/10 [==============================] - 1s 128ms/step - loss: 0.4536 - accuracy: 0.8344 - val_loss: 0.5416 - val_accuracy: 0.8375
Epoch 6/100
10/10 [==============================] - 1s 128ms/step - loss: 0.4126 - accuracy: 0.8438 - val_loss: 0.3755 - val_accuracy: 0.8875
Epoch 7/100
10/10 [==============================] - 1s 128ms/step - loss: 0.4070 - accuracy: 0.8594 - val_loss: 0.4433 - val_accuracy: 0.8500
Epoch 8/100
10/10 [==============================] - 1s 129ms/step - loss: 0.4323 - accuracy: 0.8344 - val_loss: 0.4056 - val_accuracy: 0.8781
Epoch 9/100
10/10 [==============================] - 1s 129ms/step - loss: 0.2884 - accuracy: 0.9000 - val_loss: 0.4439 - val_accuracy: 0.8469
Epoch 10/100
10/10 [==============================] - 1s 131ms/step - loss: 0.3366 - accuracy: 0.8781 - val_loss: 0.3357 - val_accuracy: 0.8813
Epoch 11/100
10/10 [==============================] - 1s 130ms/step - loss: 0.3328 - accuracy: 0.8813 - val_loss: 0.3875 - val_accuracy: 0.8750
Epoch 12/100
10/10 [==============================] - 1s 130ms/step - loss: 0.3658 - accuracy: 0.8750 - val_loss: 0.4408 - val_accuracy: 0.8531
Epoch 13/100
10/10 [==============================] - 1s 129ms/step - loss: 0.3231 - accuracy: 0.8938 - val_loss: 0.2841 - val_accuracy: 0.8969
Epoch 14/100
10/10 [==============================] - 1s 148ms/step - loss: 0.3020 - accuracy: 0.9156 - val_loss: 0.3482 - val_accuracy: 0.8594
Epoch 15/100
10/10 [==============================] - 1s 130ms/step - loss: 0.3207 - accuracy: 0.8938 - val_loss: 0.2843 - val_accuracy: 0.8750
Epoch 16/100
10/10 [==============================] - 1s 130ms/step - loss: 0.3158 - accuracy: 0.8844 - val_loss: 0.3054 - val_accuracy: 0.8844
Epoch 17/100
10/10 [==============================] - 1s 129ms/step - loss: 0.3175 - accuracy: 0.9062 - val_loss: 0.3209 - val_accuracy: 0.8781
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
