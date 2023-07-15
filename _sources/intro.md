# Welcome to Dr. Nguyen's research team!



## Pipeline

### Detection

First, we locate aortic regions with object detection methods. Currently we use YOLOv5.. 

Object detection will find bounding boxes that contain the ascending and descending aortas. We crop the image to those two bounding boxes.

### Segmentation

We take the cropped bounding boxes and pass them through U-Net, an image segmentation model. U-Net finds the actual aortas inside the bounded regions and creates black and white masks.

### 



###
###
###
