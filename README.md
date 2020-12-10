![Header Image](https://github.com/lanapalmer/EyeSpy_ImageClassifier/blob/master/images/EyeSpy-GitHubHeader.png)

# Eye Spy: A CNN Image Classifier for Headshot Photographers #

## Introduction ##

I have a side business as a photographer, focusing on headshot photography for film and theatre actors. In every session, headshot photographers will typically take 300-600 photographs. Invariably, the subject is blinking, or has partially closed eyes in some of these images.

Photos where the subject is blinking or has partially closed eyes aren't usually the most flattering images, so after every session, I manually edit out these photographs before sending them to the client. This can can take 30 minutes to an hour for each session.

<p align="center">
<img src='https://github.com/lanapalmer/EyeSpy_ImageClassifier/blob/master/images/web-example-image.png'>
  </p>

I was considering hiring an assistant to do this task, but first, I wanted to see if I could create a convolutional neural network to filter through the photographs and classify them, saving me time and expense.

## Objective ##
To build a convolutional neural network that correctly classifies images where the subject is blinking with 80% accuracy, and deploy it as a web app.

## Data Collection & Curation ## 

I've been offering headshot sessions for several years, so I have a large archive of images. I manually labelled photographs from my own collection of archived sessions, splitting them into BLINKING and NON_BLINKING groups. Each group included 500 images.

I aimed to create a dataset that was diverse in age, gender, and racial groups. The approximate breakdown was:

* **Gender** Female: 54%, Male 43%, Non-Binary: 3%
* **Race** White: 60%, Black: 27%, Asian: 8%, Other: 3%
* **Age** < 25: 8%, 25-50: 49%, 50+: 38%

For the privacy of my clients I am not including the images on github, but this is an example of 'blinking' and 'non-blinking' photos from the data set:
<p align="center">
<img src='https://github.com/lanapalmer/EyeSpy_ImageClassifier/blob/master/images/Blinks-NonBlinks-Ex.png'>
  </p>
  
## Initial Model ##

I built the initial model using the Gradient Machine Learning Platform on Paperspace. I used  Keras with TensorFlow 2.0 to build a three layer sequential model.

### Initial Model Metrics ###
* Train Accuracy: 0.817, Test Accuracy: 0.777
* Precision: 0.778523
* Recall: 0.773333
* F1 score: 0.775920

<p align="center">
<img src='https://github.com/lanapalmer/EyeSpy_ImageClassifier/blob/master/images/EyeSpy-InitialModel.png'  height="400">
</p>

  
## Model Tuning ##

I tuned the model using the Keras Hyperband tuner, resulting in a optimal learning rate of .0001 over 10 epochs.

### Final Model Metrics ###
* Train Accuracy: 0.86, Test Accuracy: 0.79 
* Precision: 0.77
* Recall: 0.82
* F1 score: 0.775

<p align="center">
<img src='https://github.com/lanapalmer/EyeSpy_ImageClassifier/blob/master/images/EyeSpy-FinalModel.png'  height="400">
</p>


## Conclusion ##

The convolutional neural network was able to classify blinks versus non-blinks with 79% accuracy on the testing data set.

## NEXT STEPS ##

I plan to back to the initial model and see which images are being misclassified. I can then provide more training examples of similar images, which may improve model performance.

After improving model performance, I'd like to build a more robust app that will import a large number of images, and filter them into two groups for final review.
This could either be a web app, an MacOS app, or a plugin to an existing photo editing application.
