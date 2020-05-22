# Crystal Image Classifier
- Image classification using [resnet34](https://arxiv.org/abs/1512.03385)
- Using crystal images from [MARCO](https://marco.ccr.buffalo.edu/) 

<div style="display: flex;">
  <figure>
    <img src="https://marco.ccr.buffalo.edu/image/raw/1" width="300">
    <figcaption>Clear</figcaption>
  </figure>

  <figure>
    <img src="https://marco.ccr.buffalo.edu/image/raw/58" width="300">
    <figcaption>Crystal</figcaption>
  </figure>

  <figure>
    <img src="https://marco.ccr.buffalo.edu/image/raw/1212" width="300">
    <figcaption>Other</figcaption>
  </figure>

  <figure>
    <img src="https://marco.ccr.buffalo.edu/image/raw/245" width="300">
    <figcaption>Precipitate</figcaption>
  </figure>
</div>

---
## Current state-of-the-art

> Bruno AE, Charbonneau P, Newman J, Snell EH, So DR, et al. (2018) Classification of crystallization outcomes using deep convolutional neural networks. PLOS ONE 13(6): e0198883. https://doi.org/10.1371/journal.pone.0198883

![Confusion matrix](https://journals.plos.org/plosone/article/figure/image?size=large&id=info:doi/10.1371/journal.pone.0198883.t004)

Let's see if we can do better using resnet-34

---
## My model

With fine-tuning and using the resnet34 CNN on a set of **2048 images**, I trained a model with an **accuracy of 85%**, which isn't too far off from the state-of-the-art model trained with much more data. Like the previous paper, the classifier struggled most with images labeled as "Other" and seemed to struggle with precipitate vs clear and precipitate vs crystals.

### Data sourcing

A set of 2048 .jpeg images was taken from MARCO. Download [here](https://d27i862zg3bohz.cloudfront.net/ml/xtal-marco-2048.zip).

Data was then split into a training (80%) and test (80%) set.


### Training

![Confusion matrix before learning rate tuning](https://github.com/loren-jiang/xtal-classifier/blob/master/confusion_matrix_pretune.png)

![Top losses](https://github.com/loren-jiang/xtal-classifier/blob/master/top_9_losses.png)

![Learning rate vs loss](https://github.com/loren-jiang/xtal-classifier/blob/master/learning_rate_tuning.png)

![Confusion matrix after learning rate tuning](https://github.com/loren-jiang/xtal-classifier/blob/master/confusion_matrix_posttune.png)

