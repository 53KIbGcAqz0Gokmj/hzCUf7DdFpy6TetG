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

![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/78e8348f-d970-459c-aead-42ccb175ef3b)  ![image](https://github.com/53KIbGcAqz0Gokmj/hzCUf7DdFpy6TetG/assets/143815258/3a2757e7-1a99-45bb-9e71-9e44b915d218)

