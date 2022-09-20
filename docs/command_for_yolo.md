Image detection with YOLO
=========================

## Background

This holds the information to use YOLO for detecting object from images

## Source of detecting object

- For detecting object from own dataset follow this link: <https://medium.com/@manivannan_data/how-to-train-multiple-objects-in-yolov2-using-your-own-dataset-2b4fee898f17>

## Making dataset for YOLO

1/ Make a folder where all of your image will be stored. Then if you have "mask image" as we have got from UE4 then just find out the coordinate of the desired object x,x+w,y,y+h and save them in a text file.

2/ Then make that text file suitable for yolo. For doing this follow this link <https://github.com/ManivannanMurugavel/YOLO-Annotation-Tool>

## Detection

1/ to perform detection usng yolo and save the predicted image with the name "predictions.jpg"--

./darknet detector test cfg/obj.data cfg/yolo-obj.cfg backup/yolo-obj_1200.weights data/chair.jpg

The problem of that command is that it always overwrite the old predicted image with the new test image as it always take the name "predictions.jpg". Look at number 2 to solve it.

2/ To save predicted image in a new name(it will work at a time for single image)--

./darknet detector test cfg/obj.data cfg/yolo-obj.cfg backup/yolo-obj_1200.weights data/somat_795.jpg -out myfile_somat
