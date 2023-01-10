# CAIS++ Winter Project
Lucia Zhang, lrzhang@usc.edu

This project aims to classify images of letters from American Sign Language, including the 26 letters A-Z and SPACE, DELETE, NOTHING. 

The ASL Alphabet dataset on Kaggle (https://www.kaggle.com/datasets/grassknoted/asl-alphabet) (ASL Alphabet Version 1 by Akash Nagaraj) consists of 87,000 200 x 200 pixel images in the training data set and 29 images in the test data set. I pre-processed the data by applying image transformations to resize, crop, and normalize the images.

I trained only on 27,173 total images rather than the entire 87,029, and I split it into train, test, and validation sets. The original test set only had 29 images, so I made it bigger. I used transfer learning with ResNet 50, because it has many layers that allow it to train well, but it is not so big that training would take too long or it would overfit. I froze all of the layers besides the last fully connected layer and set it to output 29 classes. The model trained well after 2 epochs with cross entropy loss, the Adam optimizer, and a learning rate of 0.001. 

I evaluated based on cross entropy loss and accuracy during training and also on the test set. The model performed with a 98% accuracy on the test set.

The dataset, model architecture, training procedures, and chosenmetrics fit the task at hand pretty well. However, not being able to use the entire dataset and also other constraints associated with computational power limited what I could do. Furthermore, the images were all very uniform: the hand formation positioned in the same place with different lighting for each letter. The model became really good at classifying images from this type of data, but when applying the model to other images of ASL letters not from the data set, it would likely perform poorly. 

These efforts could be extended to motions rather than just still frames, so it could classify words rather than just letters. This could also become live transcription on videos to allow for real-time translation from ASL to English. Limitations could include the fact that most of the training data in this training set (and likely many other sets) are not realistic representations of what regular photos or videos of ASL would look like. Gathering data would be a large constraint for this project. 

If I were to continue this project, I would work on classifying videos of words, not just letters. The current model is not fit for this task because it cannot classify words from video clips, and it is again trained on a very limited, uniform dataset. 
