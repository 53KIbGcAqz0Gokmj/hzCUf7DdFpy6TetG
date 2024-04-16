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

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/e74660ed-79cf-4159-ab66-2f23275e1448)

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/394a2ed5-0c45-4aae-bda8-26382410d3e6)

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/b2b1bf70-b2d7-41e2-b528-cc17a7562e51)

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/78e8348f-d970-459c-aead-42ccb175ef3b) 

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/41068f11-f777-4494-8fc6-5a0fb1810ffc)

Using a maxlen of 10, which is much smaller than maxlen of 27, for training and a maxlen of 5 for validation works really well for validation accuracy. You get around 96% val accuracy. Increasing maxlen for training beyond 10 doesn’t seem to improve val accuracy.

To evaluate the model on the test set, I used a maxlen of 4; 95% of the test sequences have a length that is less than or equal to 6, but using a maxlen of 4 gives better results. After evaluating on the test set, I got a test accuracy of 98.06%, a precision of 1, a recall of 0.96, and a f1score of 0.98

# Conclusion:

In this project, I trained a traditional CNN model to classify images as flip or notflip with 95% accuracy, and I used transfer learning to fine-tune a pretrained Resnet18 model to classify images with 99% accuracy. The pretrained model performed better than the CNN and took less time to train. However, both models did not generalize well when applied to images that were not as realistic-looking as the ones the models were trained on. Finally, I applied a CNN/LSTM combined model to classify sequences of images, or ‘videos’, as flip or notflip with 98% accuracy. The choice of a good maxlen value was crucial in getting optimal performance.

The image and video analyses performed in this project are useful not only for the mobile app, MonReader, that automates document digitization but also for image classification tasks like medical image analysis and activity/motion detection tasks like automated surveillance.


