# YOLOv5

Our model runs object detection as an ensemble of two models: FasterRCNN and YOLOv5. FasterRCNN is 
covered in [Chau's tutorial](https://chautrn.github.io/aneurysm-docs/faster-rcnn.html). YOLOv5 will
be covered here.

YOLOv5 is actually an independent Git repo, hosted on the [Ultralytics Github](https://github.com/ultralytics/yolov5).
Our version of the repo is located at:
`/data/aneurysm/hakimi93/CamdenAneurysmProject/inference_package/yolo`

Our version may be outdated compared to Ultralytics' version, but the ensemble uses
a customized version of the detection script, so updating might break it.

## Data Format

The format of a YOLO dataset is quite different from FasterRCNN. You still have
a folder with images, but instead of a single annotation file, YOLO demands a
separate .txt file that corresponds to each image.

Furthermore, YOLO also requires a data.yaml file that will specify the paths
to your training dataset and validation dataset.

### Converting from COCO JSON to YOLO

The annotations we receive from Ron are in the COCO JSON format required for
FasterRCNN. We can't directly use these for YOLO, so we need to convert them.

I have already written a script for this, using a package called [pylabel](https://github.com/pylabel-project/pylabel).
The script is straightforward - all you need to change is the annotation path 
(where is the json file located) and the output path (where you want to put your data
after converting it). *NOTE: The output path must be an absolute path.*

The script is located at:
`/data/aneurysm/hakimi93/CamdenAneurysmProject/scripts/coco2yolo.py`

### Training and Testing

You shouldn't be training on the entire dataset since you'll get biased results
if you test on data that you already trained on.

The ratio of training data to untouched testing data is called the train-test split.
Our FasterRCNN uses a train-test split of 80-20, meaning that 80% of the data is
used for training and we test on the remaining 20%.

In order to achieve similar results with YOLO, we have to actually move images
(and their corresponding labels) out of the *train* directory and into a new *test* 
directory.

## Training

First, enter the repository:
`cd /data/aneurysm/hakimi93/CamdenAneurysmProject/inference_package/yolo`

From here, you can execute the training script. Be warned - it has a lot of 
command line arguments.

The most basic training script call might look something like this:
`python train.py --data data.yaml --weights '' --cfg yolov5s.yaml --img 512`

This command will train on images defined in `data.yaml` (the path should be adjusted
so that it actually points to something - there is no data.yaml in the yolo directory)
for 300 (default) epochs, from scratch, with images automatically resized to 512x512.
Incidentally, our images are all already 512x512.

Further usage can be found [here](https://github.com/ultralytics/yolov5/blob/master/train.py#L453).

## Testing

Testing is done from the same location as training, with the script `detect.py`.

The most basic testing script call might look like this:
`python detect.py --source data/images --weights yolov5s.pt`

Again, the paths must be adjusted.

Further usage can be found [here](https://github.com/ultralytics/yolov5/blob/master/detect.py#L216).

