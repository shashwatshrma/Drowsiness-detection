# Drowsinessdetection
This project aims to create a CNN classifier to classify whether the eye in the given image is closed or not in order to predict whether the user is drowsy or not (or a driver in a real life scenario). This project incorporates transfer learning in order to achieve classification.

## Data used
The dataset used in this project is the MRL eye dataset, taken from http://mrl.cs.vsb.cz/eyedataset.

## Preprocessing
I have first arranged the given dataset into 2 directories open and closed eyes. Then split these into training and testing set following the hierarchy:
```
prepared_data/
		train_data/
			open_eyes/
			
			closed_eyes/

		test_data/
			open_eyes/
			
			closed_eyes/
```

The code for doing this can be found in preprocess.ipynb

## Model
I have used the concept of Transfer Learning to use InceptionV3 in this project. Inception is a CNN developed by Google and introduced in 2015.
I have added a head model of dense layers in addition to Inception's convolution and pooling layers.

Then I have trained this model on the training set made in the preprocessing step using 20% as validation set and running 10 epochs on the this data.

The code for doing this can be found in model.ipynb

## Detector application
Finally, the application that actually detects the drowsiness.

This application uses OpenCV to capture the device's webcam and uses the inbuilt haar cascade detector's to detect face and eyes. Each second, the application evaluates the frame for open or closed eyes using our classification model. 

If the eyes are closed for more than 3 seconds then an alarm is played.