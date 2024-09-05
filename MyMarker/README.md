# `MyMarker`

Since `yolo` detects objects in images and saves the detection results in a text file, we can use the detection results to mark the objects in the images by ourself. `MyMarker` is a tool to help you mark the objects in images by using the detection results of `yolo`.

## `yolo` result format

The detection results of `yolo` are saved in a text file. Each line in the text file represents a detection result of an object in an image. The format of each line is as follows:

```txt
0 0.1 0.2 0.3 0.4
1 0.5 0.6 0.7 0.8
```

Which means there are two objects detected in the image. The first object is a `0` class object, whose center is at `(0.1, 0.2)` and whose size is `(0.3, 0.4)`. The second object is a `1` class object, whose center is at `(0.5, 0.6)` and whose size is `(0.7, 0.8)`.

## How it works

We decide to split the mark process into three steps:

1. pair the images and the detection results, in which you may need:
   1. `os`: to list the files in a directory
   2. `re`: to match the image file name and the detection result file name
2. read in the images and the detection results, in which you may need:
   1. `cv2`: to read in the images
   2. `numpy`: to read in the detection results
   3. `pandas`: to read in the detection results
3. mark the objects in the images, in which you may need:
   1. `matplotlib`: to show the images
   2. `pillow`: to save the marked images

You may not necessarily need all the libraries mentioned above. You can choose the libraries you are familiar with.

## Things you may consider

1. The detection results are in the range of `[0, 1]`, which means the center of the object is at `(0.5, 0.5)`.
2. `yolo`'s results may not given by the scheme as mentioned above (for example, in `xml` form). You need design a parser to transform the results into the scheme.