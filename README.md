# Face Recognition using OpenCV

## What does it do?

This project uses OpenCV to detect faces and then recognize them. The model is trained using Images from the folder and then is deployed on a live 
video feed, which recognizes the faces frame by frame.

## Technologies
- OpenCV 

- Python 

## Usage 

### Step 1 - Extract embeddings

> Once the face detector detects a face we need to get information of the image to pass it forward to train the model. Here we extract 128 features 
from the image, this gives a matrix having 128 features of the image. 

> Run the following code in your console after keeping the images of the faces you want to train in the dataset folder

```shell
python extract_embeddings.py --dataset dataset \
	--embeddings output/embeddings.pickle \
	--detector face_detection_model \
	--embedding-model openface_nn4.small2.v1.t7
```

### Step 2 - Train Model

> To train the model with the new dataset, run the following commands 

```shell
python train_model.py --embeddings output/embeddings.pickle \
	--recognizer output/recognizer.pickle \
	--le output/le.pickle
```

### Step 3.a - Recognize faces from Video

> Run the python file - recognize_video.py

### Step 3.b - Recognize faces from an Image

> Run the following commands, and add the input image name in place of {image name comes here}

```shell
python recognize.py --detector face_detection_model \
	--embedding-model openface_nn4.small2.v1.t7 \
	--recognizer output/recognizer.pickle \
	--le output/le.pickle \
	--image images/{image name comes here}.jpg  #be sure to keep it in the image folder
```
