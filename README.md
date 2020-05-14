# Object-Detection-Deep-learning
## Acknowledgment
This repo contains code from several github repos - Thankx to them :)

retinanet : https://github.com/fizyr/keras-retinanet

yolo : https://github.com/experiencor/keras-yolo3

Faster-RCNN : https://github.com/RockyXu66/Faster_RCNN_for_Open_Images_Dataset_Keras

-----------------------------------------------------

## Faster - RCNN
```
Dataset  consist of images of folder and train, test csv file which contain information in the following format 
filename,x1,y1,x2,y2,class_name

```
```
Training and Testing
For training and testing run following jupyter notebook files
frcnn_train_vgg.ipynb
frcnn_test_vgg.ipynb
Change the folder paths and run all the cells
```

## Yolo3
```
Dataset must be in the form of PASCL VOC dataset

```
```
Training and Testing

For training and testing run following jupyter notebook file
Yollo3.ipynb
Run the cells respectively and change the paths
```
## Retinanet
```
Dataset must be in the form of PASCL VOC dataset

```
```
Training and Testing

Command for training - change the paths
retinanet-train --freeze-backbone --backbone resnet50 --no-resize --compute-val-loss --random-transform --weights C:\Users\saad\simd\keras-retinanet/weights/resnet50_coco_best_v2.h5 --batch-size 8 --steps 100 --epochs 100 --multiprocessing --compute-val-loss --weighted-average --snapshot-path C:\Users\saad\simd\keras-retinanet/snapshots csv annotations.csv classes.csv

Commands for testing - change the paths
retinanet-convert-model C:\Users\saad\simd\keras-retinanet\snapshots\resnet50_csv_40.h5 C:\Users\saad\simd\keras-retinanet\converted_model\out.h5
retinanet-evaluate csv test_data_ratina.csv classes.csv C:\Users\saad\simd\keras-retinanet\converted_model\out.h5
```
