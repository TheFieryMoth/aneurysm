#How to run main:

## Setting paths

`main.py` contains several variables at the top, just below the imports.
These variables contain important path information needed for running
main.
You should edit these and save your changes before running main.

All paths must be absolute paths (i.e. start with `/`).

### Weights

There are three paths that refer to weight files:
YOLO_WEIGHTS, FASTER_WEIGHTS, and UNET_WEIGHTS.

Weight files are located in `/data/aneurysm/models/weights`,
inside the `yolo`, `faster`, and `unet` folders for their respective
models.

### Save directories

There are five paths that relate to directory locations:
SAVE_DIR, CROP_DIR, MASK_DIR, FULLMASK_DIR, and MODEL3D_DIR.

Ideally, you want all of these to be located in the same directory.

These must all exist *prior* to running main - main won't create them
for you.

They should all be pretty much self-explanatory, but I'll give some
explanation just in case.

SAVE_DIR - the location you want to save *images* after detection.
(Possibly will be removed in the future)

CROP_DIR - the location you want to save *aorta crops*.

MASK_DIR - the location you want to save *crop masks*.

FULLMASK_DIR - the location you want to save *masks of the entire image*.

MODEL3D_DIR - the location you want to save *the 3D models*.

### Source files

The final path is called SOURCE.

SOURCE must be a directory that contains all the files you want to read.
It should not have *any* files besides the jpg/dcm files you want to use,
and the files should all be directly in the directory, i.e. not in a
subdirectory.

### Important: none of the path names should have underscores (_) in them!

## Other preparations

Besides editing the paths, you also need to create a directory in the
same directory your `main.py` is placed, called temp.

This is easy, just `mkdir temp`.

After you've created temp the first time, you don't need to create it
again.

Once you've done all this, you can just `python main.py`.

## I ran main... now what?

The most important thing produced by `main.py` is the 3D Model, which
should be located in wherever you set MODEL3D_DIR to be. The 3D model
is an html file that you can open up in your browser and interact with.  
