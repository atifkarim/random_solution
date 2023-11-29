Create first basic Linux image
==============================

This document shares the information regarding kickstart of Yocto and creation of basic linux image to run using `qemu`

## Preparation of the environment

### Installation of required libraries

This steps starts with the installation of the yocto. I have followed here [This tutorial](https://dornerworks.com/blog/heres-how-you-can-build-your-own-custom-linux-distro-with-yocto/)


### Summary of the steps

- If you just follow the first tutorial you will reach at a stage where you will get first directory, named will be chosen by you, eg: `yocto`. I prefer to keep it at `/home` directory.
- Inside of this directory, I hope that already `Yocto Poky` git repo is 
cloned
- So, now the folder tree is `yocto/poky`
- `cd ~/yocto/poky`
- Source it to run the next commands: `source oe-init-build-env`. After pressing `Enter`, you will be redirected to `build` directory. An output will be displayed as like as follows:
    ```bash
    vmash18@vmash18-Standard-PC-Q35-ICH9-2009:~/yocto/poky$ source oe-init-build-env 

    ### Shell environment set up for builds. ###

    You can now run 'bitbake <target>'

    Common targets are:
        core-image-minimal
        core-image-sato
        meta-toolchain
        meta-ide-support

    You can also run generated qemu images with a command like 'runqemu qemux86'
        ```
- From here, firstly have to modify the `local.conf` file(location `~/yocto/poky/build/conf/`).
- To modify this file I have followed [this youtube video](https://www.youtube.com/watch?v=5fj05BWryhM&list=PLwqS94HTEwpQmgL1UsSwNk_2tQdzq3eVJ&index=1&pp=iAQB&ab_channel=Tech-A-Byte). Only my target machine name is:

    ```sh
    MACHINE ??= "qemux86"
    ```
- Then, from `build` directory execute the command `bitbake core-image-full-cmdline`. As far I have understood, using this command, created Linux distribution will be accessible only via command line. Other command could be found while you will do the `source oe-init-build-env`. It will take more than 1 hour respective with your host machine performance.
- While it would be passed successfully, you can find the images in the following directory
  - Firstly, keep in mind that, I have modifed my `local.conf` file where I have introduced a new variable as `SOURCES` whose path is in the same level of `poky`. So folder tree is :
  ```bash
  yocto--|-poky
       --|-sources
  ```
  - Inside of `/sources/tmp/deploy/images/` folder `qemux86` is present where the necessary images are present
 
- To run this using qemu from build directory:
    ```bash
    runqemu ../../sources/tmp/deploy/images/qemux86/
    ```
    A console will be appeared where `login` will be `root`, and it will require no password.

- After entering in that console, one can experience freshly developed linux image. Just play with common linux command such as `ls, pwd, uname -r, uname -a, lsblk` etc