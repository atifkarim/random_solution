OpenCV - Image Processing Library
=================================

## Background

This writing will guide to install OpenCV

## Install OpenCV in Ubuntu 18

- Firstly Update the required package

```sh
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
```

- If `python` is unavailable follow the next code snipet, otherwise avoid it and go to the next point

```sh
sudo apt-get install python3.6-dev python3-numpy libtbb2 libtbb-dev
```
- Install required package for OpenCV

```sh
sudo apt-get install libjpeg-dev libpng-dev libtiff5-dev libjasper-dev libdc1394-22-dev libeigen3-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev sphinx-common libtbb-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libopenexr-dev libgstreamer-plugins-base1.0-dev libavutil-dev libavfilter-dev libavresample-dev
```

- The former command may occur an error `E: Unable to locate package libjasper-dev`. if no problem occurs jump to the next point.
    - If occurs then follow [this](https://stackoverflow.com/questions/43484357/opencv-in-ubuntu-17-04/43507858)

    - Or
        ```sh
        sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
        sudo apt update
        sudo apt install libjasper1 libjasper-dev
        ```

- Final steps
```sh
sudo -s
cd /opt
git clone https://github.com/Itseez/opencv.git
cd opencv
git checkout 3.3.1 (you can checkout in other release version also)
cd ..
git clone https://github.com/Itseez/opencv_contrib.git
cd opencv_contrib
git checkout 3.3.1
cd opencv
mkdir release
cd release
cmake -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D ENABLE_AVX=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=OFF -D WITH_V4L=OFF -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/opt/opencv_contrib/modules /opt/opencv/
make -j4
make install
ldconfig
exit
cd ~
```


## Install OpenCV in virtual environment

- [Initial Source](https://www.pyimagesearch.com/2018/09/19/pip-install-opencv/)
- If problem occurs then try [this](/https://github.com/ContinuumIO/anaconda-issues/issues/9601
)