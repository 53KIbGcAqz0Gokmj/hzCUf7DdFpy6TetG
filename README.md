# MonReader

# Background:

MonReader is a new mobile document digitalization experience for the blind, for researchers and for everyone else in need for fully automatic, highly fast and high-quality document scanning in bulk. It is composed of a mobile app and all the user needs to do is flip pages and everything is handled by MonReader: it detects page flips from low-resolution camera preview and takes a high-resolution picture of the document, recognizing its corners and crops it accordingly, and it dewarps the cropped document to obtain a bird's eye view, sharpens the contrast between the text and the background and finally recognizes the text with formatting kept intact, being further corrected by MonReader's ML powered redactor.

# Goal(s):

Predict if the page is being flipped using a single image.

# Success Metrics:

Evaluate model performance based on F1 score, the higher the better.

# Bonus(es):

Predict if a given sequence of images contains an action of flipping.

# Methodology

## Images before Data Preprocessing

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/0354486a-14c5-437f-bfe7-49a953ea1ab5)

## CNN

* Convolutional Neural Networks (CNNs) to develop an image classification system capable of identifying 'flip' or 'not flip' conditions within images. 

initialiser: https://www.tensorflow.org/api_docs/python/tf/keras/initializers/HeUniform 

Activation functions: https://medium.com/@cmukesh8688/activation-functions-sigmoid-tanh-relu-leaky-relu-softmax-50d3778dcea5 -->

Use ReLu and sigmoid for the last Optimizer: https://www.analyticsvidhya.com/blog/2021/10/a-comprehensive-guide-on-deep-learning-optimizers/ -->

Adam: https://machinelearningmastery.com/adam-optimization-algorithm-for-deep-learning/

## Sequence Classification:

* One of our tasks was to classify sequences of images as flip or notflip; that is, we want to classify a short video clip as displaying the flipping action or not. In order to do this, we use the Resnet18 model to extract features from each image in a given sequence and then use an LSTM to learn the sequential nature from frame to frame.

* I padded the training sequences using a maxlen of 10. 95% of the training sequences have a length that is less than or equal to 27. Further, 95% of the validation sequences have a length that is less than or equal to 5. Using a maxlen of 10 is a sort of compromise and leads to good performance. I padded the validation sequences using a maxlen of 5. After training for 20 epochs, here are the accuracy and loss plots:

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/77ba3483-f03b-4fd1-98f5-6de43f041518)

Using a maxlen of 10, which is much smaller than maxlen of 27, for training and a maxlen of 5 for validation works really well for validation accuracy. You get around 96% val accuracy. Increasing maxlen for training beyond 10 doesn’t seem to improve val accuracy.

To evaluate the model on the test set, I used a maxlen of 4; 95% of the test sequences have a length that is less than or equal to 6, but using a maxlen of 4 gives better results. After evaluating on the test set, I got a test accuracy of 98.06%, a precision of 1, a recall of 0.96, and a f1score of 0.98

# Success Metrics:

* Evaluate model performance based on F1 score, the higher the better.

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/34a1ceda-3a62-490e-b327-0f79f1a607fa)

# Conclusion:

In this project, I developed and evaluated several models for image and video classification tasks, focusing on the 'flip' or 'not flip' scenarios:

* Traditional CNN Model: I trained a traditional CNN model to classify images as flip or not flip with 95% accuracy. This model established our foundational approach to image classification.

* Transfer Learning with Resnet18: By employing transfer learning techniques on a pretrained Resnet18 model, I enhanced the classification accuracy to 99%. This model required less training time and achieved better performance compared to the traditional CNN.

* Combined CNN/LSTM Model: For video sequence analysis, I used a combined CNN/LSTM model to classify sequences of images, or ‘videos’, achieving an accuracy of 98%. The selection of an optimal maxlen value was crucial for attaining this high level of performance.

* The image and video analyses performed in this project are useful not only for the mobile app, MonReader, that automates document digitization but also for image classification tasks like medical image analysis and activity/motion detection tasks like automated surveillance.


