# Face-recognition
The face recognition program uses Facenet, MTCNN, and SVM for training and Haarcascade, Facenet, and SVM model for face recognition

During the training process, MTCNN detects and aligns facial features, Facenet generates feature vectors, and SVM is trained to match the vectors with known identities. The resulting model is then used in the face recognition code, which employs Haarcascade for face detection, Facenet for feature generation, and the SVM model for identity matching. This system provides accurate and reliable face recognition capabilities, and can be used in a variety of applications.

Below is face recognition video using a model trained on 100 face images, running on an I3-7200U CPU
<p align="center">
<img src="https://github.com/Ng-Tuan-Anh/Face-recognition/blob/main/Face-recognition-on-webcam.gif" width="500" height="394" />
</p>

## Installation

Clone repository and install requirements.txt
```
git clone https://github.com/Ng-Tuan-Anh/Face-recognition
cd Face-recognition
pip install -r requirements.txt
```

## Training

**1. Data preparation**

In order to train a face recognition system, you have to collect a certain number of pictures that capture the faces of the people you want the system to recognize. You need to have a minimum of two distinct image classes. The dataset folder structure in Facenet may look like this:

```
dataset/
    person1/
        img1.jpg
        img2.jpg
        ...
    person2/
        img1.jpg
        img2.jpg
        ...
    ...
```

**2. Train**

To get started, you'll have to locate ```line 55``` in the ```train.py``` file and change the value of the ```'dataset'``` field to the path of your dataset directory.
Finally, execute the command:
```
python train.py
```
Once it is completed, the output will be two files, namely ```faces_embeddings.npz``` and ```svm_model.pkl```
The ```faces_embeddings.npz``` file contains the facial feature vectors of the trained faces, generated by the FaceNet model. These feature vectors are used to represent each face uniquely

The ```svm_model.pkl``` file contains the trained SVM (Support Vector Machine) model, which uses the feature vectors to classify and recognize new faces. It acts as a decision boundary between different classes of faces, and can predict the identity of a new face by comparing its feature vector with the ones in the ```faces_embeddings.npz``` file.

## Face Recognition on Webcam

Run the command:
```
python detect.py
```
It should be noted that the paths of the files ```haarcascade_frontalface_default.xml``` and ```svm_model.pkl``` in lines ```23```, ```26``` are correct. The ```camera device``` can be changed on ```line 29``` as well
