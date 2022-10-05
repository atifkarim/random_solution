Training and Testing with YOLO
==============================


## Training with YOLO

1/ Go to the `darknet` directory. Then create a folder where you will put all pic(RGB) and text file(containing bounding region in YOLO format). To make this file follow the [next point](#make-yolo-format-text-file)

### Make YOLO format text file

- Required Git Repository is [here](https://github.com/ManivannanMurugavel/YOLO-Annotation-Tool).
- Here, you will see two folder - `Images` and `Labels`. These 2 are main folders.
- In 'Images' folder keep all of your RGB images(whole image, not crop) in the specific folder. For example, you have images of 10 classes. So, make `001,002,......,0010` folder and keep the corresponding images in the respective folder.
- Now, keep the annotated text file in the Labels folder as the same way you have kept files and folders in the `Images` folder.
- Here, one question is who will give you the annotated text file. Actually, annotated text file means the information of ROI of the desired object in each image. In my case, I have generated it directly from `Unreal Engine` using `UnrealCV`.
- Inside of the `Labels` folder you have to create one folder named `out`(In `convert.py` this name is given. To change the folder name please take a look in the code file also.)
- Inside of that `out` folder you have to also create `001,002,........,0010,0011` folder(created folder number will be same as the folder number of `Labels` or `Images`)

- [Some modification has done. A few lines below it is given](#some-changes)

- Now keeping the files has finished. The next step is to use the `convert.py` file. In this file check the following points
    - In line 7 you will find the class list. Fill it up with your required class. class = [001,002,..........,0010] (don't put dot dot here :P)
    - In line 29 change `cls = "001"` to your desired class for which you are going to make the YOLO typed text file.
    - In line 26 and 27 mention your folder path for the already made text file and `output` YOLO typed text file path respectively. In the `output path` make the folder for each class where you want to save the file. Keep the folder name same as the input folder path.
    - Then check in which format you have saved your image. In my case that was `.png`. But `convert.py` file by default will take `.jpg` format. So, change all `.jpg` to your desired image format in the convert.py file.
    - Now excute `convert.py` by writing `python convert.py` in the terminal from the directory where `convert.py` is situated.

    DONE !!!

### Some changes

    - In the beginning of the execution of this code please give the folder_number. for 001 or 002 put in the console 1 or 2. For, 0011 or 0015 please put 11 or 15. It will modify the following lines.

    - In line 29 no need to touch

    - In line 26 and 27 no need to touch. Just see the code and change the path except the last string where folder number will go.

    - In the 'out' folder no need to create any folder. It will generate automatically by using the folder_number information.

- Give this folder name `obj` and put it in the `darknet/data/` folder
- Put `obj.names` and `obj.data` these two files `darknet/data/` folder
- In `obj.data` file you can change train and test folder info.
    ```xml
    train= data/train.txt
    test= data/test.txt
    names = data/obj.names
    backup = backup/
    ```

- `obj.names` : This file contain the name of the class by in a form which will be used to show the result in testing. Please order the name as per as the right class.
- I have written a code to write the `obj.names` file using python. For this mandatory things is to have a folder where all bunch of folders will be located with the name as well as with the correct class order(I have chosen the class order with the alphabetical order.)

- python file name is `creation_obj_names_file.py`. Here, only change the folder path where all of the ordered folders are located. And place this code file where you want to create the `obj.names` file (usually in the `darknet/data/ directory`.)

- and also change the classes number

- put `process.py` python file `darknet/data/` folder to create `train.txt` and `test.txt`. Change the directory address in the `process.py` file
- In `darknet/cfg/` folder put `yolo-obj.cfg` file (you will find it in local pc/Atif's pc). Here change the classes number as your desire or goal.
- In `darknet/` folder put `darknet53.conv.74` file. It is a configured training file. You can also download it from [hete](https://github.com/mathieuorhan/darknet)
- Then in `Makefile` change `GPU=0` to `GPU=1` if you want to use `GPU` and then write in terminal `make` and hit Enter. If you don't want to use GPU leave this line and go to next point
- In the terminal go to `cd /home/user/darknet` and write `./darknet detector train data/obj.data cfg/yolo-obj.cfg darknet53.conv.74` and wait to finish the training
-  Let's assume you have done a training and you have a trained weight file named xyz_weights. If you in future again want to do the training for same dataset just write
`./darknet detector train data/obj.data cfg/yolo-obj.cfg backup/xyz_weights`


### Encountered Error

- Check the following file `darknet/cfg/yolo-obj.cfg`. Also check [this file](https://github.com/pjreddie/darknet/issues/236)
- Search for classes. 3 times you will get it.
- Change classes = give_the_desired_number_of_class
- Search for `num`. in `yolov3` `num` by default given 9.
- What is the significance of this `num`?
    - It helps to give the `filter number`.
    - Formula of `filter number` in `yolov3` is `filter = (num/3)*(classes+5)`
    - For `yolov2` is `num*(classes+5)`
- But where this `filter number` you will change?
    - Go to `darknet/cfg/yolo-obj.cfg` and find `yolo` word.
    - You will see 3 times `yolo` will be appeared.
    - Before this `yolo` word you will see `filters` is written. Change the number here.
    - You will also see other `filter` also written in the other places of the file but no need to change.

## Testing Image

- To perform detection using yolo and save the predicted image with the name "predictions.jpg"--
`./darknet detector test data/obj.data cfg/yolo-obj.cfg backup/yolo-obj_1200.weights data/chair.jpg`. The problem of that command is that it always overwrite the old predicted image with the new test image as it always take the name "predictions.jpg". Look at next point to solve it.
- To save predicted image in a new name(it will work at a time for single image)
`./darknet detector test data/obj.data cfg/yolo-obj.cfg backup/yolo-obj_1200.weights data/somat_795.jpg -out myfile_somat`
