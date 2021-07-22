<div align="center">
  <h1>Multiclass Classification: Structure Type Identification</h1>
</div>
<h3 style="font-style: italic;">Authored by Michael Dinh<h3>
  
## Introduction
### Problem Statement

## Data
### Exploratory Data Analysis

  

<p align="center">
  <img src="https://user-images.githubusercontent.com/46685852/126672473-2e2409b2-9384-4654-84a9-4b120fb0fb03.png">
</p>
  
### Limitations

## Preprocessing

## VGG19 Modeling 

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
