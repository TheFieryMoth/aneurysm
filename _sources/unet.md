# U-Net

## What is U-Net?

U-Net is an image segmentation architecture designed for biomedical purposes. The original paper can be found at https://arxiv.org/pdf/1505.04597.pdf

This project uses a PyTorch implementation of U-Net. It should be located at TutorialTest/training/UNet.

## Training

In order to train U-Net, all you have to do is enter the training script train.py and change some parameters :

train_path: A directory containing the image and mask information. Should have TWO directories inside of it - an 'images' directory and a 'masks' directory (named, exactly, 'images' and 'masks')

train_anno: The json file that contains the annotations

dir_checkpoint: The location you want your weights to be saved to. Must exist BEFORE running the script

crops_root: The directory containing the original crops of the aortas

output_root: The location you want your final image outputs to be saved to. Must exist BEFORE running the script

`train_path`, `train_anno`, and `crops_root` will need to be changed depending on what set of data you're training on.

## Metrics

The training script automatically performs testing for you and stores the images in whichever directory you set.

In order to calculate the accuracy of image segmentation, a metric called Jaccard score is used. The script to get that is in `TutorialTest/training/scripts/get_jaccard_scores.py`. You just need to change the paths of `truthdir` and `preddir` at the very bottom.

