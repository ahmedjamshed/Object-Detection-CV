# Object-Detection-CV

This repository compares the performances of different CNN's on Satellite Imagery DataSet SIMD. Models compared were

* [YOLOV3](https://github.com/experiencor/keras-yolo3) - You only look once
* [RetinaNet](https://github.com/fizyr/keras-retinanet) - Focal loss (resnet50 backbone)
* [FasterRcnn](https://github.com/RockyXu66/Faster_RCNN_for_Open_Images_Dataset_Keras) - RPN with detector (vgg backbone)



## About Dataset

Satellite Imagery Multi-vehicles Dataset (SIMD). It comprises 5,000 images of resolution 1024 x 768 and collectively contains 45,303 objects in 15 different classes of vehicles including cars, trucks, buses, long vehicles, various types of aircrafts and boats. The source images are taken from public satellite imagery available in Google Earth and contain images of multiple locations from seven countries.


**Make sure to change the paths in the mentioned notebook files if you are not using given dataset structure.**

## Yolo3

**Anchors optimization**

Anchors optimization is the key to improve the performance of any object detection CNN. In order to optimize the anchros for the given dataset,  

````
python gen_anchors.py -c path/to/config.json
````
and paste it's output in the same config.json. Anchors for the given dataset are

````
"model" : {
        "min_input_size":       256,
        "max_input_size":       256,
        "anchors":              [16,21, 20,45, 26,75, 33,28, 39,49, 61,33, 67,83, 103,150, 212,274],
        "labels":               ["airliner", "boat", "bus", "car", "chartered", "fighter", "helicopter", "longvehicle",                                    "other", "propeller", "pushbacktruck", "stairtruck", "trainer", "truck", "van"]
      },
````

**Dataset Details**

Dataset must be in the form of pascal voc format containg proper XML annotaions.

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

**Anchors optimization**

Anchors optimization is the key to improve the performance of any object detection CNN. Anchors settings used for the given dataset are

````
# Original anchor_box_scales in the paper is [128, 256, 512]
self.anchor_box_scales = [16, 32, 64, 128, 256] # results were not good at [64, 128, 256]

# Anchor box ratios
self.anchor_box_ratios = [[1, 1], [1./math.sqrt(2), 2./math.sqrt(2)], [2./math.sqrt(2), 1./math.sqrt(2)]]
````

**Dataset Details**
* train.txt - format: filename,x1,y1,x2,y2,calss_id,class_name
* test.txt - format: filename,x1,y1,x2,y2,calss_id,class_name

**Training**
Use  ["fasterRcnn/frcnn_train_vgg.ipynb"](https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/frcnn_train_vgg.ipynb) to train the newtwork

 <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/class_acc_mop.png" height ="155" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/class_reg.png" height ="155" />
<img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/rpn.png" height ="155" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/total_loss.png" height ="155" />

**Testing**
Use  ["fasterRcnn/frcnn_test_vgg.ipynb"](https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/frcnn_test_vgg.ipynb) to evaluate the trained newtwork.

<img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/boats.png" width ="400" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/car.png" width ="400" />
<img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/airliners.png" width ="400" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/fasterRcnn/results/carvan.png" width ="400" />

## Retinanet

**Anchors optimization**

Anchors optimization is the key to improve the performance of any object detection CNN. Anchors settings used for the given dataset are

````
[anchor_parameters]
# Sizes should correlate to how the network processes an image
sizes   = 16 32 64 128 256
# Strides should correlate to how the network strides over an image
strides = 8 16 32 64 128
# The different ratios to use per anchor location.
ratios  = 0.5 1 2 3
# The different scaling factors to use per anchor location.
scales  = 1 1.2 1.6
````

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

**Results**

Results obtained from retina net were

````
2113 instances of class car with average precision: 0.8946
367 instances of class van with average precision: 0.7070
105 instances of class truck with average precision: 0.3815
96 instances of class bus with average precision: 0.5932
22 instances of class others with average precision: 0.0886
37 instances of class airliner with average precision: 0.7450
40 instances of class stair_truck with average precision: 0.2819
26 instances of class pushback_truck with average precision: 0.0350
87 instances of class lang_vehicle with average precision: 0.2985
1 instances of class propeller_aircraft with average precision: 0.0312
36 instances of class charted_aircraft with average precision: 0.4861
8 instances of class helicopter with average precision: 0.0115
108 instances of class trainer_aircraft with average precision: 0.6296
94 instances of class boat with average precision: 0.7173
0 instances of class fighter_aircraft with average precision: 0.0000
Inference time for 307 images: 0.0883
mAP using the weighted average of precisions among classes: 0.7858
mAP: 0.4215
````

<img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/retinaNet/results/4.png" width ="280" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/retinaNet/results/44.png" width ="280" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/retinaNet/results/111.png" width ="280" /> 
<img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/retinaNet/results/132.png" width ="280" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/retinaNet/results/196.png" width ="280" /> <img src = "https://github.com/ahmedjamshed/Object-Detection-CV/blob/master/retinaNet/results/299.png" width ="280" /> 



## Authors

* **Ahmed Jamshed**

## Acknowledgments

This repo contains code from several github repos - Thankx to them :)

retinanet : https://github.com/fizyr/keras-retinanet

yolo : https://github.com/experiencor/keras-yolo3

Faster-RCNN : https://github.com/RockyXu66/Faster_RCNN_for_Open_Images_Dataset_Keras
