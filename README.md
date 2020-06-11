## [<img width="500" alt="found2" src="https://user-images.githubusercontent.com/33357541/84373486-5202d800-abe5-11ea-999c-cd1aa2c0da5d.png">](https://vvitsenets.github.io)

### Real-time emotion recognition in browser using javascript library [face-api.js](https://github.com/justadudewhohacks/face-api.js)

![test](https://user-images.githubusercontent.com/33357541/84315507-71ace880-ab72-11ea-9aee-53363777033a.png)


face-api.js - JavaScript API for face detection and face recognition in the browser.

JavaScript emotion recognition API for the browser implemented on top of tensorflow.js core ([tensorflow/tfjs-core](https://github.com/tensorflow/tfjs))

### TO DO

- Turn on the Webcam  

- Turn on the Load Model switch to load the face detection pre-trained models

- Turn on the Detect Face switch to start detecting faces in your webcam

## Face Detection Models

SSD Mobilenet V1

For face detection, this project implements a SSD (Single Shot Multibox Detector) based on MobileNetV1. The neural net will compute the locations of each face in an image and will return the bounding boxes together with it's probability for each face. This face detector is aiming towards obtaining high accuracy in detecting face bounding boxes instead of low inference time. The size of the quantized model is about 5.4 MB (ssd_mobilenetv1_model).

The face detection model has been trained on the WIDERFACE dataset.

Tiny Face Detector

The Tiny Face Detector is a very performant, realtime face detector, which is much faster, smaller and less resource consuming compared to the SSD Mobilenet V1 face detector, in return it performs slightly less well on detecting small faces. This model is extremely mobile and web friendly, thus it should be your GO-TO face detector on mobile devices and resource limited clients. The size of the quantized model is only 190 KB (tiny_face_detector_model).

The face detector has been trained on a custom dataset of ~14K images labeled with bounding boxes. Furthermore the model has been trained to predict bounding boxes, which entirely cover facial feature points, thus it in general produces better results in combination with subsequent face landmark detection than SSD Mobilenet V1.
This model is basically an even tinier version of Tiny Yolo V2, replacing the regular convolutions of Yolo with depthwise separable convolutions. Yolo is fully convolutional, thus can easily adapt to different input image sizes to trade off accuracy for performance (inference time).

68 Point Face Landmark Detection Models

This package implements a very lightweight and fast, yet accurate 68 point face landmark detector. The default model has a size of only 350kb (face_landmark_68_model) and the tiny model is only 80kb (face_landmark_68_tiny_model). Both models employ the ideas of depthwise separable convolutions as well as densely connected blocks. The models have been trained on a dataset of ~35k face images labeled with 68 face landmark points.

Face Recognition Model

For face recognition, a ResNet-34 like architecture is implemented to compute a face descriptor (a feature vector with 128 values) from any given face image, which is used to describe the characteristics of a persons face. The model is not limited to the set of faces used for training, meaning you can use it for face recognition of any person, for example yourself. You can determine the similarity of two arbitrary faces by comparing their face descriptors, for example by computing the euclidean distance or using any other classifier of your choice.

The neural net is equivalent to the FaceRecognizerNet used in face-recognition.js and the net used in the dlib face recognition example. The weights have been trained by davisking and the model achieves a prediction accuracy of 99.38% on the LFW (Labeled Faces in the Wild) benchmark for face recognition.

The size of the quantized model is roughly 6.2 MB (face_recognition_model).

Face Expression Recognition Model

The face expression recognition model is lightweight, fast and provides reasonable accuracy. The model has a size of roughly 310kb and it employs depthwise separable convolutions and densely connected blocks. It has been trained on a variety of images from publicly available datasets as well as images scraped from the web. Note, that wearing glasses might decrease the accuracy of the prediction results.


