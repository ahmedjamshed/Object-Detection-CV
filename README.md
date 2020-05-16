# Object-Detection-CV

This repository compares the performances of different CNN's on Satellite Imagery DataSet SIMD. Models compared were

* [YOLOV3](https://github.com/experiencor/keras-yolo3) - You only look once
* [RetinaNet](https://github.com/fizyr/keras-retinanet) - Focal loss (resnet50 backbone)
* [FasterRcnn](https://github.com/RockyXu66/Faster_RCNN_for_Open_Images_Dataset_Keras) - RPN with detector (vgg backbone)



## About Dataset

Satellite Imagery Multi-vehicles Dataset (SIMD). It comprises 5,000 images of resolution 1024 x 768 and collectively contains 45,303 objects in 15 different classes of vehicles including cars, trucks, buses, long vehicles, various types of aircrafts and boats. The source images are taken from public satellite imagery available in Google Earth and contain images of multiple locations from seven countries.

Datasets and Data formats used in this repository, along with the trained weights and results can be found here.

[DataSet](https://drive.google.com/drive/folders/1q64pmfB2CuSUYRcdwuGXE8zuH0YRMQpZ?usp=sharing) - Google Drive Link

**Make sure to change the paths in the mentioned notebook files if you are not using given dataset structure.**

## Yolo3

**Dataset Details**
dataset must be in the form of pascal voc format containg proper XML annotaions.

**Trainig and Testing**

Use ["yolo3/yolo3.ipynb"](https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/yolo3/yolo3.ipynb) to train and evaluate the newtwork. Make sure to change the paths if you are not using given dataset structure.

**Results**

Results obtained from YOLO3 are quite impressive

```
airliner: 0.9895
boat: 0.9549
bus: 0.9430
car: 0.9446
chartered: 0.9811
fighter: 0.9849
helicopter: 0.9898
longvehicle: 0.9173
other: 0.6810
propeller: 0.9125
pushbacktruck: 0.8040
stairtruck: 0.8589
trainer: 0.9724
truck: 0.9100
van: 0.9100
mAP: 0.9169
```

<img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/yolo3/results/1020.jpg" width ="400" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/yolo3/results/0025.jpg" width ="400" />
<img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/yolo3/results/4954.jpg" width ="400" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/yolo3/results/2933.jpg" width ="400" />

## Faster - RCNN

**Dataset Details**
* train.txt - format: filename,x1,y1,x2,y2,calss_id,class_name
* test.txt - format: filename,x1,y1,x2,y2,calss_id,class_name

**Training**
Use  ["fasterRcnn/frcnn_train_vgg.ipynb"](https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/frcnn_train_vgg.ipynb) to train the newtwork 

**Testing**
Use  ["fasterRcnn/frcnn_test_vgg.ipynb"](https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/frcnn_test_vgg.ipynb) to evaluate the trained newtwork.


## Retinanet


**Dataset Details**
* classes.csv - format: class_name,class_id
* train.csv - format: filename,x1,y1,x2,y2,class_name
* test.csv - format: filename,x1,y1,x2,y2,class_name

**BackBone cnn**
Resnet50 is used as backbone

**Loss function**
Wieghted-average

**Trainig and Testing**
Use  ["retinaNet/retinanet.ipynb"](https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/retinaNet/retinanet.ipynb) to train and evaluate the trained newtwork.


## Authors

* **Ahmed Jamshed**

## Acknowledgments

This repo contains code from several github repos - Thankx to them :)

retinanet : https://github.com/fizyr/keras-retinanet

yolo : https://github.com/experiencor/keras-yolo3

Faster-RCNN : https://github.com/RockyXu66/Faster_RCNN_for_Open_Images_Dataset_Keras
