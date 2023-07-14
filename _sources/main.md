# Main, aka our inference script

## What is inference?

Inference is the process of obtaining a prediction from a machine learning model. This is one half of the project, 
with the other half being training the model.

The scripts for inferences are located in the `inference` folder.

## Running main.py

The main script for inferencing is called `main.py`. It is run with command-line arguments, meaning you have to
specify the arguments when you run it. So you would do something like this:

`python main.py --cmdlinearg1 x --cmdlinearg2 y`

## main.py command-line arguments

-y (--yolo) :

This argument specifies the path for the object detection weights file. It will be used to calculate the crops of the image slices.

-u (--unet) :

This argument specifies the path for the image segmentation weights file. It will be used to generate a black-and-white mask of the detected aorta.

-d (--dir) :

This argument specifies the path of the output. After running the script, the crops, masks, and final 3d model will be located in the directory specified here. It SHOULD NOT EXIST beforehand.

-s (--source) :

This argument specifies the path to the directory that contains the source images. This directory should contain .dcm files.

-f (--faster) :

This argument is obsolete, a holdover from when we were using an ensemble. It doesn't need to be specified and can probably be removed without any problems.

### Important note: To prevent accidental corruption of any files, it's a good idea to copy all the files and directories you will use into a separate copies directory beforehand. The paths you specify in these command line arguments SHOULD NOT be direct links to /data/aneurysm/models/datasets or /data/aneurysm/models/weights.

The final line you run in the terminal might look something like this:

`python main.py -y /data/aneurysm/yourname/copies/yolo.pt -u /data/aneurysm/yourname/copies/unet.pth -d /data/aneurysm/yourname/run1 -s /data/aneurysm/yourname/copies/TCGA-17-Z011`

## After running main.py

At the end, you will find the following in whatever output directory you specified with `-d` :

1. A directory named crops, containing cropped images of the detected aortas

2. A directory named masks, containing black-and-white masks of the cropped aortas

3. A directory named fullmasks, containing the aorta masks pasted back on top of the original image

4. A directory named patients, containing a single .html file of the 3d model of the aorta

5. A directory named dcms, containing dicom images that have their pixel data replaced with black-and-white masks
